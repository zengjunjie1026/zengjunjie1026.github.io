---
title: mysql
date: 2023-08-16 21:49:26
tags:
---

### Archlinux  安装mysql；
```bash
Paceman -S mariadb
sudo mariadb-install-db --user=mysql --basedir=/usr --datadir=/var/lib/mysql

Two all-privilege accounts were created.
One is root@localhost, it has no password, but you need to
be system 'root' user to connect. Use, for example, sudo mysql
The second is mysql@localhost, it has no password either, but
you need to be the system 'mysql' user to connect.
After connecting you can set the password, if you would need to be
able to connect as any of these users with a password and without sudo


Sudo systemctl stop mariadb;
mysqld_safe --skip-grant-tables &

Mysql;
Use mysql;
Delete from user where user='';
flush privileges;
set password for root@'localhost'=password('redhat');
set password for mysql@‘ocalhost'=password('redhat');
grant all privileges on *.* to username@'%' identified by 'pass';

Exit

 UPDATE mysql.user SET authentication_string = PASSWORD("pass"), plugin = 'mysql_native_password' WHERE User = 'root' AND Host = 'localhost';
```



## centos linux安装MySQL

优先去yum源中去找
```bash`
yum search mysql-community-server
yum search mysql-server
``
去官网下载mysql:
```bash
https://dev.mysql.com/downloads/mysql/
Select Operating System:
Red Hat Enterprise Linux / Oracle Linux
Select OS Version:
Red Hat Enterprise Linux7 /Oracle Linux7 (x86,64-bit)
```
```bash
需要下载的安装包：
- [x] mysql-community-libs
- [x] mysql-community-common
- [x] mysql-community-client
- [x] mysql-community-server
```
### 安装

```bash
mariadb-libs 被 mysql-community-libs-8.0.32-1.el7.x86_64 取代
rpm -e mariadb-libs —nodeps 卸载一个软件包

rpm -ivh mysql-community-common-8.0.32-1.el7.x86_64.rpm 
rpm -ivh mysql-community-client-plugins-8.0.32-1.el7.x86_64.rpm
rpm -ivh mysql-community-libs-8.0.32-1.el7.x86_64.rpm 
rpm -ivh mysql-community-client-8.0.32-1.el7.x86_64.rpm

  

yum install net-tools
yum install -y perl-Module-Install.noarch

rpm -ivh mysql-community-icu-data-files-8.0.32-1.el7.x86_64.rpm
rpm -ivh mysql-community-server-8.0.32-1.el7.x86_64.rpm
```

### 启动mysql:
```bash
mysqld --initialize初始化
cd /var/lib chown mysql:mysql mysql -R  修改mysql数据文件的拥有者
systemctl start mysqld.service 启动mysql
 systemctl status  mysqld.service 查看mysql的启动状态.     systemctl status firewalld.service查看防火墙的启动状态
 systemctl start  mysqld.service	手动启动mysql		       systemctl stop firewalld.service 关闭防火墙
临时密码：e_z(hG9M=ZfD 
修改密码：alter user 'root'@'localhost' identified by 'pass'
quit:退出mysql
systemctl enable mysqld.service将mysql设置为随机启动
systemctl disable mysqld.service 将mysql设置为不随机启动
```