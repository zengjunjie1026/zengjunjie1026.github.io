---
title: linux 查找trick
date: 2023-08-18 11:25:17
tags:
---

### 查找大文件

```bash
find / -type f -print0 | xargs -0 du -h | sort -rh | head -n 10
```

### 精确查找

```bash
find / -type f -name "*.conf" | xargs grep -ri "10.0.0.74" -i
```