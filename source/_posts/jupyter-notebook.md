---
title: jupyter notebook
date: 2023-08-16 21:48:30
tags: server
---
```bash
(base) andrew@imac:~#jupyter notebook password
Enter password: 
Verify password: 
[NotebookPasswordApp] Wrote hashed password to /Users/andrew/.jupyter/jupyter_notebook_config.json
(base) andrew@imac:~#jupyter notebook --generate-config 
Writing default config to: /Users/andrew/.jupyter/jupyter_notebook_config.py
```


## (一)使用
### 1.终端输入：jupyter notebook --generate-config 

会生成一个配置文件，成功后会显示文件路径（～/.jupyter/jupyter_notebook_config.py）
```bash
c.NotebookApp.ip = '0.0.0.0'
c.NotebookApp.port = 8888
```

### 2.打开路径下的jupyter_notebook_config.py配置文件
找到c.NotebookApp.notebook_dir=修改为自己的工作目录

### 3.在终端输入：jupyter notebook即可打开jupyter，就可以在web端编写python啦！
## (二)设置密码

```bash
jupyter notebook password
```
