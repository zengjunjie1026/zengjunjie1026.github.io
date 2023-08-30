---
title: centos升级git
date: 2023-08-23 17:44:41
tags: server
---

1.2 Centos7
```bash
wget http://opensource.wandisco.com/centos/7/git/x86_64/wandisco-git-release-7-1.noarch.rpm
rpm -ivh wandisco-git-release-7-1.noarch.rpm
```
# 或者
```bash
wget http://opensource.wandisco.com/centos/7/git/x86_64/wandisco-git-release-7-2.noarch.rpm
rpm -ivh wandisco-git-release-7-2.noarch.rpm
```
2. 安装git 2.x
```bash
yum install git -y
```


3. 验证
```bash
git --version 
```