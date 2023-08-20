---
title: supervisor
date: 2023-08-20 09:28:45
tags:
---

ubuntu supervisor进程管理
Supervisor 是一个用 Python 写的进程管理工具，可以很方便的对进程进行启动、停止、重启等操作。

安装命令：
```bash
sudo apt install supervisor
```
安装成功后，会在/etc/supervisor目录下，生成supervisord.conf配置文件。

你也可以使用echo_supervisord_conf > supervisord.conf命令，生成默认的配置文件（不建议，内容比较多）。

```
[unix_http_server]
file=/var/supervisor/supervisor.sock   ;UNIX socket 文件，supervisorctl 会使用
;chmod=0700                 ;socket文件的mode，默认是0700
;chown=nobody:nogroup       ;socket文件的owner，格式：uid:gid

;[inet_http_server]         ;HTTP服务器，提供web管理界面
;port=127.0.0.1:9001        ;Web管理后台运行的IP和端口，如果开放到公网，需要注意
安全性
;username=andrew             ;登录管理后台的用户名
;password=python             ;登录管理后台的密码

[supervisord]
logfile=/Users/andrew/logs/supervisord.log ;日志文件，默认是 $CWD/supervisord.log
logfile_maxbytes=50MB        ;日志文件大小，超出会rotate，默认 50MB，如果设成0，
表示不限制大小
logfile_backups=10           ;日志文件保留备份数量默认10，设为0表示不备份
loglevel=info                ;日志级别，默认info，其它: debug,warn,trace
pidfile=/var/supervisor/supervisord.pid ;pid 文件
nodaemon=false               ;是否在前台启动，默认是false，即以 daemon 的方式启>动
minfds=1024                  ;可以打开的文件描述符的最小值，默认 1024
minprocs=200                 ;可以打开的进程数的最小值，默认 200
```
进程配置会读取/etc/supervisor/conf.d目录下的*.conf配置文件，我们在此目录下创建一个hwapp.conf进程配置文件：

```bash
[program:frpc-proxys]
directory = /Users/andrew/frp_0.30.0_darwin_amd64
command = /Users/andrew/frp_0.30.0_darwin_amd64/frpc -c /Users/andrew/frp_0.30.0_darwin_amd64/frpc-aliyun-5900.ini
autostart = True
autorestart = True
user = andrew
startsecs=3
stderr_logfile=/Users/andrew/logs/frpc-err.log
stdout_logfile=/Users/andrew/logs/frpc.log
stdout_logfile_maxbytes=200MB
```
设置开机自启和启动

```bash
sudo systemctl enable supervisord
sudo systemctl start supervisord
```
