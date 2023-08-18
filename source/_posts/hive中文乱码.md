---
title: hive中文乱码
date: 2023-08-18 17:25:57
tags:
---

在metastroe

（1）修改表字段注解和表注解
```bash
alter table COLUMNS_V2 modify column COMMENT varchar(256) character set utf8;
alter table TABLE_PARAMS modify column PARAM_VALUE varchar(4000) character set utf8;
```
（2）修改分区字段注解

```bash
alter table PARTITION_PARAMS modify column PARAM_VALUE varchar(4000) character set utf8 ;
alter table PARTITION_KEYS modify column PKEY_COMMENT varchar(4000) character set utf8;
```
（3）修改索引注解
```bash
alter table INDEX_PARAMS modify column PARAM_VALUE varchar(4000) character set utf8;
```
修改hive-site.xml配置文件
```bash
<property>
    <name>javax.jdo.option.ConnectionURL</name>
    <value>jdbc:mysql://IP:3306/db_name?createDatabaseIfNotExist=true&amp;useUnicode=true&characterEncoding=UTF-8</value>
    <description>JDBC connect string for a JDBC metastore</description>
</property>
```