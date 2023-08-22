---
title: pymongo分片
date: 2023-08-18 17:28:46
tags:
---

```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
import time
from pymongo import MongoReplicaSetClient
from pymongo import MongoClient
# 连接单机
# single mongo
# c = MongoClient(host="192.168.89.151", port=27017) # okay
# 连接集群
# mongo cluster
c = MongoClient('mongodb://192.168.89.151,192.168.89.152,192.168.89.153')#okay
print c.database_names()
```