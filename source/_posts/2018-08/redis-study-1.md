---
title: Redis学习笔记（一）——初识Redis
date: 2018-08-17 11:36:57
tags: [Redis]
categories: Redis
---
![Redis picture](redis-study-1/redis-1.png)
## Redis介绍
- Redis是一个开源、高级的键值存储和一个适用的解决方案，用于构建高性能、可扩展的web应用程序，遵循BSD协议<a href="#to-bsd"><sup>[1]</sup></a>，是一个高性能的key-value数据库。
- Redis特点：
  * 支持数据持久化。可将内存中的数据保存在磁盘中，重启时可再次加载使用。
  * 数据结构存储类型丰富，eg：list,set,zset,hash,string等。
  * 支持master-slave模式的数据备份。
<!-- more -->  

## Redis优点
- 性能高，读写速度快。
- 数据类型丰富。支持大多数数据类型的操作，如列表、集合、排序集、散列。
- 操作具有原子性。要么成功执行，要么失败都不执行。单个操作是原子性的，多个操作也支持事务原子性。  

## Redis与同类产品作为高速缓存比较
除了Redis，同样可以作为缓存的有Ehcache、Memcached。
- Ehcache：Java开源项目，引入jar包即可方便的使用。
- Memcached：如果开启多线程模式，读取速度将会有很大提高。数据只会存储于内存中，挂掉后不可恢复。
- Redis：数据结构丰富；支持主从、分片等多种高级特性，用于负载均衡和容灾，具有高可用性。

## 参考资料
[http://www.runoob.com/redis/redis-install.html](http://www.runoob.com/redis/redis-install.html)
[https://www.yiibai.com/redis/redis_quick_guide.html](https://www.yiibai.com/redis/redis_quick_guide.html)
[https://www.cnblogs.com/yiwangzhibujian/p/7053840.html](https://www.cnblogs.com/yiwangzhibujian/p/7053840.html)
## 标注
- <span id="to-bsd">[1] BSD开源协议：使用者可自由使用、修改源代码，也可将修改后的代码作为开源或者专有软件再发布。BSD鼓励代码共享，但要尊重代码作者的著作权。</span>

