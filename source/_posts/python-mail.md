---
title: python mail
date: 2023-08-21 16:25:37
tags: server
---

```python
import smtplib
import time
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText
from loguru import logger

mail_host = 'smtp.163.com'
# 163用户名
mail_user = 'username'
# 密码(部分邮箱为授权码)
mail_pass = '--------------'
# 邮件发送方邮箱地址
sender = 'sender@163.com'
# ff
# 邮件接受方邮箱地址，注意需要[]包裹，这意味着你可以写多个邮件地址群发
receivers = ["xxx@email.com"]


def send(title, messages):
    # 设置email信息
    # 邮件内容设置
    message = MIMEText(messages, 'plain', 'utf-8')
    # message= MIMEMultipart('mixed')
    # 邮件主题
    message['Subject'] = title
    # 发送方信息
    message['From'] = sender
    # 接受方信息

    # 登录并发送邮件
    try:
        smtpObj = smtplib.SMTP(mail_host)
        # smtpObj = smtplib.SMTP_SSL(mail_host)
        # 连接到服务器
        smtpObj.connect(mail_host, 25)
        smtpObj.starttls()
        # 登录到服务器
        smtpObj.login(mail_user, mail_pass)

        # 发送
        for receiver in receivers:
            message["To"] = ", ".join(message)
            # message['To'] = receiver
            smtpObj.sendmail(
                sender, receiver, message.as_string())
        # 退出
        smtpObj.quit()
        logger.info('success')
    except smtplib.SMTPException as e:
        logger.error(f'error {e}')  # 打印错误



if __name__=="__main__":
    for i in range(3):
        send("test",f"hello_{i}")
        time.sleep(3)

```