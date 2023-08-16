---
title: ceph分布式安装
date: 2023-08-11 17:59:52
tags:
---

1.环境配置
#在所有节点配置YUM：
#清空原来自带配置文件：

```bash
cd /etc/yum.repos.d/
mkdir /tmp/bak
mv * /tmp/bak/
```
#配置系统源码，epel源：
```bash
curl -o /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-7.repo
yum install wget -y
wget -O /etc/yum.repos.d/epel.repo http://mirrors.aliyun.com/repo/epel-7.repo
#YUM优先级别：
yum -y install yum-plugin-priorities.noarch
```
#配置ceph源：
```bash
cat << EOF | tee /etc/yum.repos.d/ceph.repo
[Ceph]
name=Ceph packages for $basearch
baseurl=http://mirrors.163.com/ceph/rpm-nautilus/el7/\$basearch
enabled=1
gpgcheck=1
type=rpm-md
gpgkey=https://download.ceph.com/keys/release.asc
priority=1
[Ceph-noarch]
name=Ceph noarch packages
baseurl=http://mirrors.163.com/ceph/rpm-nautilus/el7/noarch
enabled=1
gpgcheck=1
type=rpm-md
gpgkey=https://download.ceph.com/keys/release.asc
priority=1
[ceph-source]
name=Ceph source packages
baseurl=http://mirrors.163.com/ceph/rpm-nautilus/el7/SRPMS
enabled=1
gpgcheck=1
type=rpm-md
gpgkey=https://download.ceph.com/keys/release.asc
EOF
```
#关闭防火墙：


```bash
systemctl stop firewalld
systemctl disable firewalld
systemctl status firewalld
```
#配置主机名称：
```bash
ceph1节点：
hostnamectl --static set-hostname ceph1
ceph2节点：
hostnamectl --static set-hostname ceph2
ceph3节点：
hostnamectl --static set-hostname ceph3
```
#所有节点配置hosts文件：
```bash
/etc/hosts
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
192.168.0.231    ceph1
192.168.0.232    ceph2
192.168.0.233    ceph3
```

#所有节点NTP配置：
在所有集群和客户端节点安装NTP，修改配置。
```bash
yum -y install ntp ntpdate
# 以ceph1为NTP服务端节点，在ceph1新建NTP文件。
vi /etc/ntp.conf
# 并新增如下内容作为NTP服务端：
restrict 127.0.0.1
restrict ::1
restrict 192.168.3.0 mask 255.255.255.0 //ceph1的网段与掩码
server 127.127.1.0
fudge 127.127.1.0 stratum 8
```
在ceph2、ceph3及所有客户机节点新建NTP文件。
```bash
vi /etc/ntp.conf
# 并新增如下内容作为客户端：
server 192.168.3.166

systemctl start ntpd
systemctl enable ntpd
systemctl status ntpd
```
#ssh配置，在ceph1节点生成公钥，并发放到各个主机/客户机节点。：
```bash
ssh-keygen -t rsa #回车采取默认配置
for i in {1..3}; do ssh-copy-id ceph$i; done #根据提示输入yes及节点密码
for i in {1..3}; do ssh-copy-id client$i; done
```

#在所有节点，关闭SELinux
```bash
sed -i 's/enforcing/disabled/' /etc/selinux/config
setenforce 0
```
1. 安装Ceph软件
使用yum install安装ceph的时候会默认安装当前已有的最新版，如果不想安装最新版本，可以在/etc/yum.conf文件中加以限制。
2.1 在所有集群和客户端节点安装Ceph
```bash
yum -y install ceph
ceph -v命令查看版本:
[root@ceph1 ~]# ceph -v
ceph version 14.2.9 (581f22da52345dba46ee232b73b990f06029a2a0) nautilus (stable)
[root@ceph2 ~]# ceph -v
ceph version 14.2.9 (581f22da52345dba46ee232b73b990f06029a2a0) nautilus (stable)
[root@ceph3 ~]# ceph -v
ceph version 14.2.9 (581f22da52345dba46ee232b73b990f06029a2a0) nautilus (stable)
```
2.2 在ceph1节点额外安装ceph-deploy。
```bash
yum -y install ceph-deploy
```
3.部署MON节点
3.1 创建目录生成配置文件
```
mkdir cluster
cd cluster
ceph-deploy new ceph1 ceph2 ceph3
```

```bash
[root@ceph1 ~]# cd cluster/
[root@ceph1 cluster]# ceph-deploy new ceph1 ceph2 ceph3
[ceph_deploy.conf][DEBUG ] found configuration file at: /root/.cephdeploy.conf
[ceph_deploy.cli][INFO  ] Invoked (2.0.1): /usr/bin/ceph-deploy new ceph1 ceph2 ceph3
[ceph_deploy.cli][INFO  ] ceph-deploy options:
[ceph_deploy.cli][INFO  ]  username                      : None
[ceph_deploy.cli][INFO  ]  func                          : <function new at 0x7ffb7dc07de8>
[ceph_deploy.cli][INFO  ]  verbose                       : False
[ceph_deploy.cli][INFO  ]  overwrite_conf                : False
[ceph_deploy.cli][INFO  ]  quiet                         : False
[ceph_deploy.cli][INFO  ]  cd_conf                       : <ceph_deploy.conf.cephdeploy.Conf instance at 0x7ffb7d58c6c8>
[ceph_deploy.cli][INFO  ]  cluster                       : ceph
[ceph_deploy.cli][INFO  ]  ssh_copykey                   : True
[ceph_deploy.cli][INFO  ]  mon                           : ['ceph1', 'ceph2', 'ceph3']
[ceph_deploy.cli][INFO  ]  public_network                : None
[ceph_deploy.cli][INFO  ]  ceph_conf                     : None
[ceph_deploy.cli][INFO  ]  cluster_network               : None
[ceph_deploy.cli][INFO  ]  default_release               : False
[ceph_deploy.cli][INFO  ]  fsid                          : None
[ceph_deploy.new][DEBUG ] Creating new cluster named ceph
[ceph_deploy.new][INFO  ] making sure passwordless SSH succeeds
[ceph1][DEBUG ] connected to host: ceph1 
[ceph1][DEBUG ] detect platform information from remote host
[ceph1][DEBUG ] detect machine type
[ceph1][DEBUG ] find the location of an executable
[ceph1][INFO  ] Running command: /usr/sbin/ip link show
[ceph1][INFO  ] Running command: /usr/sbin/ip addr show
[ceph1][DEBUG ] IP addresses found: [u'192.168.0.231']
[ceph_deploy.new][DEBUG ] Resolving host ceph1
[ceph_deploy.new][DEBUG ] Monitor ceph1 at 192.168.0.231
[ceph_deploy.new][INFO  ] making sure passwordless SSH succeeds
[ceph2][DEBUG ] connected to host: ceph1 
[ceph2][INFO  ] Running command: ssh -CT -o BatchMode=yes ceph2
[ceph2][DEBUG ] connected to host: ceph2 
[ceph2][DEBUG ] detect platform information from remote host
[ceph2][DEBUG ] detect machine type
[ceph2][DEBUG ] find the location of an executable
[ceph2][INFO  ] Running command: /usr/sbin/ip link show
[ceph2][INFO  ] Running command: /usr/sbin/ip addr show
[ceph2][DEBUG ] IP addresses found: [u'192.168.0.232']
[ceph_deploy.new][DEBUG ] Resolving host ceph2
[ceph_deploy.new][DEBUG ] Monitor ceph2 at 192.168.0.232
[ceph_deploy.new][INFO  ] making sure passwordless SSH succeeds
[ceph3][DEBUG ] connected to host: ceph1 
[ceph3][INFO  ] Running command: ssh -CT -o BatchMode=yes ceph3
[ceph3][DEBUG ] connected to host: ceph3 
[ceph3][DEBUG ] detect platform information from remote host
[ceph3][DEBUG ] detect machine type
[ceph3][DEBUG ] find the location of an executable
[ceph3][INFO  ] Running command: /usr/sbin/ip link show
[ceph3][INFO  ] Running command: /usr/sbin/ip addr show
[ceph3][DEBUG ] IP addresses found: [u'192.168.0.233']
[ceph_deploy.new][DEBUG ] Resolving host ceph3
[ceph_deploy.new][DEBUG ] Monitor ceph3 at 192.168.0.233
[ceph_deploy.new][DEBUG ] Monitor initial members are ['ceph1', 'ceph2', 'ceph3']
[ceph_deploy.new][DEBUG ] Monitor addrs are ['192.168.0.231', '192.168.0.232', '192.168.0.233']
[ceph_deploy.new][DEBUG ] Creating a random mon key...
[ceph_deploy.new][DEBUG ] Writing monitor keyring to ceph.mon.keyring...
[ceph_deploy.new][DEBUG ] Writing initial config to ceph.conf...
```
3.2 初始化密钥
```bash
ceph-deploy mon create-initial
```
3.3 将ceph.client.admin.keyring拷贝到各个节点上
```bash
ceph-deploy --overwrite-conf admin ceph1 ceph2 ceph3
```
3.4 查看是否配置成功。
```bash
[root@ceph1 cluster]# ceph -scluster:id:     ea192428-05d2-437a-8cce-9d187de82dd5health: HEALTH_OKservices:mon: 3 daemons, quorum ceph1,ceph2,ceph3 (age 5m)mgr: no daemons activeosd: 0 osds: 0 up, 0 indata:pools:   0 pools, 0 pgsobjects: 0 objects, 0 Busage:   0 B used, 0 B / 0 B availpgs:  
```
4 部署MGR节点
```bash
ceph-deploy mgr create ceph1 ceph2 ceph3
```
查看MGR是否部署成功。

```bash
ceph -s
[root@ceph1 cluster]# ceph -scluster:id:     ea192428-05d2-437a-8cce-9d187de82dd5health: HEALTH_WARNOSD count 0 < osd_pool_default_size 3services:mon: 3 daemons, quorum ceph1,ceph2,ceph3 (age 8m)mgr: ceph1(active, since 22s), standbys: ceph2, ceph3osd: 0 osds: 0 up, 0 indata:pools:   0 pools, 0 pgsobjects: 0 objects, 0 Busage:   0 B used, 0 B / 0 B availpgs: 
```  
5 部署OSD节点
```bash
ceph-deploy osd create --data /dev/sdb ceph1
ceph-deploy osd create --data /dev/sdc ceph1
ceph-deploy osd create --data /dev/sdd ceph1
ceph-deploy osd create --data /dev/sdb ceph2
ceph-deploy osd create --data /dev/sdc ceph2
ceph-deploy osd create --data /dev/sdd ceph2
ceph-deploy osd create --data /dev/sdb ceph3
ceph-deploy osd create --data /dev/sdc ceph3
ceph-deploy osd create --data /dev/sdd ceph3
```
创建成功后，查看是否正常

```bash
[root@ceph1 cluster]# ceph -scluster:id:     ea192428-05d2-437a-8cce-9d187de82dd5health: HEALTH_OKservices:mon: 3 daemons, quorum ceph1,ceph2,ceph3 (age 14m)mgr: ceph1(active, since 6m), standbys: ceph2, ceph3osd: 9 osds: 9 up (since 2m), 9 in (since 2m)data:pools:   0 pools, 0 pgsobjects: 0 objects, 0 Busage:   9.0 GiB used, 135 GiB / 144 GiB availpgs:  
```
6 验证Ceph
创建存储池
```bash
ceph osd pool create vdbench 10 10
```
创建块设备
```bash
rbd create image01 --size 200--pool vdbench --image-format 2 --image-feature layering
rbd ls --pool vdbench
[root@ceph1 cluster]# rbd create image01 --size 200 --pool  vdbench --image-format 2 --image-feature layering
[root@ceph1 cluster]# rbd ls --pool vdbench
image01
```

#PG 分 配 计 算
归置组(PG)的数量是由管理员在创建存储池的时候指定的，然后由 CRUSH 负责创建和使用，PG 的数量是 2 的 N 次方的倍数,每个 OSD 的 PG 不要超出 250 个 PG  
Total PGs = (Total_number_of_OSD * 100) / max_replication_count  
单个 pool 的 PG 计算如下：  
有 100 个 osd，3 副本，5 个 pool  
Total PGs =100*100/3=3333  
每个 pool 的 PG=3333/5=512，那么创建 pool 的时候就指定 pg 为 512  
客户端在读写对象时，需要提供的是对象标识和存储池名称  
客户端需要在存储池中读写对象时，需要客户端将对象名称，对象名称的hash码，存储池中的PG数量和存储池名称作为输入信息提供给ceph，然后由CRUSH计算出PG的ID以及PG针对的主OSD即可读写OSD中的对象。  
具体写操作如下：  
1.APP向ceph客户端发送对某个对象的请求，此请求包含对象和存储池，然后ceph客户端对访问的对象做hash计算，并根据此hash值计算出对象所在的PG，完成对象从Pool至PG的映射。  
APP 访问 pool ID 和 object ID （比如 pool = pool1 and object-id = “name1”）  
ceph client 对 objectID 做哈希   
ceph client 对该 hash 值取 PG 总数的模，得到 PG 编号(比如 32)  
ceph client 对 pool ID 取 hash（比如 “pool1” = 3）  
ceph client 将 pool ID 和 PG ID 组合在一起(比如 3.23)得到 PG 的完整 ID。  
2.然后客户端据 PG、CRUSH 运行图和归置组(placement rules)作为输入参数并再次进行计  
算，并计算出对象所在的 PG 内的主 OSD ，从而完成对象从 PG 到 OSD 的映射。  
3.客户端开始对主 OSD 进行读写请求(副本池 IO)，如果发生了写操作，会有 ceph 服务端完  
成对象从主 OSD 到备份 OSD 的同步  

二.熟练 ceph 的用户管理及授权  
客户端使用 session key 向 mon 请求所需要的服务，mon 向客户端提供一个 tiket，用于向实际处理数据的 OSD 等服务验证客户端身份，MON 和 OSD 共享同一个 secret.  
ceph 用户需要拥有存储池访问权限，才能读取和写入数据  
ceph 用户必须拥有执行权限才能使用 ceph 的管理命令  
ceph 支持多种类型的用户，但可管理的用户都属于 client 类型  
通过点号来分割用户类型和用户名，格式为 TYPE.ID，例如 client.admin。
```bash
root@ceph-deploy:~# cat /etc/ceph/ceph.client.admin.keyring 
[client.admin]
        key = AQBnFaNj1iyBMBAAd+9hKWXaNw3GYxT9PEXvrQ==
        caps mds = "allow *"
        caps mgr = "allow *"
        caps mon = "allow *"
        caps osd = "allow *"
```
#列 出 指 定 用 户 信 息
```bash
root@ceph-deploy:~# ceph auth get osd.10
[osd.10]
        key = AQB+I6Njk4KWNBAAL09FFayLKF44IgUQ1fjKYQ==
        caps mgr = "allow profile osd"
        caps mon = "allow profile osd"
        caps osd = "allow *"

exported keyring for osd.10
```
#: 列 出 用 户
```bash
cephadmin@ceph-deploy:~$ ceph auth list
mds.ceph-mgr1
        key: AQAdRbFjOwBXIRAAUTdwElBzYPHW+4uFicFC7Q==
        caps: [mds] allow
        caps: [mon] allow profile mds
        caps: [osd] allow rwx
osd.0
        key: AQC0IqNjbcgKIxAA+BCNpQeZiMujR+r+69Miig==
        caps: [mgr] allow profile osd
        caps: [mon] allow profile osd
        caps: [osd] allow *
```
#可以结合使用-o 文件名选项和 ceph auth list 将输出保存到某个文件。
```bash
[cephadmin@ceph-deploy ceph-cluster]$ ceph auth list -o 123.key
```

#ceph auth add
此命令是添加用户的规范方法。它会创建用户、生成密钥，并添加所有指定的能力
添加认证 key：

```bash
cephadmin@ceph-deploy:~/ceph-cluster$ ceph auth add client.tom mon 'allow r' osd 'allow rwx pool=testpool2'
added key for client.tom
```

##验证 key

```bash
cephadmin@ceph-deploy:~/ceph-cluster$ ceph auth get client.tom
[client.tom]
        key = AQD2vbJj8fIiDBAArtJBzQiuPy8nDWPSFVs0bw==
        caps mon = "allow r"
        caps osd = "allow rwx pool=testpool2"
exported keyring for client.tom
```
##创建用户
```bash
cephadmin@ceph-deploy:~/ceph-cluster$ ceph auth get-or-create client.jack mon 'allow r' osd 'allow rwx pool=testpool2'
[client.jack]
        key = AQC/vrJj5kenHhAAGeRJpY64feS4Dn6DD/R8VA==
```
##再次创建用户
```bash
cephadmin@ceph-deploy:~/ceph-cluster$ ceph auth get-or-create client.jack mon 'allow r' osd 'allow rwx pool=testpool2'
[client.jack]
        key = AQC/vrJj5kenHhAAGeRJpY64feS4Dn6DD/R8VA==
```
#ceph auth get-or-create-key:
此命令是创建用户并返回用户密钥，对于只需要密钥的客户端(例如 libvrirt),此命令非常有用。
```bash
[cephadmin@ceph-deploy ceph-cluster]$ ceph auth get-or-create-key client.jack
mon 'allow r' osd 'allow rwx pool=mypool'
AQAtr8dfi37XMhAADbHWEZ0shY1QZ5A8eBpeoQ==
```
用户有 key 就显示没有就创建
#修 改 用 户 能 力
```bash
cephadmin@ceph-deploy:~/ceph-cluster$ ceph auth get client.jack
[client.jack]
        key = AQC/vrJj5kenHhAAGeRJpY64feS4Dn6DD/R8VA==
        caps mon = "allow r"
        caps osd = "allow rwx pool=testpool2"
exported keyring for client.jack
cephadmin@ceph-deploy:~/ceph-cluster$ ceph auth caps client.jack mon 'allow r' osd 'allow rw pool=testpool2'
updated caps for client.jack
cephadmin@ceph-deploy:~/ceph-cluster$ ceph auth get client.jack
[client.jack]
        key = AQC/vrJj5kenHhAAGeRJpY64feS4Dn6DD/R8VA==
        caps mon = "allow r"
        caps osd = "allow rw pool=testpool2"
exported keyring for client.jack
```

#删 除 用 户 
```bash
cephadmin@ceph-deploy:~/ceph-cluster$ ceph auth del client.tom
updated
```
#导出 keyring 至指定文件
```bash
[cephadmin@ceph-deploy ceph-cluster]$ ceph auth get client.user1 -o
ceph.client.user1.keyring
exported keyring for client.user1
```
#验证指定用户的 keyring 文件：
```bash
[cephadmin@ceph-deploy ceph-cluster]$ cat ceph.client.user1.keyring
[client.user1]
key = AQAUUchfjpMqGRAARV6h0ofdDEneuaRnxuHjoQ==
caps mon = "allow r"
caps osd = "allow * pool=mypool"
[cephadmin@ceph-deploy ceph-cluster]$ ceph auth del client.user1 #演示误删除用户
Updated
[cephadmin@ceph-deploy ceph-cluster]$ ceph auth get client.user1 #确认用户被删除
Error ENOENT: failed to find client.user1 in keyring
[cephadmin@ceph-deploy ceph-cluster]$ ceph auth import -i
ceph.client.user1.keyring #导入用户
imported keyring
[cephadmin@ceph-deploy ceph-cluster]$ ceph auth get client.user1 #验证已恢复用户
exported keyring for client.user1
```
#将多 用 户 导 出 至 秘 钥 环 ：
#创建 keyring 文件：
```bash
$ ceph-authtool --create-keyring ceph.client.user.keyring #创建空的 keyring 文件
creating ceph.client.user.keyring
```
#把指定的 admin 用户的 keyring 文件内容导入到 user 用户的 keyring 文件：
```bash
$ceph-authtool ./ceph.client.user.keyring
--import-keyring ./ceph.client.admin.keyring
importing contents of ./ceph.client.admin.keyring into ./ceph.client.user.keyring
```
#验证 keyring 文件：


```bash
[cephadmin@ceph-deploy ceph-cluster]$ ceph-authtool -l ./ceph.client.user.keyring
[client.admin]
key = AQAGDKJfQk/dAxAA3Y+9xoE/p8in6QjoHeXmeg==
caps mds = "allow *"
caps mgr = "allow *"
caps mon = "allow *"
caps osd = "allow *"
```
#再导入一个其他用户的 keyring：
```bash
[cephadmin@ceph-deploy ceph-cluster]$ ceph-authtool ./ceph.client.user.keyring
--import-keyring ./ceph.client.user1.keyring
importing contents of ./ceph.client.user1.keyring into ./ceph.client.user.keyring
```
#再次验证 keyring 文件是否包含多个用户的认证信息：
```bash
[cephadmin@ceph-deploy ceph-cluster]$ ceph-authtool -l ./ceph.client.user.keyring
[client.admin]
key = AQAGDKJfQk/dAxAA3Y+9xoE/p8in6QjoHeXmeg==
caps mds = "allow *"
caps mgr = "allow *"
caps mon = "allow *"
caps osd = "allow *"
[client.user1]
key = AQAUUchfjpMqGRAARV6h0ofdDEneuaRnxuHjoQ==
caps mon = "allow r"
caps osd = "allow * pool=mypool"
```
三. 使用普通客户挂载块存储
#创建存储池：
```bash
cephadmin@ceph-deploy:~/ceph-cluster$ceph osd pool create rbd-data1 32 32

#存储池启用 rbd
cephadmin@ceph-deploy:~/ceph-cluster$ceph osd pool application enable rbd-data1 rbd
#初始化 rbd
cephadmin@ceph-deploy:~/ceph-cluster$rbd pool init -p rbd-data1

#创建两个镜像：
cephadmin@ceph-deploy:~/ceph-cluster$rbd create data-img1 --size 3G --pool rbd-data1 --image-format 2 --image-feature layering
cephadmin@ceph-deploy:~/ceph-cluster$rbd create data-img2 --size 5G --pool rbd-data1 --image-format 2 --image-feature layering


#列出镜像信息
cephadmin@ceph-deploy:~/ceph-cluster$rbd ls --pool rbd-data1
#以 json 格 式 显 示 镜 像 信 息
cephadmin@ceph-deploy:~/ceph-cluster$rbd ls --pool rbd-data1 -l --format json --pretty-format

#创建普通账户
ceph auth add client.shijie mon 'allow r' osd 'allow rwx pool=rbd-data1'

#验证用户信息
ceph auth get client.shijie

#创建用 keyring 文件
cephadmin@ceph-deploy:~/ceph-cluster$ ceph-authtool --create-keyring ceph.client.shijie.keyring

#导出用户 keyring
cephadmin@ceph-deploy:~/ceph-cluster$ ceph auth get client.shijie -o ceph.client.shijie.keyring 

#验证指定用户的 keyring 文件

cephadmin@ceph-deploy:~/ceph-cluster$cat ceph.client.shijie.keyring 
  
#同 步 普 通 用 户 认 证 文 件

cephadmin@ceph-deploy:~/ceph-cluster$ scp ceph.client.shijie.keyring root@172.31.6.109:/etc/ceph/

#管理端验证镜像状态

cephadmin@ceph-deploy:~/ceph-cluster$rbd ls -p rbd-data1 -l

#在client上操作
#映射 rbd

root@ceph-node4:/# rbd -p rbd-data1 map data-img1
/dev/rbd0
root@ceph-node4:/# lsblk
rbd0
root@ceph-node4:/# mkfs.xfs /dev/rbd0
root@ceph-node4:/# mount /dev/rbd0 /data
root@ceph-node4:/# docker run -it -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD="12345678" -v /data:/var/lib/mysql mysql:5.6.46
48374db8541a7fa375c00611373051ef21690e89adfd4c156b3f6ffb0dbe95a2
root@ceph-node4:/data# ls
ibdata1  ib_logfile0  ib_logfile1  mysql  performance_schema  test

#在client上操作
#使用普通用户映射 rbd

root@ceph-node4:/etc/ceph# rbd --user shijie -p rbd-data1 map data-img2
/dev/rbd1
#格式化
root@ceph-node4:/etc/ceph#mkfs.ext4 /dev/rbd0
root@ceph-node4:/etc/ceph# mkdir /data1
root@ceph-node4:/etc/ceph# mount /dev/rbd1 /data1
root@ceph-node4:/etc/ceph# cp /var/log/auth.log /data1
root@ceph-node4:/etc/ceph# cd /data1
root@ceph-node4:/data1# ls
auth.log  lost+found
四. 使用普通用户挂载 cephfs（可以通过 secret 或者 secretfile 的形式多主机同时挂载）
Ceph FS 需要运行 Meta Data Services(MDS)服务，其守护进程为 ceph-mds，ceph-mds进程管理与 cephFS 上存储的文件相关的元数据，并协调对 ceph 存储集群的访问。

#部署MDS服务:
cephadmin@ceph-deploy:~/ceph-cluster$ apt-cache madison ceph-mds
  ceph-mds | 16.2.10-1bionic | https://mirrors.tuna.tsinghua.edu.cn/ceph/debian-pacific bionic/main amd64 Packages
cephadmin@ceph-deploy:~/ceph-cluster$ apt install ceph-mds=16.2.10-1bionic

#创建CephFS meta data和data存储池
[cephadmin@ceph-deploy ceph-cluster]$ ceph osd pool create cephfs-metadata 32 32
pool 'cephfs-metadata' created #保存 metadata 的 pool
[cephadmin@ceph-deploy ceph-cluster]$ ceph osd pool create cephfs-data 64 64
pool 'cephfs-data' created #保存数据的 pool
[cephadmin@ceph-deploy ceph-cluster]$ ceph fs new mycephfs cephfs-metadata
cephfs-data
new fs with metadata pool 7 and data pool 8
cephadmin@ceph-deploy:~/ceph-cluster$ ceph fs ls
name: mycephfs, metadata pool: cephfs-metadata, data pools: [cephfs-data ]
#查看指定 cephFS 状态

cephadmin@ceph-deploy:~/ceph-cluster$ ceph fs status mycephfs
mycephfs - 0 clients
RANK  STATE      MDS        ACTIVITY     DNS    INOS   DIRS   CAPS  
 0    active  ceph-mgr1  Reqs:    0 /s    10     13     12      0   
      POOL         TYPE     USED  AVAIL  
cephfs-metadata  metadata   146k  18.9T  
  cephfs-data      data       0   18.9T  
MDS version: ceph version 16.2.10 (45fa1a083152e41a408d15505f594ec5f1b4fe17) pacific (stable)
#验证cephFS服务状态

cephadmin@ceph-deploy:~$ ceph mds stat
mycephfs:1 {0=ceph-mgr1=up:active}

#创建客户端账户
cephadmin@ceph-deploy:~/ceph-cluster$ceph auth add client.yanyan mon 'allow r' mds 'allow rw' osd 'allow rwx pool=cephfs-data'
#验证账户
[cephadmin@ceph-deploy ceph-cluster]$ ceph auth get client.yanyan
exported keyring for client.yanyan
[client.yanyan]
key = AQCxpdhfjQt1OxAAGe0mqTMveNu2ZMEem3tb0g==
caps mds = "allow rw"
caps mon = "allow r"
caps osd = "allow rwx pool=cephfs-data"
#创建keyring 文件
[cephadmin@ceph-deploy ceph-cluster]$ ceph auth get client.yanyan -o
ceph.client.yanyan.keyring
exported keyring for client.yanyan
#创建 key 文件：

[cephadmin@ceph-deploy ceph-cluster]$ ceph auth print-key client.yanyan > yanyan.key
#验证用户的 keyring 文件

[cephadmin@ceph-deploy ceph-cluster]$ cat ceph.client.yanyan.keyring
[client.yanyan]
key = AQCxpdhfjQt1OxAAGe0mqTMveNu2ZMEem3tb0g==
caps mds = "allow rw"
caps mon = "allow r"
caps osd = "allow rwx pool=cephfs-data"

#同步客户端认证文件 ：

[cephadmin@ceph-deploy ceph-cluster]$ scp ceph.conf ceph.client.yanyan.keyring
yanyan.key root@172.31.6.109:/etc/ceph/

#客户端验证权限

root@ceph-node4:~# ceph --user yanyan -s
  cluster:
    id:     7c088d6f-06b0-4584-b23f-c0f150af51d4
    health: HEALTH_OK
  services:
    mon: 3 daemons, quorum ceph-mon1,ceph-mon2,ceph-mon3 (age 24m)
    mgr: ceph-mgr1(active, since 65m)
    mds: 1/1 daemons up
    osd: 16 osds: 16 up (since 24m), 16 in (since 13d)
    rgw: 1 daemon active (1 hosts, 1 zones)
  data:
    volumes: 1/1 healthy
    pools:   10 pools, 329 pgs
    objects: 296 objects, 218 MiB
    usage:   948 MiB used, 60 TiB / 60 TiB avail
    pgs:     329 active+clean

#客户端通过 key 文件挂载:

 root@ceph-node4:~#mkdir /data
 root@ceph-node4:/etc/ceph# mount -t ceph 172.31.6.101:6789,172.31.6.102:6789,172.31.6.103:6789:/ /data -o name=yanyan,secretfile=/etc/ceph/yanyan.key
root@ceph-node4:/etc/ceph# df -h
Filesystem                                               Size  Used Avail Use% Mounted on
udev                                                     955M     0  955M   0% /dev
172.31.6.101:6789,172.31.6.102:6789,172.31.6.103:6789:/   19T     0   19T   0% /data

#客户端通过key挂载

root@ceph-node3:~# mkdir /data
root@ceph-node3:~# mount -t ceph 172.31.6.101:6789,172.31.6.102:6789,172.31.6.103:6789:/ /data -o name=yanyan,secret=AQAfebVjaIPgABAAzkW4ChX2Qm2Sha/5twdxPA==
root@ceph-node3:~# df -h
Filesystem                                               Size  Used Avail Use% Mounted on
udev                                                     955M     0  955M   0% /dev
172.31.6.101:6789,172.31.6.102:6789,172.31.6.103:6789:/   19T     0   19T   0% /data
root@ceph-node3:~# cp /var/log/auth.log /data
root@ceph-node3:~# cd /data
root@ceph-node3:/data# ls
auth.log
root@ceph-node3:/data# vim auth.log 
root@ceph-node3:/data# echo "12345678" >> auth.log 
root@ceph-node3:/data# echo "testlog" >> auth.log
#在node4客户端上查看cephfs挂载点/data 目录下内容，已经同步

root@ceph-node4:/# tail -f /data/auth.log 
Jan  4 22:25:01 ceph-node3 CRON[4365]: pam_unix(cron:session): session closed for user root
12345678
testlog
#客户端内核加载 ceph.ko 模块挂载 cephfs 文件系统

root@ceph-node4:/# lsmod|grep ceph
ceph                  380928  1
libceph               315392  1 ceph
fscache                65536  1 ceph
libcrc32c              16384  5 nf_conntrack,nf_nat,xfs,raid456,libceph
root@ceph-node4:/# modinfo ceph
filename:       /lib/modules/4.15.0-130-generic/kernel/fs/ceph/ceph.ko
license:        GPL
description:    Ceph filesystem for Linux
author:         Patience Warnick <patience@newdream.net>
author:         Yehuda Sadeh <yehuda@hq.newdream.net>
author:         Sage Weil <sage@newdream.net>
alias:          fs-ceph
srcversion:     CB79D9E4790452C6A392A1C
depends:        libceph,fscache
retpoline:      Y
intree:         Y
name:           ceph
vermagic:       4.15.0-130-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
```

五.实现 MDS 服务的多主一备高可用架构

#当前mds服务器状态
```bash
cephadmin@ceph-deploy:~$ ceph mds stat
mycephfs:1 {0=ceph-mgr1=up:active}
#添加MDS服务器
将 ceph-mgr2 和 ceph-mon2 和 ceph-mon3 作为 mds 服务角色添加至 ceph 集群，最后实两主两备的 mds 高可用和高性能结构。
#mds 服务器安装 ceph-mds 服务

[root@ceph-mgr2 ~]# apt install ceph-mds -y
[root@ceph-mon2 ~]# apt install ceph-mds -y
[root@ceph-mon3 ~]# apt install ceph-mds -y
#添加 mds 服务器

cephadmin@ceph-deploy:~/ceph-cluster$ ceph-deploy mds create ceph-mgr2
cephadmin@ceph-deploy:~/ceph-cluster$ ceph-deploy mds create ceph-mon2
cephadmin@ceph-deploy:~/ceph-cluster$ ceph-deploy mds create ceph-mon3
```
#验证 mds 服务器当前状态：
```bash
[cephadmin@ceph-deploy ceph-cluster]$ ceph mds stat
mycephfs-1/1/1 up {0=ceph-mgr1=up:active}, 3 up:standby
```
#验证 ceph集群当前状态
当前处于激活状态的 mds 服务器有一台，处于备份状态的 mds 服务器有三台。
```bash
cephadmin@ceph-deploy:~/ceph-cluster$ ceph fs status
mycephfs - 0 clients
RANK  STATE      MDS        ACTIVITY     DNS    INOS   DIRS   CAPS  
 0    active  ceph-mgr1  Reqs:    0 /s    16     14     12      0   
      POOL         TYPE     USED  AVAIL  
cephfs-metadata  metadata   282k  18.9T  
  cephfs-data      data     564k  18.9T  
STANDBY MDS  
```
#当前的文件系统状态:
```bash
cephadmin@ceph-deploy:~/ceph-cluster$ ceph fs get mycephfs
Filesystem 'mycephfs' (1)
fs_name        mycephfs
epoch        28
flags        12
created        2023-01-01T19:09:29.258956+0800
modified        2023-01-05T14:58:00.369468+0800
tableserver        0
root        0
session_timeout        60
session_autoclose        300
max_file_size        1099511627776
required_client_features        {}
last_failure        0
last_failure_osd_epoch        406
compat        compat={},rocompat={},incompat={1=base v0.20,2=client writeable ranges,3=default file layouts on dirs,4=dir inode in separate object,5=mds uses versioned encoding,6=dirfrag is stored in omap,7=mds uses inline data,8=no anchor table,9=file layout v2,10=snaprealm v2}
max_mds        1
in        0
up        {0=144106}
failed        
damaged        
stopped        
data_pools        [8]
metadata_pool        7
inline_data        disabled
balancer        
standby_count_wanted        1
[mds.ceph-mgr1{0:144106} state up:active seq 27 addr [v2:172.31.6.104:6800/428364709,v1:172.31.6.104:6801/428364709] compat {c=[1],r=[1],i=[7ff]}]

#设置处于激活状态mds的数量
目前有四个 mds 服务器，但是有一个主三个备，可以优化一下部署架构，设置为为两主两备。

cephadmin@ceph-deploy:~/ceph-cluster$ ceph fs set mycephfs max_mds 2
cephadmin@ceph-deploy:~/ceph-cluster$ ceph fs status
mycephfs - 0 clients
RANK  STATE      MDS        ACTIVITY     DNS    INOS   DIRS   CAPS  
 0    active  ceph-mgr1  Reqs:    0 /s    16     14     12      0   
 1    active  ceph-mon2  Reqs:    0 /s    10     13     11      0   
      POOL         TYPE     USED  AVAIL  
cephfs-metadata  metadata   354k  18.9T  
  cephfs-data      data     564k  18.9T  
STANDBY MDS  
 ceph-mgr2   
 ceph-mon3   
MDS version: ceph version 16.2.10 (45fa1a083152e41a408d15505f594ec5f1b4fe17) pacific (stable)
```


安装完成后ceph -s提示：“mon is allowing insecure global_id reclaim”。

解决方案：禁用不安全模式
```bash
ceph config set mon auth_allow_insecure_global_id_reclaim false
```
输入完成后需要等待5-10秒。

PG数量计算公式：

（总OSD数量*100）/ 副本数（复制分数，默认为3）= PG数量

一般情况下结果取2的N次方，尽量先设置小点，后期可以增大。如果先设置的比较大的话后期减小风险较高，所以尽量取小的2的N次方结果。
建一个存储池，要想使用ceph的存储功能，必须先创建存储池
```bash
ceph osd pool create rbd 128 128 
```

初始化存储池
```bash
rbd pool init -p rbd
```
1.设置存储池副本数
```bash
[root@controller-1 ~]# ceph osd pool get rbd size
size: 2
[root@controller-1 ~]# ceph osd pool set rbd size 1
set pool 1 size to 1
```
升级client的虚拟机内核到5版本

修改client下文件权限
```bash
chmod +r /etc/ceph/ceph.client.admin.keyring
client节点创建设备镜像，单位是M
rbd create --size 4096 --pool rbd img
client节点映射镜像到主机：
rbd map img --name client.admin
client节点格式化块设备
mkfs.ext4 -m 0 /dev/rbd/rbd/foo 
client节点挂载mount块设备
mkdir /mnt/ceph-block-device
mount /dev/rbd/rbd/foo /mnt/ceph-block-device -o discard
创建文件系统时报不支持EC数据池问题
当拥有一个ceph_metadata元数据副本类型池和一个ceph_data数据EC类型池时，建立文件系统：
ceph fs new cephfs cephfs_metadata cephfs_data
N版可能会报：
Error EINVAL: pool 'cephfs_data' (id '11') is an erasure-coded pool. Use of an EC pool for the default data pool is discouraged; see the online CephFS documentation for more information. Use --force to override.
加上—force后：
ceph fs new cephfs cephfs_metadata cephfs_data --force

也可能会报：

Error EINVAL: pool 'cephfs_data' (id '11') is an erasure-coded pool, with no overwrite support

这是需要手动设置ceph_data池 allow_ec_overwrites=true
ceph osd pool set cephfs_data allow_ec_overwrites true

再执行
ceph fs new cephfs cephfs_metadata cephfs_data –forc
就可以创建文件系统成功。
```