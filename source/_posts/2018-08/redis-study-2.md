---
title: Redis学习笔记（二）——Redis数据类型
date: 2018-08-17 15:32:33
tags: [Redis]
categories: Redis
---
![Redis picture](redis-study-2/redis-2.jpg)
Redis支持5种数据类型：
- string：字符串
- hash：哈希
- list：列表
- set： 集合
- zset：有序集合（sorted set） 

## String：字符串
string是Redis最基本的类型，一个key对应一个value；
string类型是二进制安全的，即Redis的string可包含任何数据。比如jpg图片或者序列化的对象。
string类型是Redis最基本的数据类型，string类型的值最大能存储512MB。
> 语法格式：
set key value
get key

```
127.0.0.1:6379> set name 'zrx'
OK
127.0.0.1:6379> get name
"zrx"
```
> Redis 命令不区分大小写。上面例子 键为`name`，值为`zrx`。使用了set先给name赋值为'zrx'，再使用了get取键对应的值。  

<!-- more -->

## Hash：哈希
Hash是键值对集合，适用于存储对象。Redis哈希（散列）是字符串字段和字符串值之间的映射。
> 语法格式：
hmset key field value
hget key field

```
127.0.0.1:6379> hmset myhash field1 "hello" field2 "world"
OK
127.0.0.1:6379> hget myhash field1
"hello"
127.0.0.1:6379> hget myhash field2
"world"
127.0.0.1:6379> hmset myhash name "zrx" age "twenty"
OK
127.0.0.1:6379> hget myhash name
"zrx"
127.0.0.1:6379> hget myhash age
"twenty"
```

hmset 设置`field=>value`对，hget获取对应field对应的value。
上面例子中`field=>value`对有：
`field1=>"hello"`,`field2=>"world"`,`name=>"zrx"`,`age=>"twenty"`。
> 每个hash可以存储2<sup>32</sup>-1个键值对。

## List：列表
Redis列表是简单的字符串列表，按照插入顺序排序。可以添加一个元素到列表的头部（左边）或尾部（右边）。
> 语法格式：
lpush key member

```
127.0.0.1:6379> lpush list1 good
(integer) 1
127.0.0.1:6379> lpush list1 study
(integer) 2
127.0.0.1:6379> lpush list1 up
(integer) 3
127.0.0.1:6379> lrange list1 0 2
1) "up"
2) "study"
3) "good"
```

> 列表最大长度为2<sup>32</sup>-1个元素。
## Set：集合
Redis的set是string类型的***无序*** 集合。集合是通过哈希表实现的，因此添加、删除、查找的复杂度都是O(1)。
***sadd命令***
添加一个string元素到key对应的set集合中，成功返回1，元素已在集合中返回0，key对应的set不存在返回错误。
> 语法格式：sadd key member  

```
127.0.0.1:6379> sadd subject java
(integer) 1
127.0.0.1:6379> sadd subject html
(integer) 1
127.0.0.1:6379> sadd subject java
(integer) 0
127.0.0.1:6379> smembers subject
1) "java"
2) "html"
```
值`java`被添加了两次，但根据集合内元素唯一性，第二次添加的元素将忽略。
> 集合中最大的成员数为2<sup>32</sup>-1
## zset：有序集合（sorted set）
添加元素到集合，若元素在集合中存在则更新对应score。
> 语法格式
zadd key score member  

```
127.0.0.1:6379> zadd zname 0 zs
(integer) 1
127.0.0.1:6379> zadd zname 0 ls
(integer) 1
127.0.0.1:6379> zadd zname 0 ww
(integer) 1
127.0.0.1:6379> ZRANGEBYSCORE zname 0 10
1) "ls"
2) "ww"
3) "zs"
```
## 参考资料
[http://www.runoob.com/redis/redis-install.html](http://www.runoob.com/redis/redis-install.html)
[https://www.yiibai.com/redis/redis_quick_guide.html](https://www.yiibai.com/redis/redis_quick_guide.html)

