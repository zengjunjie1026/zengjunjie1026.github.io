---
title: redis分布式安装
date: 2023-08-16 17:59:33
tags: server
---

python 操作redis
```python
import redis

#   连接redis
#   几个常用默认参数：
#   host='localhost', port=6379, db=0, decode_responses=False, password=None
pool = redis.ConnectionPool(host='ip-address', port=6379, decode_responses=True,db=1,password='password')

# ---redis
```


字符串

```python


r = redis.Redis(connection_pool=pool)
#   增加数据：set key value（如果key存在，则修改为新的value）
print(r.set('str_type', 'str_value'))  # 打印True
#   追加数据：append key value
print(r.append('str_type', '_new'))  # 打印13，字符长度
#   查看数据：get key
print(r.get('str_type'))
```

数组

```python

#   在插入数据时，如果该键并不存在，Redis将为该键创建一个
#   在末尾添加数据（列表右边）
r.rpush('list_type', '2', 'xy', 'li_val_end')
#   在头部添加数据（列表左边）
r.lpush('list_type', '1', 'xy', 'li_val_start')

#   查看数据
#   数据为：['li_val_start', 'xy', '1', '2', 'xy', 'li_val_end']
#   下标范围：lrange key start stop
print(r.lrange('list_type', 0, 10))
#   指定下标：lindex key index
print(r.lindex('list_type', -1))

#   删除数据
#   从末尾删除（列表右边）：rpop key
print(r.rpop('list_type'))  # 打印删除的值
#   从头部删除（列表左边）：lpop key
print(r.lpop('list_type'))  # 打印删除的值
#   指定值删除：lrem key count(可以存在多个重复的值，指定value删除的次数) value
print(r.lrem('list_type', 2, 'xy'))  # 打印成功删除的个数
```
字典类型

```python
#   hash类型的值是一个键值对集合，如：h_test : { field1:value1, field2:value2,...}
#   添加数据：hset key field value
print(r.hset('hash_type', 'filed', 'value'))  # 打印成功添加数据的条数
#   查看域值：hget key field
print(r.hget('hash_type', 'filed'))
#   查看所有的field：hkeys key
print(r.hkeys('hash_type'))
#   查看所有的value：hvals key
print(r.hvals('hash_type'))
#   查看所有的键值对：hgetall key
print(r.hgetall('hash_type'))
```

# python zset
```python
conn=redis.StrictRedis(host='192.168.80.41',port=6379,db=0)
conn.zadd('znames',100,'jiang')
conn.zadd('znames',20,'wolson')
    #向有顺集合中增加一个元素jiang、它的分值为100

print(conn.zscore('znames','jiang'))
    #获取jiang这个元素的分值

print(conn.zrange('znames',0,-1,desc=True,withscores=True))
    #获取集合中指定序列内的元素

print(conn.zrangebyscore('znames',80,100))
    #获取指定分数范围内的元素

newScore=conn.zincrby('znames','wolson',10)
print(newScore)
print(conn.zscore('znames','wolson'))
    #增加指定元素的分值

print(conn.zcard('znames'))
    #获取集合中的元素数

print(conn.zcount('znames',90,101))
    #获取分数范围内的元素数量

conn.zrem('znames','wolson')
print(conn.zrange('znames',0,-1))
    #删除集合中指定元素
pass

```