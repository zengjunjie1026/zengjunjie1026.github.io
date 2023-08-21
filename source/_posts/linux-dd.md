---
title: linux dd
date: 2023-08-21 17:44:32
tags: server
---

在制作U盘启动的时候,有时候需要用dd命令写入U盘.

```python
sudo dd if=./manjaro-deepin-18.0.2-stable-x86_64.iso of=/dev/sdc bs=4M
sudo watch kill -USR1 $(pgrep ^dd)
```
查看硬盘情况
```python
df -h
```
```bash
##df -h                      
文件系统        容量  已用  可用 已用% 挂载点
dev              32G     0   32G    0% /dev
run              32G  1.4M   32G    1% /run
/dev/nvme0n1p1  938G  194G  696G   22% /
tmpfs            32G   90M   32G    1% /dev/shm
tmpfs            32G     0   32G    0% /sys/fs/cgroup
tmpfs            32G   82M   32G    1% /tmp
/dev/nvme0n1p2  455M   18M  437M    4% /boot/efi
tmpfs           6.3G   28K  6.3G    1% /run/user/1000
/dev/nvme1n1p2  234G   11G  212G    5% /run/media/andrew/ebbbb5d2-99ae-4e7c-855f-eb44554ecadd
/dev/sda4       113G   54G   59G   48% /run/media/andrew/9A3402873402671B
/dev/sdb        120G   45G   76G   37% /run/media/andrew/USB3.0

```

查看硬盘分区
```python
sudo fdisk -l
```
```bash
Disk /dev/nvme0n1：953.89 GiB，1024209543168 字节，2000409264 个扇区
磁盘型号：HS-SSD-C2000                            
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节
磁盘标签类型：gpt
磁盘标识符：9F2B628D-7951-40D7-B172-BBAEFFA299F6

设备             起点       末尾       扇区   大小 类型
/dev/nvme0n1p1 933888 2000397701 1999463814 953.4G Linux 文件系统
/dev/nvme0n1p2   2048     933887     931840   455M Microsoft 基本数据

分区表记录没有按磁盘顺序。


Disk /dev/nvme1n1：238.49 GiB，256060514304 字节，500118192 个扇区
磁盘型号：SAMSUNG MZVLW256HEHP-00000              
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节
磁盘标签类型：gpt
磁盘标识符：DE2A08FE-1B0B-6041-8F6E-93205335DCED

设备              起点      末尾      扇区  大小 类型
/dev/nvme1n1p1    2048   1026047   1024000  500M EFI 系统
/dev/nvme1n1p2 1026048 500118158 499092111  238G Linux 文件系统


Disk /dev/sda：113 GiB，121332826112 字节，236978176 个扇区
磁盘型号：APPLE SSD SD0128
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 4096 字节
I/O 大小(最小/最佳)：4096 字节 / 4096 字节
磁盘标签类型：gpt
磁盘标识符：6151D0C2-B64E-405D-A17C-12F529F48388

设备          起点      末尾      扇区   大小 类型
/dev/sda1     2048   1085439   1083392   529M Windows 恢复环境
/dev/sda2  1085440   1288191    202752    99M EFI 系统
/dev/sda3  1288192   1320959     32768    16M Microsoft 保留
/dev/sda4  1320960 236976127 235655168 112.4G Microsoft 基本数据


Disk /dev/sdb：120 GiB，128849018880 字节，251658240 个扇区
磁盘型号：Flash Disk      
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节
磁盘标签类型：dos
磁盘标识符：0x00000000


Disk /dev/sdc：30 GiB，32212254720 字节，62914560 个扇区
磁盘型号：Flash Disk      
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节
磁盘标签类型：dos
磁盘标识符：0x00000000

设备       启动  起点     末尾     扇区 大小 Id 类型
/dev/sdc1  *    16128 62914559 62898432  30G  c W95 FAT32 (LBA)



```
重新制作文件系统
```python
sudo mkfs -t fat /dev/sdc
```
格式化完成
```bash
mkexfatfs 1.3.0
Creating... done.
Flushing... done.
File system created successfully.
```