---
title: hadoop 八股文
date: 2023-08-18 11:30:44
tags:
---



## 1. 请说下HDFS读写流程

HDFS写流程 
1）client客户端发送上传请求，通过RPC与namenode建立通信，namenode检查该用户是否有上传权限，以及上传的文件是否在hdfs对应的目录下重名，如果这两者有任意一个不满足，则直接报错，如果两者都满足，则返回给客户端一个可以上传的信息 
2）client根据文件的大小进行切分，默认128M一块，切分完成之后给namenode发送请求第一个block块上传到哪些服务器上 
3）namenode收到请求之后，根据网络拓扑和机架感知以及副本机制进行文件分配，返回可用的DataNode的地址 
* 注：Hadoop 在设计时考虑到数据的安全与高效, 数据文件默认在 HDFS 上存放三份, 存储策略为本地一份，同机架内其它某一节点上一份, 不同机架的某一节点上一份 
4）客户端收到地址之后与服务器地址列表中的一个节点如A进行通信，本质上就是RPC调用，建立pipeline，A收到请求后会继续调用B，B在调用C，将整个pipeline建立完成，逐级返回client 
5）client开始向A上发送第一个block（先从磁盘读取数据然后放到本地内存缓存），以packet（数据包，64kb）为单位，A收到一个packet就会发送给B，然后B发送给C，A每传完一个packet就会放入一个应答队列等待应答 
6）数据被分割成一个个的packet数据包在pipeline上依次传输，在pipeline反向传输中，逐个发送ack（命令正确应答），最终由pipeline 中第一个 DataNode 节点 A 将 pipelineack 发送给 Client 
7）当一个 block 传输完成之后, Client 再次请求 NameNode 上传第二个 block ，namenode重新选择三台DataNode给client
HDFS读流程 
1）client向namenode发送RPC请求。请求文件block的位置 
2）namenode收到请求之后会检查用户权限以及是否有这个文件，如果都符合，则会视情况返回部分或全部的block列表，对于每个block，NameNode 都会返回含有该 block 副本的 DataNode 地址； 这些返回的 DN 地址，会按照集群拓扑结构得出 DataNode 与客户端的距离，然后进行排序，排序两个规则：网络拓扑结构中距离 Client 近的排靠前；心跳机制中超时汇报的 DN 状态为 STALE，这样的排靠后 
3）Client 选取排序靠前的 DataNode 来读取 block，如果客户端本身就是DataNode,那么将从本地直接获取数据(短路读取特性) 
4）底层上本质是建立 Socket Stream（FSDataInputStream），重复的调用父类 DataInputStream 的 read 方法，直到这个块上的数据读取完毕
5）当读完列表的 block 后，若文件读取还没有结束，客户端会继续向NameNode 获取下一批的 block 列表
6）读取完一个 block 都会进行 checksum 验证，如果读取 DataNode 时出现错误，客户端会通知 NameNode，然后再从下一个拥有该 block 副本的DataNode 继续读
7）read 方法是并行的读取 block 信息，不是一块一块的读取；NameNode 只是返回Client请求包含块的DataNode地址，并不是返回请求块的数据
8） 最终读取来所有的 block 会合并成一个完整的最终文件

## 2. HDFS在读取文件的时候,如果其中一个块突然损坏了怎么办
客户端读取完DataNode上的块之后会进行checksum 验证，也就是把客户端读取到本地的块与HDFS上的原始块进行校验，如果发现校验结果不一致，客户端会通知 NameNode，然后再从下一个拥有该 block 副本的DataNode 继续读

## 3. HDFS在上传文件的时候,如果其中一个DataNode突然挂掉了怎么办
客户端上传文件时与DataNode建立pipeline管道，管道正向是客户端向DataNode发送的数据包，管道反向是DataNode向客户端发送ack确认，也就是正确接收到数据包之后发送一个已确认接收到的应答，当DataNode突然挂掉了，客户端接收不到这个DataNode发送的ack确认
，客户端会通知 NameNode，NameNode检查该块的副本与规定的不符，NameNode会通知DataNode去复制副本，并将挂掉的DataNode作下线处理，不再让它参与文件上传与下载。

## 4. NameNode在启动的时候会做哪些操作
NameNode数据存储在内存和本地磁盘，本地磁盘数据存储在fsimage镜像文件和edits编辑日志文件 
* 首次启动NameNode 
1、格式化文件系统，为了生成fsimage镜像文件 
2、启动NameNode 
（1）读取fsimage文件，将文件内容加载进内存 
（2）等待DataNade注册与发送block report 
3、启动DataNode 
（1）向NameNode注册 
（2）发送block report 
（3）检查fsimage中记录的块的数量和block report中的块的总数是否相同 
4、对文件系统进行操作（创建目录，上传文件，删除文件等） 
（1）此时内存中已经有文件系统改变的信息，但是磁盘中没有文件系统改变的信息，此时会将这些改变信息写入edits文件中，edits文件中存储的是文件系统元数据改变的信息。 
* 第二次启动NameNode 
1、读取fsimage和edits文件 
2、将fsimage和edits文件合并成新的fsimage文件 
3、创建新的edits文件，内容为空 
4、启动DataNode 


## 5. Secondary NameNode了解吗，它的工作机制是怎样的

Secondary NameNode 是合并NameNode的edit logs到fsimage文件中；
它的具体工作机制： 
（1）Secondary NameNode询问NameNode是否需要checkpoint。直接带回NameNode是否检查结果 
（2）Secondary NameNode请求执行checkpoint 
（3）NameNode滚动正在写的edits日志 
（4）将滚动前的编辑日志和镜像文件拷贝到Secondary NameNode 
（5）Secondary NameNode加载编辑日志和镜像文件到内存，并合并 
（6）生成新的镜像文件fsimage.chkpoint 
（7）拷贝fsimage.chkpoint到NameNode 
（8）NameNode将fsimage.chkpoint重新命名成fsimage 
所以如果NameNode中的元数据丢失，是可以从Secondary NameNode恢复一部分元数据信息的，但不是全部，因为NameNode正在写的edits日志还没有拷贝到Secondary NameNode，这部分恢复不了

## 6. Secondary NameNode不能恢复NameNode的全部数据，那如何保证NameNode数据存储安全 
## 8. 在NameNode HA中，会出现脑裂问题吗？怎么解决脑裂 

## 9. 小文件过多会有什么危害,如何避免 

## 10. 请说下HDFS的组织架构 


## 11. 请说下MR中Map Task的工作机制 

## 12. 请说下MR中Reduce Task的工作机制

##13. 请说下MR中shuffle阶段 

## 14. shuffle阶段的数据压缩机制了解吗 15. 在写MR时，什么情况下可以使用规约 16. yarn 集群的架构和工作原理知道多少 17. yarn 的任务提交流程是怎样的 18. yarn 的资源调度三种模型了解吗
