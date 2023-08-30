---
title: linux硬盘格式化与挂载
date: 2020-03-16 18:01:58
tags:
---

```bash
yum install -y gdisk
fdisk /dev/sdb
m
g
w
```

```bash
mkfs -t ext4 /dev/sdb
mkdir /data
mounr /dev/sdb /data
```


```
base) [root@gpu004:7 /]# fdisk /dev/sdb
WARNING: fdisk GPT support is currently new, and therefore in an experimental phase. Use at your own discretion.
欢迎使用 fdisk (util-linux 2.23.2)。

更改将停留在内存中，直到您决定将更改写入磁盘。
使用写入命令前请三思。


命令(输入 m 获取帮助)：d
No partition is defined yet!

命令(输入 m 获取帮助)：g
Building a new GPT disklabel (GUID: 8BC566A3-7EC7-4A20-887C-107BB9D3D01D)


命令(输入 m 获取帮助)：w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: 设备或资源忙.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)

```