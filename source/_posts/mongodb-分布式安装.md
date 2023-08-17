---
title: mongodb 分布式安装
date: 2023-08-16 17:59:17
tags:
---

参考搭建文档https://blog.csdn.net/msh6453/article/details/131161845

前言
官方文档：https://www.mongodb.com/docs/（可以参考）

## 一，安装说明
1.1环境说明
1、首先确定部署的环境，确定下服务器的端口，一般默认是22的端口；
2、操作系统Centos7.9；
3、 数据库mongodb-linux-x86_64-rhel70-4.4.22。
mongodb版本4.4.22

![Alt text](image-1.png)

mongos，数据库集群请求的入口，所有的请求都通过mongos进行协调，不需要在应用程序添加一个路由选择器，mongos自己就是一个请求分发中心，它负责把对应的数据请求请求转发到对应的shard服务器上。在生产环境通常有多mongos作为请求的入口，防止其中一个挂掉所有的mongodb请求都没有办法操作。

config server，顾名思义为配置服务器，存储所有数据库元信息（路由、分片）的配置。mongos本身没有物理存储分片服务器和数据路由信息，只是缓存在内存里，配置服务器则实际存储这些数据。mongos第一次启动或者关掉重启就会从 config server 加载配置信息，以后如果配置服务器信息变化会通知到所有的 mongos 更新自己的状态，这样 mongos 就能继续准确路由。在生产环境通常有多个 config server 配置服务器，因为它存储了分片路由的元数据，防止数据丢失！

shard，分片（sharding）是指将数据库拆分，将其分散在不同的机器上的过程。将数据分散到不同的机器上，不需要功能强大的服务器就可以存储更多的数据和处理更大的负载。基本思想就是将集合切成小块，这些块分散到若干片里，每个片只负责总数据的一部分，最后通过一个均衡器来对各个分片进行均衡（数据迁移）。

replica set，中文翻译副本集，其实就是shard的备份，防止shard挂掉之后数据丢失。复制提供了数据的冗余备份，并在多个服务器上存储数据副本，提高了数据的可用性， 并可以保证数据的安全性。

仲裁者（Arbiter），是复制集中的一个MongoDB实例，它并不保存数据。仲裁节点使用最小的资源并且不要求硬件设备，不能将Arbiter部署在同一个数据集节点中，可以部署在其他应用服务器或者监视服务器中，也可部署在单独的虚拟机中。为了确保复制集中有奇数的投票成员（包括primary），需要添加仲裁节点做为投票，否则primary不能运行时不会自动切换primary。

简单了解之后，我们可以这样总结一下，应用请求mongos来操作mongodb的增删改查，配置服务器存储数据库元信息，并且和mongos做同步，数据最终存入在shard（分片）上，为了防止数据丢失同步在副本集中存储了一份，仲裁在数据存储到分片的时候决定存储到哪个节点。


|  服务器  | ceph-node-1 | ceph-node-2 |  ceph-node-3  | 
|  ----  | ----  |-| - |
| ip  | 10.30.0.48|10.30.0.49|  10.30.0.50|
| server-route | mongos|mongos|  mongos|
| server-config| config server|  config server  |config server  |
| server-config| shard server1 主节点|  shard server1 副节点  | shard server1 仲裁  |
| server-config| shard server2 仲裁|  shard server2 主节点  | shard server2 副节点 |
|  server-config | shard server3 副节点| shard server3 仲裁|  shard server3 主节点 |


## 安装步骤
```bash
mkdir -p /opt/mongo/MongoDB/conf
mkdir -p /opt/mongo/MongoDB/server
mkdir -p /opt/mongo/MongoDB/mongos/log
mkdir -p /opt/mongo/MongoDB/config/data
mkdir -p /opt/mongo/MongoDB/config/log
mkdir -p /opt/mongo/MongoDB/shard1/data
mkdir -p /opt/mongo/MongoDB/shard1/log
mkdir -p /opt/mongo/MongoDB/shard2/data
mkdir -p /opt/mongo/MongoDB/shard2/log
mkdir -p /opt/mongo/MongoDB/shard3/data
mkdir -p /opt/mongo/MongoDB/shard3/log

wget https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-rhel70-4.4.22.tgz
tar -xvzf mongodb-linux-x86_64-rhel70-4.4.22.tgz -C /opt/mongo/MongoDB/server/
mv /opt/mongo/MongoDB/server/mongodb-linux-x86_64-rhel70-4.4.22 /opt/mongo/MongoDB/server/mongodb

vim /etc/profile
export MONGODB_HOME=/opt/mongo/MongoDB/server/mongodb
export PATH=$MONGODB_HOME/bin:$PATH
:wq!
source /etc/profile
vim /opt/mongo/MongoDB/conf/config.conf 
vim /opt/mongo/MongoDB/conf/shard1.conf
vim /opt/mongo/MongoDB/conf/shard2.conf
vim /opt/mongo/MongoDB/conf/shard3.conf
vim /opt/mongo/MongoDB/conf/mongos.conf
```

配置文件如mongo/conf 下面
注意安装的时候不要设置最后的安全密钥，待完毕后添加


启动服务顺序
```bash
mongod -f /opt/mongo/MongoDB/conf/config.conf
mongod -f /opt/mongo/MongoDB/conf/shard1.conf
mongod -f /opt/mongo/MongoDB/conf/shard2.conf
mongod -f /opt/mongo/MongoDB/conf/shard3.conf
mongos -f /opt/mongo/MongoDB/conf/mongos.conf
```



随便登入一台
```mongo
mongo 10.30.0.48:21000
use admin
config = {_id : "config",members : [{_id : 0, host : "10.30.0.48:21000" },
{_id : 1, host : "10.30.0.49:21000" },{_id : 2, host : "10.30.0.50:21000" }]}
rs.initiate(config)
```


同理 server sharded1
```mongo
mongo 10.30.0.48:27001
use admin
config = { _id : "shard1",members : [{_id : 0, host : "10.30.0.48:27001" ,priority: 2 },{_id : 1, host : "10.30.0.49:27001" ,priority: 1 },{_id : 2, host : "10.30.0.50:27001",arbiterOnly: true}]}
//(“priority”优先级，数字越大，优先等级越高；“arbiterOnly”冲裁节点；冲裁节点根据优先等级判断哪个节点作为主节点)
rs.initiate(config)

```

```bash
mongo 10.30.0.48:27002
server shard2
use admin
config = { _id : "shard2",members : [{_id : 0, host : "10.30.0.48:27002" ,arbiterOnly: true },
{_id : 1, host : "10.30.0.49:27002" ,priority: 2 },{_id : 2, host : "10.30.0.50:27002",priority: 1}]}
rs.initiate(config)

```

server shard3

```mongo
mongo 10.30.0.48:27003
use admin
config = { _id : "shard3",members : [{_id : 0, host : "10.30.0.48:27003" ,priority: 1 },

{_id : 1, host : "10.30.0.49:27003" ,arbiterOnly: true },{_id : 2, host : "10.30.0.50:27003",priority: 2}]}

rs.initiate(config)
```



添加分片服务器

```bash
use admin
sh.addShard("shard1/10.30.0.48:27001,10.30.0.49:27001,10.30.0.50:27001")

sh.addShard("shard2/10.30.0.48:27002,10.30.0.49:27002,10.30.0.50:27002")

sh.addShard("shard3/10.30.0.48:27003,10.30.0.49:27003,10.30.0.50:27003")

sh.status()
```


创建用户
```bash
执行命令： mongo -port 20000
执行命令： use admin//这个条件是必须的
执行命令：db.createUser(

  {

        user:"ml_grp",

        pwd:"ml&dl#mongodb",

        roles:[{role:"root",db:"admin"}]

    }

)
```

use admin
执行命令：db.auth('ml_grp','passwd')
执行命令：db.runCommand( { enablesharding :"zjxndc"});//为zjxndc开启分片功能
执行命令：db.runCommand( { shardcollection : "zjxndc.measureHisvalues",key : {_id: 1} } )/


use config
db.settings.save({"_id":"chunksize","value":1})
use zjxndc
d、执行命令：for (var i = 1; i <= 100000; i++){

db.measureHisvalues.insert({"_id":i,"test1":"testval1"+i});

}

![enable partition](1408af41c022dc62726ecf884c95ff0a.png)
![查看是否分区成功](image.png)


### 配置安全


#### 4.1 安全验证设置用户
1、副本集和共享集群的各个节点成员之间使用内部身份验证，可以使用密钥文件或x.509证书。密钥文件比较简单，官方推荐如果是测试环境可以使用密钥文件，但是正是环境，官方推荐x.509证书。原理就是，集群中每一个实例彼此连接的时候都检验彼此使用的证书的内容是否相同。只有证书相同的实例彼此才可以访问。使用客户端连接到mongodb集群时，开启访问授权。对于集群外部的访问。如通过可视化客户端，或者通过代码连接的时候，需要开启授权。
a、生成密钥文件，在keyfile身份验证中，副本集中的每个mongod实例都使用keyfile的内容作为共享密码，只有具有正确密钥文件的mongod或者mongos实例可以连接到副本集。密钥文件的内容必须在6到1024个字符之间，并且在unix/linux系统中文件所有者必须有对文件至少有读的权限。可以用任何方式生成密钥文件例如：(任意一台机器即可)

执行命令：openssl rand -base64 756 > /opt/mongo/MongoDB/testKeyFile.file //生成密钥

执行命令：chmod 400 /opt/mongo/MongoDB/testKeyFile.file //赋予权限

执行命令：scp -P22 /opt/mongo/MongoDB/testKeyFile.file root@10.30.0.49:/opt/mongo/MongoDB //拷贝至其他0.55服务器上（“-P22”是端口，根据实际情况来）

执行命令：scp -P22 /opt/mongo/MongoDB/testKeyFile.file root@:10.30.0.49 /opt/mongo/MongoDB //拷贝至其他0.56服务器上


创建用户成功后，关闭所有的节点（三台机都需要操作）

执行命令：按照先后顺序来处理关闭，mongos>config>shadr3>shadr2>shadr1

//注意的是每一个服务的关闭都需要在三台机上关闭，在关闭其他服务。例如关闭shadr3服务，先关闭0.54服务器上的shadr3服务，其次0.55服务器上的shadr3服务，再是0.56服务器上的shadr3服务；然后在关闭shadr2服务，也是按照这个顺序处理。（这个地方主要新手操作避免出错）

执行命令：

```bash
mongod -f /opt/mongo/MongoDB/conf/shard1.conf --shutdown
mongod -f /opt/mongo/MongoDB/conf/shard2.conf --shutdown
mongod -f /opt/mongo/MongoDB/conf/shard3.conf --shutdown
mongod -f /opt/mongo/MongoDB/conf/config.conf --shutdown
mongo 10.30.0.48:20000//mongos需要这样关闭，用上面的命令有问题。

use admin
db.auth('ml_grp','passwd')
db.shutdownServer()
```

3、配置testKeyFile.file，依次在每台机器上的mongos.conf、config.conf、shard1.conf、shard2.conf、shard3.conf的配置和开启授权验证。
a、先是config.conf、shard1.conf、shard2.conf、shard3.conf的配置和开启授权验证。（三台机器的这些文件都需要添加）
在conf这几个文件的的最后添加：
```bash
security:
  keyFile: /opt/mongo/MongoDB/testKeyFile.file
  authorization: enabled
```
b、然后在三台机器的mongos.conf配置文件中最后添加：
```bash
security:
  keyFile: /opt/mongo/MongoDB/testKeyFile.file
```
//这里就说明了testKeyFile.file最好在每台机器放在一个位置，为了后面复制粘贴处理

//解释说明： mongos比mongod少了authorization：enabled的配置。原因是，副本集加分片的安全认证需要配置两方面的，副本集各个节点之间使用内部身份验证，用于内部各个mongo实例的通信，只有相同keyfile才能相互访问。所以都要开启keyFile: /data/mongodb/testKeyFile.file

    然而对于所有的mongod，才是真正的保存数据的分片。mongos只做路由，不保存数据。所以所有的mongod开启访问数据的授权authorization:enabled。这样用户只有账号密码正确才能访问到数据
