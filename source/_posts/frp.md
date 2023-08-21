---
title: frp
date: 2023-08-16 21:46:10
tags: server
---

内网穿透是打破没有公网ip的桎梏，让处于内网的机器也能在远程使用ssh链接，让我这个机器学习算法工程师也能处在世界任何一个地方操纵自己的电脑。话不多说，开始教程。

需要的条件是，有一台有公网ip的服务器当代理机器，使用端口映射，将内网内的主机localhost:22y映射到公网ip的主机上任意一个没有占用的端口，比如6000.

## 复习计算机网络
假设我们的主机IP是192.168.0.0，路由器LAN IP为192.168.0.1，WAN IP为211.22.145.234（这是一个公网IP）,google 服务器 IP 为74.125.204.101。

主机构建HTTP请求数据包，目标IP为74.125.204.101，目标端口是80/443，源IP为192.168.0.0，源端口随机生成，假定为5000
主机检查目标IP地址，发现不在一个网段，数据包丢给默认网关192.168.0.1
路由器LAN口收到数据包，构建NAT映射，随机生成端口，假定为5500,这样映射就是：5500->192.168.0.0:5000．WAN口收到的数据包，如果目标端口是5500,则会转发给192.168.0.0的5000端口。
路由器修改数据包的源端口为5500,源ＩＰ地址为211.22.145.234，使用WAN口将数据包发出去
google服务器收到请求，构建响应HTTP数据包，目标IP地址为211.22.145.234,目标端口是5500
路由器WAN口收到数据包，目标端口是5500,查询NAT表，发现对应的机器是192.168.0.0:5000，所以修改目标IP为192.168.0.0，目标端口为5000，并通过LAN口发送给主机
主机收到数据包，完成一次通信。

参考
[frp穿透原理](https://www.jianshu.com/p/a621556fc07b)

## 使用frp穿透内网
点击链接下载https://github.com/fatedier/frp/releases/download/v0.30.0/frp_0.30.0_linux_amd64.tar.gz
[frp_0.30_amd64_linux](https://github.com/fatedier/frp/releases/download/v0.30.0/frp_0.30.0_linux_amd64.tar.gz)
目前版本为0.30，请到官网下载最新的frp内网穿透软件，我买的腾讯云的服务器，架构一般的X86_64.,上传服务器，解压。
或者直接使用wget或aria2下载
```python
##使用wget 下载
wget https://github.com/fatedier/frp/releases/download/v0.30.0/frp_0.30.0_linux_amd64.tar.gz
##使用aria2下载
aria2 https://github.com/fatedier/frp/releases/download/v0.30.0/frp_0.30.0_linux_amd64.tar.gz
```
下载完毕后解压,进入路径
```python
##解压
tar -xvzf  frp_0.30.0_linux_amd64.tar.gz
##进入软件包
cd frp_0.30.0_linux_amd64
```
## 设置服务端server
```python
vim frps.ini
```
查看监听的端口号
```bash
[common]
bind_port = 7000        # frp服务的端口
```
在服务端开启frp代理服务
```bash
./frps -c frps.ini      # 前台直接启动，测试看日志方便
nohup ./frps -c ./frps.ini > /dev/null 2>&1 &   # 后台运行
```
##  设置客户端client 
同上下载对应版本的frp软件，解压到适当的路径。
```python
##使用wget 下载
wget https://github.com/fatedier/frp/releases/download/v0.30.0/frp_0.30.0_linux_amd64.tar.gz
##使用aria2下载
aria2 https://github.com/fatedier/frp/releases/download/v0.30.0/frp_0.30.0_linux_amd64.tar.gz
```
下载完毕后解压,进入路径
```python
##解压
tar -xvzf  frp_0.30.0_linux_amd64.tar.gz
##进入软件包
cd frp_0.30.0_linux_amd64
```
编辑客户端的配置，将server的公网ip写入server_addr，这里是23。12.12.12,监听端口写入server_port,这里是7000，远程连接时使用的端口remote_port改为6000。
`
```python
vim frpc.ini
```
修改的端口号
```bash
[common]
server_addr = 23.12.12.12     # 公网服务器IP
server_port = 7000              # 公网服务器的bind_port

[ssh]
type = tcp                      # 协议格式
local_ip = 127.0.0.1
local_port = 22                 # 本地ssh服务端口
remote_port = 6000             # 远程连接时使用的端口
```
开启客户端的frp服务。
```python
./frpc -c ./frpc.ini    # 前台直接启动，测试看日志方便
nohup ./frpc -c ./frpc.ini > /dev/null 2>&1 & # 后台运行
```
如果有多台机器需要配置，只需要将每台客户端的的
```python
[ssh]
type = tcp                      # 协议格式
local_ip = 127.0.0.1
local_port = 22                 # 本地ssh服务端口
remote_port = 6000             # 远程连接时使用的端口
```
中ssh改一个其他名字，remote_port改为其他的端口比如6001.像这样。
```python
[ssh_6001]
type = tcp                      # 协议格式
local_ip = 127.0.0.1
local_port = 22                 # 本地ssh服务端口
remote_port = 6001             # 远程连接时使用的端口
```
之后开启服务。

## 测试远程登陆计算机。
```python
ssh innet_username@server_ip_address -p 6000
ssh innet_username@server_ip_address -p 6001
```
输入密码就可以登录在内网内的主机了，是不是很方便？

## 使用scp在刚刚内网穿透的机器上进行文件传输
scp是一个很好的文件传输工具，在局域网内可以很方便传输，或者在有公网ip的机器上也可以，那么在内网穿透后可以传输吗？答案是肯定的。

```python
scp -P 6000 -r ./local_file inner_net_username@server_ip_address:/your/inner/net/machine/path
```
-P 添加刚刚的port
-r 代表递归，传输文件夹

## 关掉frp
```python
ps -aux|grep frp| grep -v grep
kill process_id
```