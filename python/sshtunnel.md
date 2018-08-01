---
description: 可以通过使用 sshtunnel 模块建立客户端与跳板机的隧道
---

# sshtunnel

## 安装：

```python
pip install sshtunnel
```

## 使用：

![](../.gitbook/assets/06274cea.jpg)

### 通过 sshtunnel 访问 Mysql

#### 首先倒入所要使用的库

```
import MySQLdb
from sshtunnel import SSHTunnelForwarder
```

### 创建一个隧道代理\(...\)

```text
server =  SSHTunnelForwarder(  
    ssh_address_or_host=('10.10.10.128',22),
    ssh_username='root',
    ssh_password='123456',
    remote_bind_address=('127.0.0.1',3306),
    local_bind_address=('127.0.0.1',10000)
  )
```

* ssh\_address\_or\_host
  * 指定跳板机的地址和ssh端口
* ssh\_username
  * 跳板机的用户
* ssh\_password
  * 跳板机的密码
* remote\_bind\_address
  * 要通过堡垒机访问的ip地址和端口。_注意：_这个ip地址是相对于跳板机来说的，本例子写的是127.0.0.1相当于访问跳板机本身
* local\_bind\_address
  * 将需要通过跳板机连接的服务器的地址和端口（也就是remote\_bind\_address中定义的地址和端口）绑定到本地的10000

### 启动这个隧道代理

```text
server.start()
```

### 连接 Mysql

```text
conn = MySQLdb.connect(
    host='127.0.0.1',       # 此处必须是是127.0.0.1
    port=10000,             # ssh隧道建立是与远程机器绑定的本地端口  
    user='root',  
    passwd='123456',    
    db='weapon')  
```

### 完成，此时就可以使用对数据库进行操作啦

