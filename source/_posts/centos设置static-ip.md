---
title: centos设置static ip
date: 2023-08-18 11:29:45
tags:
---


archlinux设置固定ip

cd   /etc/netctl/

Ip adds 查看网卡id

vim 网卡id

TYPE=Ethernet
PROXY_METHOD=none
BROWSER_ONLY=no
BOOTPROTO="static"         # 使用静态IP地址，默认为dhcp
IPADDR="192.168.28.5"   # 设置的静态IP地址
NETMASK="255.255.255.0"    # 子网掩码
GATEWAY="192.168.28.1"    # 网关地址
DNS1="192.168.28.1"       # DNS服务器
DEFROUTE=yes
IPV4_FAILURE_FATAL=no
IPV6INIT=yes
IPV6_AUTOCONF=yes
IPV6_DEFROUTE=yes
IPV6_FAILURE_FATAL=no
IPV6_ADDR_GEN_MODE=stable-privacy
NAME=enp0s8
UUID=fb16fac1-9eca-4962-9e2f-a0587174b47c
DEVICE=enp0s8
ONBOOT=yes

如果是centos7设置固定ip
cd /etc/sysconfig/network-scripts

查看网卡id
```bash
2: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:59:05:17 brd ff:ff:ff:ff:ff:ff
    inet 192.168.28.5/24 brd 192.168.28.255 scope global noprefixroute enp0s8
       valid_lft forever preferred_lft forever
    inet6 fe80::750c:27c1:a8c4:bcc8/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
   ```
   enp0s8
vim ifcfg-enp0s8
添加上诉配置文件，修改相应的NAME IPADDR

保存后重启电脑


