---
description: 内置时间处理模块 time
---

# time

## 基本介绍 {#ji-ben-jie-shao}

**当前时间时间戳**

`time.time()`

 **将时间戳转换为本地时间**

`time.localtime(1533021272)`

 **将本地时间转换为想要的可视化格式**

`time.strftime('%Y-%m-%d', '本地时间')`

 **将可视化时间格式转换为本地时间**

`time.strptime('2018-07-31', '%Y-%m-%d')`

 **将本地时间转换为时间戳**

`time.mktime('本地时间')`

## 常用时间操作组合  {#chang-yong-shi-jian-cao-zuo-zu-he}

 **获得当前时间的指定格式的输出**

`time.strftime('%Y-%m-%d %H:%M', time.localtime(time.time()))`

