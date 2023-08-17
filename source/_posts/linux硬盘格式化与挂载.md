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