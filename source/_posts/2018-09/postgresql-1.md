---
title: PostgreSQL学习笔记（一）——PostgreSQL介绍
date: 2018-09-25 22:40:55
tags: [PostgreSQL,数据库]
categories: [PostgreSQL]
---
## PostgreSQL介绍
PostgreSQL是一个开源对象关系数据库管理系统（ORDBMS）；用于安全地存储数据；支持最佳做法，并允许在处理请求时检索它们。PostgreSQL是跨平台的，可以在许多操作系统上运行。
## PostgreSQL特点：
- 可在所有主要操作系统上运行；
- PostgreSQL支持文本、图像、声音和视频，并包括用于C/C++,Java,Python,Ruby和开发数据库链接(ODBC)的编程接口。
- PostgreSQL支持SQL的许多功能，例如复杂SQL查询，SQL子选择，外键，触发器，视图，事务，多进程并发控制（MVCC），流式复制，热备。
- 在PostgreSQL中，表可以设置为从“父”表继承其特性
- 可以安装多个扩展以向PostgreSQL添加附加功能。

## PostgreSQL数据类型
> ***数据类型*** 指定要在表字段中存储哪种类型的数据。在创建表时，对于每列必须使用数据类型。
三种主要的数据类型：
- 数值
- 字符串
- 日期/时间 

### 数值数据类型
数字数据类型用于指定表中的数字数据。

| 名称 | 描述 | 存储大小 |
| ------ | ------ | ------ |
| smallint | 存储整数，小范围 | 2字节 |
| integer | 存储整数，使用这个类型可存储典型的整数 | 4字节 |
| bigint | 存储整数，大范围 | 8字节 |
| decimal | 用户指定的精度，精确 | 变量 |
| numeric | 用户指定的精度，精确 | 变量 |
| real | 可变精度，不精确 | 4字节 |
| double | 可变精度，不精确 | 8字节 |
| serial | 自动递增整数 | 4字节 |
| bigserial | 达到自动递增整数 | 8字节 |

<!-- more -->
### 字符串数据类型
String数据类型用于标识字符串类型值。

| 数据类型 | 描述 |
| ------ | ------ |
| char(size) | size：要存储的字符数。固定长度字符串，右边的空格填充到相等大小的字符 |
| character(size) | size：要存储的字符数。固定长度字符串，右边的空格填充到相等大小的字符 |
| varchar(size) | size：要存储的字符数。可变长度字符串。 |
| character varying(size) | size：要存储的字符数。可变长度字符串。 |
| text | 可变长度字符串。 |
|  |  |