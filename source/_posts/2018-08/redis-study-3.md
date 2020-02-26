---
title: Redis（三）——Redis键(key)
date: 2018-08-18 10:22:30
tags: [Redis]
categories: Redis
---
![blog picture](redis-study-3/redis-3.jpg)

> Redis 键命令用于管理Redis的键。  

语法：
```
command keyName
```
## Redis键命令
> 列举部分redis键相关的基本命令

### DEL key
> 删除已存在的键。不存在的key则会被忽略。  

语法：
```
DEL keyName
```
返回值：`被删除key的数量。`
例：
```
127.0.0.1:6379> set name "zrx"
OK
127.0.0.1:6379> get name
"zrx"
127.0.0.1:6379> del name
(integer) 1
127.0.0.1:6379> get name
(nil)
```

### EXISTS key
> 用于检查指定的key是否存在。  

语法：
```
EXISTS keyName
```
返回值：key存在返回1，否则返回0。
例：
```
127.0.0.1:6379> set name "a"
OK
127.0.0.1:6379> exists name
(integer) 1
127.0.0.1:6379> del name
(integer) 1
127.0.0.1:6379> exists name
(integer) 0
```
<!-- more -->
### EXPIRE key seconds
> 设置key的过期时间。key过期后将不再可用。
语法:
```
expire key seconds
```

返回值：设置成功返回1，key不存在或不能为key设置过期时间时返回0。
例：
```
127.0.0.1:6379> expire name 20
(integer) 1
```
### PERSIST key
> 移除给定key的过期时间，使得key永不过期。

```
PERSIST keyName
```
过期时间移除成功时，返回1，key不存在或key没有设置过期时间，返回0。

### RENAME old_key new_key
> 修改key的名称。

修改成功时提示OK，失败时返回一个错误。
### TYPE keyName
> 返回key所存储的值的类型。

返回key的数据类型有：
- none ：key不存在
- string：字符串
- list：列表
- set：集合
- zset：有序集
- hash： 哈希表

### keys pattern
> 查找所有符合给定模式的key。

获取redis中所有的key：
```
keys *
```

### 参考资料
[http://www.redis.net.cn/order/3528.html](http://www.redis.net.cn/order/3528.html)