---
title: 使用Jasypt对SpringBoot配置文件加密
date: 2018-12-20 11:17:57
tags: [Jasypt]
categories: [SpringBoot]
---
### 一、Jasypt介绍
&emsp;&emsp;Jasypt(Java Simplified Encryption)，为开发人员提供一种简单的方式来为项目增加加密功能，包括：密码Digest认证，文本和对象加密，集成hibernate、Spring Security来增强密码管理。Jasypt1.4新特性：加密属性文件、Spring Framework集成、加密Hibernate数据源配置、新的命令行工具、URL加密的Apache wicket集成、升级文档。
### 二、Jasypt作用
1.加密任务与应用程序。例如：加密密码、敏感信息和数据通信、创建完整检查数据的sums。
2.包括高安全性、基于标准的加密技术、可同时单向和双向加密的加密密码、文本、数字和二进制文件。
3.符合RSA标准的基于密码的加密，并提供了无配置加密工具以及新的、高可配置标准的加密工具。
4.加密属性文件（encryptable properties files）、Spring work集成、加密Hibernate数据源配置、新的命令行工具、URL加密的Apache wicket集成以及升级文档。
### 三、使用Jasypt对SpringBoot配置文件加密
#### 1.pom.xml中引入依赖
```xml
<!-- jasypt加密依赖 -->
<dependency>
	<groupId>com.github.ulisesbocchio</groupId>
	<artifactId>jasypt-spring-boot-starter</artifactId>
	<version>1.16</version>
</dependency>
```

#### 2.application.yml配置文件中配置加密所需的salt(盐)
```yml
# jasypt用于数据库url及密码加密.
jasypt:
  encryptor:
    password: zrxJuly
```
<!-- more -->
#### 3.加密
这里给配置文件中的链接数据库的用户名及密码加密。新建一个工具类JasyptUtil，main方法中加密代码示例如下：
```java
public static void main(String[] args) {
    BasicTextEncryptor textEncryptor = new BasicTextEncryptor();
    //1.加密所需的salt(盐)，此处的值要与application中的配置的password一样。 application.yml中配置：jasypt.encryptor.password=zrxJuly
    textEncryptor.setPassword("zrxJuly");
    //2.要加密的数据.运行完main方法后，将打印出的加密内容在application.yml相关参数中替换：
    String user = textEncryptor.encrypt("postgres");
    String password = textEncryptor.encrypt("zrx");
    // application.yml中替换：ENC(jdbcUrl)   ENC(password)
    System.out.println("user:"+user);
    System.out.println("password:"+password);
}
```
运行main方法，结果如下：
```yml
user:leMoA9uT7nBUbd/oNSzl+tzbjBRyeRGk
password:jLKpSiNXZ0EQKnryRhMgVg==
```
将配置文件application.yml中的数据库的用户名及密码替换为上述结果。加密字符串要在ENC()中。
```yml
user: ENC(leMoA9uT7nBUbd/oNSzl+tzbjBRyeRGk)
password: ENC(jLKpSiNXZ0EQKnryRhMgVg==)
```
运行项目，看数据库是否能连接上，若能正常链接，则加密成功。

