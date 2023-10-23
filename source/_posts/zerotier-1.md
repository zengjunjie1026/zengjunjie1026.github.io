---
title: zerotier
date: 2023-10-23 10:35:10
tags:
---

```bash
iptables -I FORWARD -i ztqu3pfdod -j ACCEPT
iptables -I FORWARD -o ztqu3pfdod -j ACCEPT
iptables -t nat -I POSTROUTING -o ztqu3pfdod -j MASQUERADE
```

zerotier的问题

同一局域网的机器有的延迟400ms有的延迟20ms。这也太奇怪了吧。可能是路由表的原因。

将两个局域网打通。目前只成功了一半，香河的路由不通。但是北京的是可以的，延迟在10ms以内，至少把服务器放在北京延迟非常低。。。。

但是北京到香河的延迟都是400ms，昨天还有7ms的延迟，双向不对等的延迟是什么鬼啊
