---
title: nfs centos
date: 2023-08-17 11:38:04
tags: server
---

```bash
[root@frps.cn ~]# yum install -y nfs-utils rpcbind

[root@frps.cn ~]# systemctl start rpcbind
[root@frps.cn ~]# systemctl enable rpcbind
[root@frps.cn ~]# systemctl start nfs
[root@frps.cn ~]# systemctl enable nfs

#首先检查nfs挂载目录是否正常
[root@nfs ~]# showmount -e localhost
Export list for localhost:
/volume1/nfs01 *

#先在客户端创建数据目录（挂载点位置）
[root@所有节点 ~]# mkdir -p /data1/k8s/
[root@所有节点 ~]# mount -t nfs 10.4.82.118:/volume1/nfs01 /data1/k8s

#现在进行挂载 分别是ip:nfs目录  节点存储目录

挂在完成后我们使用df -h 就可以看到挂载点
[root@所有节点 ~]# df -h|grep 10.4.82.135
```