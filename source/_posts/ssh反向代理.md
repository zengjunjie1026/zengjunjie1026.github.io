---
title: ssh反向代理
date: 2023-08-16 21:49:11
tags: server,内网穿透
---

### SSH 命令端口转发（Port Forward）  
远程转发到本地端口 -L （端口转发）
命令格式：

```bash
ssh -N -f -L lhost:lport:rhost:rport ruser@rhost

# 
```
访问本地127.0.0.1:8443即可访问www.google.com:443
```bash
ssh -N -f -L [lhost:]8443:www.google.com:443 root@1.1.1.1
```
本地转发到远程端口 -R （内网穿透）
命令格式：
```bash
ssh -N -f -R rhost:rport:lhost:lport ruser@rhost
```
访问1.1.1.1:443即可访问本地127.0.0.1:8443
```bash
ssh -N -f -R [rhost:]443:localhost:8443 root@1.1.1.1
```
Socks 转发 -D
命令格式：
```bash
ssh -N -f -D lhost:lport ruser@rhost
```
通过ssh建立Socks通道，本地proxychains配置127.0.0.1:8080即可转发到1.1.1.1
```bash
ssh -N -f -D [lhost:]8080 root@1.1.1.1
```