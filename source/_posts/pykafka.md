---
title: pykafka
date: 2023-08-18 17:29:44
tags:
---

```python
from pykafka import KafkaClient

client = KafkaClient(hosts="localhost:9092")

topic = client.topics['maoyan_wish']
consumer = topic.get_simple_consumer(consumer_group='test', auto_commit_enable=True, consumer_id='test')
for message in consumer:
  if message is not None:
    print(message.offset, message.value)
```
这个程序貌似是不会停止的