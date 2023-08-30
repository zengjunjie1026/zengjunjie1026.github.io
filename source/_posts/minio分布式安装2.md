---
title: minio分布式安装2
date: 2023-08-29 10:58:43
tags:
---

yum -y install ntp
systemctl enable ntpd
systemctl start ntpd
timedatectl set-ntp yes
ntpdate -u cn.pool.ntp.org
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime   
watch -n 1 'date'


mkdir /mnt/minio/{app,config,data,logs} -p

#!/bin/bash
export MINIO_ACCESS_KEY=circue
export MINIO_SECRET_KEY=circue@data
/mnt/minio/app/minio server --config-dir /mnt/minio/config  --console-address ":9001" \    
http://10.30.0.40:9000/mnt/minio/data \
http://10.30.0.43:9000/mnt/minio/data \
http://10.30.0.93:9000/mnt/minio/data \
http://10.30.0.72:9000/mnt/minio/data > /mnt/minio/logs/start.txt 2>&1 &



cat minio-cluster.conf 
upstream minio_console {
    server 10.30.0.40:9001 max_fails=3 fail_timeout=5s;
    server 10.30.0.43:9001 max_fails=3 fail_timeout=5s;
    server 10.30.0.93:9001 max_fails=3 fail_timeout=5s;
    server 10.30.0.72:9001 max_fails=3 fail_timeout=5s;
}
upstream minio_api {
    server 10.30.0.40:9000 max_fails=3 fail_timeout=5s;
    server 10.30.0.43:9000 max_fails=3 fail_timeout=5s;
    server 10.30.0.93:9000 max_fails=3 fail_timeout=5s;
    server 10.30.0.72:9000 max_fails=3 fail_timeout=5s;
}

server {
    listen          80;   #或者用80端口也可以
    server_name     10.30.0.41;    #可以用域名
    access_log      /var/log/minio.com_access.log main;
    error_log       /var/log/minio.com_error.log warn;
    location / {
        proxy_next_upstream     http_500 http_502 http_503 http_504 error timeout invalid_header;
        proxy_set_header        Host  $host;
        proxy_set_header        X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_pass              http://minio_console;
        expires                 0;
    }
}

server {
    listen          9001;
    server_name     10.30.0.41;   #可以用域名
    access_log      /var/log/minio.com_access.log main;
    error_log       /var/log/minio.com_error.log warn;
    #root            /mnt/minio/app/;

    location / {
        proxy_next_upstream     http_500 http_502 http_503 http_504 error timeout invalid_header;
        proxy_set_header        Host  $host;
        proxy_set_header        X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_pass              http://minio_api;
        expires                 0;
    }
}

