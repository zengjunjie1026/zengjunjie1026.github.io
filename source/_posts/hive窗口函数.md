---
title: hive窗口函数
date: 2023-08-18 11:31:29
tags: server
---


CREATE TABLE tmp.COSTITEM
( NAME STRING,
ORDERDATE DATE,
COST STRING);

-- 数据加
INSERT INTO  tmp.COSTITEM  VALUES ('jack','2020-01-01','10');
INSERT INTO  tmp.COSTITEM  VALUES ('tony','2020-01-02','15');
INSERT INTO  tmp.COSTITEM  VALUES ('jack','2020-02-03','23');
INSERT INTO  tmp.COSTITEM  VALUES ('tony','2020-01-04','29');
INSERT INTO  tmp.COSTITEM  VALUES ('jack','2020-01-05','46');
INSERT INTO  tmp.COSTITEM  VALUES ('jack','2020-04-06','42');
INSERT INTO  tmp.COSTITEM  VALUES ('tony','2020-01-07','50');
INSERT INTO  tmp.COSTITEM  VALUES ('jack','2020-01-08','55');
INSERT INTO  tmp.COSTITEM  VALUES ('mart','2020-04-08','62');
INSERT INTO  tmp.COSTITEM  VALUES ('mart','2020-04-09','68');
INSERT INTO  tmp.COSTITEM  VALUES ('neil','2020-05-10','12');
INSERT INTO  tmp.COSTITEM  VALUES ('mart','2020-04-11','75');
INSERT INTO  tmp.COSTITEM  VALUES ('neil','2020-06-12','80');
INSERT INTO  tmp.COSTITEM  VALUES ('mart','2020-04-13','94');

SELECT
	name,
	orderdate,
	cost,
	sum(cost) OVER() as sample1,   -- 所有行相加 ok
	sum(cost) over(PARTITION BY name) as sample2,  -- 按name分组，组内数据求和 ok
	sum(cost) OVER(PARTITION BY name ORDER BY orderdate) as sample3,   -- 按name分组，时间排序，组内数据逐个相加 ok
	sum(cost) OVER(PARTITION BY name ORDER BY orderdate ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) as sample4,   -- 组内由起点到当前行的聚合
	sum(cost) OVER(PARTITION BY name ORDER BY orderdate ROWS BETWEEN 1 PRECEDING and CURRENT ROW) as sample5,   -- 组内当前行和前面一行做聚合

	sum(cost) over(PARTITION BY name ORDER BY orderdate ROWS BETWEEN 1 PRECEDING AND 1 FOLLOWING) as sample6,   -- 组内当前行和前一行和后一行聚合

	sum(cost) over(PARTITION BY name ORDER BY orderdate ROWS BETWEEN CURRENT ROW and UNBOUNDED FOLLOWING) as sample7    -- 组内当前行和后面所有行
FROM 
    TEST.COSTITEM 


jack    2020-01-01      10      661.0   176.0   10.0    10.0    10.0    56.0    176.0
jack    2020-01-05      46      661.0   176.0   56.0    56.0    56.0    111.0   166.0
jack    2020-01-08      55      661.0   176.0   111.0   111.0   101.0   124.0   120.0
jack    2020-02-03      23      661.0   176.0   134.0   134.0   78.0    120.0   65.0
jack    2020-04-06      42      661.0   176.0   176.0   176.0   65.0    65.0    42.0
mart    2020-04-08      62      661.0   299.0   62.0    62.0    62.0    130.0   299.0
mart    2020-04-09      68      661.0   299.0   130.0   130.0   130.0   205.0   237.0
mart    2020-04-11      75      661.0   299.0   205.0   205.0   143.0   237.0   169.0
mart    2020-04-13      94      661.0   299.0   299.0   299.0   169.0   169.0   94.0
neil    2020-05-10      12      661.0   92.0    12.0    12.0    12.0    92.0    92.0
neil    2020-06-12      80      661.0   92.0    92.0    92.0    92.0    92.0    80.0
tony    2020-01-02      15      661.0   94.0    15.0    15.0    15.0    44.0    94.0
tony    2020-01-04      29      661.0   94.0    44.0    44.0    44.0    94.0    79.0
tony    2020-01-07      50      661.0   94.0    94.0    94.0    79.0    79.0    50.0
Time taken: 91.905 seconds, Fetched: 14 row(s) 


SELECT name,
       orderdate,
       cost, --当前window内，当前行的前一行到后一行 金额总和
 sum(cast(cost AS INT)) over(PARTITION BY name
                             ORDER BY orderdate DESC ROWS BETWEEN 1 PRECEDING AND 1 FOLLOWING) AS precedingFollow, --当前window内，当前行到最后行的金额总和
 sum(cast(cost AS INT)) over(PARTITION BY name
                             ORDER BY orderdate DESC ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING) AS currentFollow, --当前window内，按照时间进行排序
 row_number() OVER(PARTITION BY name
                   ORDER BY orderdate DESC) AS rank,--用户上次购买的时间
 lag(orderdate,1,'查无结果') over(PARTITION BY name
                              ORDER BY orderdate) AS lastTime,--用户下一次购买的时间
 lead(orderdate,1,'查无结果') over(PARTITION BY name
                               ORDER BY orderdate)AS nextTime,--用户上次购物金额
 lag(cost,1,'查无结果')over(PARTITION BY name
                        ORDER BY orderdate) AS lastCost,--用户下次购物金额
 lead(cost,1,'查无结果') OVER (PARTITION BY name
                           ORDER BY orderdate) AS nextCost,--用户上一次+这次的购物金额
 sum(cast(cost AS INT)) over(PARTITION BY name
                             ORDER BY orderdate ROWS BETWEEN 1 PRECEDING AND CURRENT ROW) AS lastCurrentCost,--用户每月购物金额
 sum(cast(cost AS INT)) over(PARTITION BY name,month(orderdate)
                             ORDER BY month(orderdate)) AS monthCost,--用户当月单词消费最大值
 max(cast(cost AS INT)) over(PARTITION BY name,month(orderdate)
                             ORDER BY orderdate) AS monthMaxCost,--用户当月单词消费最小值
 min(cast(cost AS INT)) over(PARTITION BY name,month(orderdate)
                             ORDER BY orderdate) as monthMinCost
FROM TEST.COSTITEM