---
title: spark group by 操作
date: 2022-08-16 17:54:33
tags:
---


scala-spark-dataframe—groupby基本操作
```bash

[andrew@hadoop102 bin]$ ./spark-shell
2022-05-07 20:35:13,392 WARN util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
Setting default log level to "WARN".
To adjust logging level use sc.setLogLevel(newLevel). For SparkR, use setLogLevel(newLevel).
Spark context Web UI available at http://hadoop102:4040
Spark context available as 'sc' (master = local[*], app id = local-1651926921962).
Spark session available as 'spark'.
Welcome to
      ____              __
     / __/__  ___ _____/ /__
    _\ \/ _ \/ _ `/ __/  '_/
   /___/ .__/\_,_/_/ /_/\_\   version 3.0.0
      /_/

Using Scala version 2.12.10 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_212)
Type in expressions to have them evaluated.
Type :help for more information.


scala> val df = spark.createDataset(Seq(
     |   ("aaa",1,2),("bbb",3,4),("ccc",3,5),("bbb",4, 6))   ).toDF("key1","key2","key3")
df: org.apache.spark.sql.DataFrame = [key1: string, key2: int ... 1 more field]

scala> df.show()
+----+----+----+
|key1|key2|key3|
+----+----+----+
| aaa|   1|   2|
| bbb|   3|   4|
| ccc|   3|   5|
| bbb|   4|   6|
+----+----+----+


scala> df.printSchema()
root
 |-- key1: string (nullable = true)
 |-- key2: integer (nullable = false)
 |-- key3: integer (nullable = false)


scala> df.groupBy("key1").count.show
+----+-----+
|key1|count|
+----+-----+
| ccc|    1|
| aaa|    1|
| bbb|    2|
+----+-----+


scala> df.select("key1").distinct.show
+----+
|key1|
+----+
| ccc|
| aaa|
| bbb|
+----+


scala> df.select("key1").distinct.count
res4: Long = 3

scala> f.groupBy("key1").count.sort("key1").show
<console>:24: error: not found: value f
       f.groupBy("key1").count.sort("key1").show
       ^

scala> df.groupBy("key1").count.sort("key1").show
+----+-----+
|key1|count|
+----+-----+
| aaa|    1|
| bbb|    2|
| ccc|    1|
+----+-----+


scala> df.groupBy("key1").count.sort($"count".desc).show
+----+-----+
|key1|count|
+----+-----+
| bbb|    2|
| ccc|    1|
| aaa|    1|
+----+-----+


scala> df.groupBy("key1").count.withColumnRenamed("count", "cnt").sort($"cnt".desc).show
+----+---+
|key1|cnt|
+----+---+
| bbb|  2|
| aaa|  1|
| ccc|  1|
+----+---+


scala> df.groupBy("key1").agg(count("key1").as("cnt")).show
+----+---+
|key1|cnt|
+----+---+
| ccc|  1|
| aaa|  1|
| bbb|  2|
+----+---+


scala>  df.groupBy("key1").agg(count("key1"), max("key2"), avg("key3")).show
+----+-----------+---------+---------+
|key1|count(key1)|max(key2)|avg(key3)|
+----+-----------+---------+---------+
| ccc|          1|        3|      5.0|
| aaa|          1|        1|      2.0|
| bbb|          2|        4|      5.0|
+----+-----------+---------+---------+


scala> f.groupBy("key1")
<console>:24: error: not found: value f
       f.groupBy("key1")
       ^

scala>        df.groupBy("key1").agg("key1"->"count", "key2"->"max", "key3"->"avg").show
+----+-----------+---------+---------+
|key1|count(key1)|max(key2)|avg(key3)|
+----+-----------+---------+---------+
| ccc|          1|        3|      5.0|
| aaa|          1|        1|      2.0|
| bbb|          2|        4|      5.0|
+----+-----------+---------+---------+


scala> df.groupBy("key1").agg(Map(("key1","count"), ("key2","max"), ("key3","avg"))).show
+----+-----------+---------+---------+
|key1|count(key1)|max(key2)|avg(key3)|
+----+-----------+---------+---------+
| ccc|          1|        3|      5.0|
| aaa|          1|        1|      2.0|
| bbb|          2|        4|      5.0|
+----+-----------+---------+---------+


scala> df.groupBy("key1").agg(count("key1").as("cnt"), max("key2").as("max_key2"), avg("key3").as("avg_key3")).sort($"cnt",$"max_key2".desc).show
+----+---+--------+--------+
|key1|cnt|max_key2|avg_key3|
+----+---+--------+--------+
| ccc|  1|       3|     5.0|
| aaa|  1|       1|     2.0|
| bbb|  2|       4|     5.0|
+----+---+--------+--------+

package groupby

import org.apache.spark.SparkConf
import org.apache.spark.sql.SparkSession


object demos {

  def main(args: Array[String]): Unit = {
    val conf = new SparkConf().setAppName("LzSparkDatasetExamples").setMaster("local[*]")
    val sparkSession = SparkSession.builder().enableHiveSupport().config(conf).getOrCreate()

//    //LOGGER.info("-------- this is info --------")
    import sparkSession.implicits._
    val df = sparkSession.createDataset(Seq(
      ("aaa", 1, 2),
      ("bbb", 3, 4),
      ("ccc", 3, 5),
      ("bbb", 4, 6)
    )).toDF("key1", "key2", "key3")


    import org.apache.spark.sql.functions._
    //LOGGER.info("--------df.groupBy(\"key1\").count().show()-----------")
    df.groupBy("key1").count().show()
    //LOGGER.info("--------df.select(\"key1\").distinct().show()-----------")
    df.select("key1").distinct().show()
    val key1Count = df.select("key1").distinct().count()
    //LOGGER.info("--------df.select(\"key1\").distinct().count()-----------" +key1Count)
    //LOGGER.info("--------df.groupBy(\"key1\").count().sort(\"key1\").show()-----------")
    df.groupBy("key1").count().sort("key1").show()
    //LOGGER.info("--------df.groupBy(\"key1\").count().sort($\"key1\".desc).show()-----------")
    df.groupBy("key1").count().sort($"key1".desc).show()
    //LOGGER.info("--------df.groupBy(\"key1\").count.withColumnRenamed(\"count\", \"cnt\").sort($\"cnt\".desc).show-----------")
    df.groupBy("key1").count
      .withColumnRenamed("count", "cnt").sort($"cnt".desc).show()
    //LOGGER.info("--------df.groupBy(\"key1\").agg(count(\"key1\").as(\"cnt\")).show-----------")
    df.groupBy("key1").agg(count("key1").as("cnt")).show()

    // 使用agg聚合函数
    df.groupBy("key1").agg(count("key1"), max("key2"), avg("key3")).show
    df.groupBy("key1").agg("key1"->"count", "key2"->"max", "key3"->"avg").show()
    df.groupBy("key1").agg(Map(("key1","count"), ("key2","max"), ("key3","avg"))).show()
    df.groupBy("key1").agg(("key1","count"), ("key2","max"), ("key3","avg")).show
    df.groupBy("key1")
      .agg(count("key1").as("cnt"), max("key2").as("max_key2"), avg("key3").as("avg_key3"))
      .sort($"cnt",$"max_key2".desc).show



  }

}

```
