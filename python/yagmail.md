---
description: yagmail 模块主要是封装邮件发送方式，使其更加方便快捷
---

# yagmail

```python
# 首先需要建立连接
# 注意建立起连接之后有如果长时间不用发邮件时会失败，再次使用需要重新建立连接
my_mail = yagmail.SMTP(
    user='test@zouri.net',
    password='123456789',
    host='smtp.exmail.qq.com',
    port='465',
    smtp_ssl=True) 
    
# 调用发送邮件方法
my_mail.send(
    to='mazouri@zouri.net',
    subject='标题',
    contents='内容')
# 关闭这个连接
my_mail.close()




# 有附件写法
my_mail.send(
    to='mazouri@zouri.net',
    subject='标题',
    contents=['内容','附件的本地路径'])
my_mail.close()
```



