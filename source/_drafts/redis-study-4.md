---
title: Redis系列（四）——Redis字符串（STRING）
date: 2020-03-03 11:29:12
tags: [Redis]
categories: Redis
---

下面列举一些Redis字符串相关的命令。

### SET key value
> Redis SET命令用于设置给定key的值。若key已经存储其他值，SET就覆盖旧值.

e.g.
```
127.0.0.1:6379> set name zrxJuly
OK
```
对已存在的键进行设置如下：
```
127.0.0.1:6379> set name 雪心玉竹
OK
127.0.0.1:6379> get name
"\xe9\x9b\xaa\xe5\xbf\x83\xe7\x8e\x89\xe7\xab\xb9"
```

### SETEX key seconds value
> 为指定的key设置过期时间seconds (以秒为单位)，若key已存在，原来的值将被覆盖。

e.g.值为zrxJuly的name键，30s后过期。
```
127.0.0.1:6379> setex name 30 zrxJuly
OK
127.0.0.1:6379> ttl name
(integer) 27
127.0.0.1:6379> get name
"zrxJuly"
```

### PSETEX key millisconds value
> 设置过期时间的单位为毫秒（ms），用法与SETEX类似。设置成功时返回OK。

e.g.
```
127.0.0.1:6379> psetex name 6000 zrx
OK
```

### SETNX key value
> SET if Not eXists的简写。在指定key不存在时，为key设置指定的值。若key已存在，则不做任何操作。

e.g.
```
127.0.0.1:6379> SET name zrxjuly
OK
127.0.0.1:6379> setnx name zrxju
(integer) 0
127.0.0.1:6379> get name
"zrxjuly"
127.0.0.1:6379> set name zrx
OK
127.0.0.1:6379> get name
"zrx"
```

### SETRANGE key offset value
> 用来覆盖一个已经存在的key的value。


### APPEND key value

### STRLEN key

### GET key

### GETRANGE key start end

### GETSET key value

### GETBIT key offset

### MSET key value[key value...]

### MGET key1,[key2,key3...]

### INCR key

### INCRBY key increment

### INCRBYFLOAT key increment

### DECR key

### DECRBY key decrement

