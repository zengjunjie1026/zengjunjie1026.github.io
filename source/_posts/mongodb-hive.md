---
title: mongodb hive
date: 2023-08-21 17:31:29
tags: server
---

.背景
公司希望使用MongoDB作为后端业务数据库，使用Hadoop平台作为数据平台。最开始是先把数据从MongoDB导出来，然后传到HDFS，然后用Hive/MR处理。我感觉这也太麻烦了，现在不可能没有人想到这个问题，于是就搜了一下，结果真找到一个MongoDB Connector for Hadoop


1.版本一定要按它要求的来，jar包去http://mvnrepository.com/下载就可以了，使用Hive只需要三个：
mongo-hadoop-core-1.5.1.jar
mongo-hadoop-hive-1.5.1.jar
mongo-java-driver-3.2.1.jar
2.将jar包拷到 <{HADOOP_HOME}/lib与</script>{HIVE_HOME}/lib下，然后启动Hive，加入jar包
```bash
$ hive

Logging initialized using configuration in jar:file:/home/hadoop/opt/apache-hive-1.2.1-bin/lib/hive-common-1.2.1.jar!/hive-log4j.properties
hive> add jar /opt/module/hadoop/opt/hive/lib/mongo-hadoop-hive-1.5.1.jarr;
hive> add jar /opt/module/hadoop/opt/hive/lib/mongo-java-driver-3.2.1.jarr;
```
Hive Usage有两种连接方式:

其一MongoDB-based 直接连接hidden节点，使用 com.mongodb.hadoop.hive.MongoStorageHandler做数据Serde
其二BSON-based 将数据dump成bson文件，上传到HDFS系统，使用 com.mongodb.hadoop.hive.BSONSerDe

MongoDB-based方式

```bash
hive> CREATE TABLE eventlog
    > ( 
    >   id string,
    >   userid string,
    >   type string,
    >   objid string,
    >   time string,
    >   source string
    > )
    > STORED BY 'com.mongodb.hadoop.hive.MongoStorageHandler' 
    > WITH SERDEPROPERTIES('mongo.columns.mapping'='{"id":"_id"}') 
    > TBLPROPERTIES('mongo.uri'='mongodb://username:password@ip:port/xxx.xxxxxx');
hive> select * from eventlog limit 10;
OK
5757c2783d6b243330ec6b25    NULL    shb NULL    2016-06-08 15:00:07 NULL
5757c27a3d6b243330ec6b26    NULL    shb NULL    2016-06-08 15:00:10 NULL
5757c27e3d6b243330ec6b27    NULL    shb NULL    2016-06-08 15:00:14 NULL
5757c2813d6b243330ec6b28    NULL    shb NULL    2016-06-08 15:00:17 NULL
5757ee443d6b242900aead78    NULL    shb NULL    2016-06-08 18:06:59 NULL
5757ee543d6b242900aead79    NULL    smb NULL    2016-06-08 18:07:16 NULL
5757ee553d6b242900aead7a    NULL    cmcs    NULL    2016-06-08 18:07:17 NULL
5757ee593d6b242900aead7b    NULL    vspd    NULL    2016-06-08 18:07:21 NULL
575b73b2de64cc26942c965c    NULL    shb NULL    2016-06-11 10:13:06 NULL
575b73b5de64cc26942c965d    NULL    shb NULL    2016-06-11 10:13:09 NULL
Time taken: 0.101 seconds, Fetched: 10 row(s)

```

这时HDFS里是没有存任何数据的，只有与表名一样的文件夹

当你处理的时候，它是直接处理mongo里最新的数据。当然，如果你想存到HDFS里也可以，用CTAS语句就可以。
hive> create table qsstest as select * from eventlog limit 10;

还可以下载下来呢
PS：mongo的用户要有读写权限，jar包别忘了拷进去！
另一种方式我感觉有点没必要，没试，但我找到一篇博客详细写了。
下面转自：MongoDB与Hadoop技术栈的整合应用
BSON-based方式

BSON-based需要先将数据dump出来，但这个时候的dump与export不一样，不需要关心具体的数据内容,不需要指定fields list.

```bash
mongodump --host=datatask01:29017 --db=test --collection=ldc_test --out=/tmp
hdfs dfs -mkdir /dev_test/dli/bson_demo/
hdfs dfs -put /tmp/test/ldc_test.bson /dev_test/dli/bson_demo/
- 创建映射表
create external table temp.ldc_test_bson
(
  id string,
  fav_id array<int>,
  info struct<github:string, location:string>
)
ROW FORMAT SERDE "com.mongodb.hadoop.hive.BSONSerDe"
WITH SERDEPROPERTIES('mongo.columns.mapping'='{"id":"id","fav_id":"fav_id","info.github":"info.github","info.location":"info.location"}')
STORED AS INPUTFORMAT "com.mongodb.hadoop.mapred.BSONFileInputFormat"
OUTPUTFORMAT "com.mongodb.hadoop.hive.output.HiveBSONFileOutputFormat"
location '/dev_test/dli/bson_demo/';
```

查询一下

```bash
0: jdbc:hive2://hd-cosmos-01:10000/default> select * from temp.ldc_test_mongo;
+--------------------+------------------------+-----------------------------------------------------------------+--+
| ldc_test_mongo.id  | ldc_test_mongo.fav_id  |                       ldc_test_mongo.info                       |
+--------------------+------------------------+-----------------------------------------------------------------+--+
| @Tony_老七           | [3,33,333,3333,33333]  | {"github":"https://github.com/tonylee0329","location":"SH/CN"}  |
+--------------------+------------------------+-----------------------------------------------------------------+--+
1 row selected (0.345 seconds)
```
打开数组可以这样

```bash

SELECT id, fid
FROM temp.ldc_test_mongo LATERAL VIEW explode(fav_id) favids AS fid;
-- 访问struct结构数据 
select id, info.github from temp.ldc_test_mongo
```
