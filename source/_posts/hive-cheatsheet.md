---
title: hive cheatsheet
date: 2023-08-20 09:24:12
tags:
---

### 1. Hive导出到.csv文件
由于Hive中导出的文件不是以逗号，而是以Tab（或者说’\t’）为分隔符的，因此，下面的命令自己试过可以转换为逗号分隔的文件，也就是真正的csv文件。

当然，有时候可能还需要跟转码的工具进行组合，转换编码格式。
```bash
sed -i ‘s/\t/,/g’ xxx.csv
``````
当然，第一步是
```bash
hive -e “SQL语句” > xxx.csv
```
所以完整的流程代码是

```bash
hive -e "SQL query" > xxx.csv
sed -i 's/\t/,/g' xxx.csv
```
### 2. Hive导入.csv文件建表
注意：

为了配合csv文件，建表的时候，最后一行的row format delimited fields terminated by ‘,’;必须要有，否则列会出问题

（这牵涉到csv和tsv等问题）

所以，在Hive下完整的删表建表导数据的流程如下：

```bash
drop table if exists table_name;
CREATE EXTERNAL TABLE beike.beike_ershoufang (
    details_name string,
    postition_url string ,
    house_url string,
    house_id string,
    house_info string,
    follew_info string,
    subway string,
    total_price float,
    total_price_danwei string,
    unit_price float,
    district string,
    city_name string,
    fetchtime timestamp
)COMMENT '贝壳二手房'
PARTITIONED BY (dt STRING, cd3 STRING)
row format delimited fields terminated by ',';

load data local inpath '/home/andrew/output.csv' 
into table  beike.beike_ershoufang PARTITION(dt='2017-03-31' ,cd3='1389');;
```

### 3. Hive看包括行数在内的信息
```bash
show tblproperties table_name;
desc formatted table_name;
```
### 4. Hive一次写入一个表的多个分区的数据
```bash
set hive.exec.dynamic.partition=true;
set hive.exec.dynamic.partition.mode=nonstrict;
insert overwrite table table1 partition(partition_column)
select col1, col2,..., partition_column from table1;
```
### 5. Hive一次写入大量分区
```
set hive.exec.max.dynamic.partitions=100000;
--每一个mapreduce job允许创建的分区的最大数量，如果超过了这个数量就会报错
set hive.exec.max.dynamic.partitions.pernode=100000;
--hive.exec.max.created.files ：所有的mapreduce job允许创建的文件的最大数量
set hive.exec.max.created.files=10000;
```
### 6避免产生小文件

--在MapReduce的任务结束时合并小文件
```bash
set hive.merge.mapredfiles=true;
```
### 7Hive开启本地模式
```bash
set hive.exec.mode.local.auto=true;
```
### 8查询打印表头
```bash
set hive.cli.print.header=true;
```