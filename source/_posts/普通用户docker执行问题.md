---
title: 普通用户docker执行问题
date: 2023-08-18 17:27:17
tags:
---

通过将用户添加到docker用户组可以将sudo去掉，命令如下

```bash
sudo groupadd docker #添加docker用户组

sudo gpasswd -a $USER docker #将登陆用户加入到docker用户组中

newgrp docker #更新用户组
```