---
title: zerotier
date: 2023-10-23 10:35:10
tags:
---

```bash
iptables -I FORWARD -i ztly56xsfh -j ACCEPT
iptables -I FORWARD -o ztly56xsfh -j ACCEPT
iptables -t nat -I POSTROUTING -o ztly56xsfh -j MASQUERADE
```

zerotier的问题

同一局域网的机器有的延迟400ms有的延迟20ms。这也太奇怪了吧。可能是路由表的原因。

将两个局域网打通。目前只成功了一半，香河的路由不通。但是北京的是可以的，延迟在10ms以内，至少把服务器放在北京延迟非常低。。。。

但是北京到香河的延迟都是400ms，昨天还有7ms的延迟，双向不对等的延迟是什么鬼啊

查看完整路由表

```BASH
route -n

andrew@macintosh:~#route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 enp24s0
0.0.0.0         192.168.2.1     0.0.0.0         UG    1002   0        0 enp24s0
10.147.20.0     0.0.0.0         255.255.255.0   U     0      0        0 ztly56xsfh
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
172.18.0.0      0.0.0.0         255.255.0.0     U     0      0        0 br-9d21bdcc9562
192.168.2.0     0.0.0.0         255.255.255.0   U     100    0        0 enp24s0
192.168.2.0     0.0.0.0         255.255.255.0   U     1002   0        0 enp24s0
192.168.2.0     10.147.20.1     255.255.255.0   UG    5000   0        0 ztly56xsfh
192.168.31.0    10.147.20.203   255.255.255.0   UG    5000   0        0 ztly56xsfh
```

下次需要到香河安装istoreos openwrt路由设备即可异地组网。大大扩展zerotier的可玩性。


关闭wifi
```bash
sudo ip link set wlan0 down

```

问题是zerotier的服务器被墙了，至少ipv4被墙了，ipv6还行，但是延迟很大，400ms
真是日了狗了