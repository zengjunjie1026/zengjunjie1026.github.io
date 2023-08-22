---
title: pyspark mongodb
date: 2023-08-21 17:35:19
tags:
---


### 1.创建pyspark与mongodb的连接，首先加载依赖包，其有三种方式：

#### 1）直接将其放在在安装spark的jars目录下；

#### 2）在spark_submit中，添加依赖包信息；

#### 3）在创建spark的对象的时候添加依赖信息，具体案例如下图所示

```shell
spark = SparkSession \
    .builder \
    .appName('mongo connection') \
    .config("spark.mongodb.input.uri", "mongodb://节点:端口号/dev.myCollection?readPreference=primaryPreferred") \
    .config("spark.mongodb.output.uri", "mongodb://节点:端口号/dev.myCollection") \
    .config('spark.jars.packages', "org.mongodb.spark:mongo-spark-connector_2.11:2.4.2") \
    .getOrCreate()
```
备注：

config的信息，都可以在spark_submit中添加。

### 2.读取mongodb

```bash
df1 = (
spark.read
.format("mongo")
.option("database", 'dev')
.option("collection", 'test_mongo_connect')
.load()
)
```
### 3.写入mongodb

```bash
df = spark.createDataFrame([(1,), (2,)], ['a'])
(
df.write
.format("mongo")
.mode("overwrite")
.option("database", 'dev')
.option("collection", 'test_mongo_connect')
.save()
)
```
