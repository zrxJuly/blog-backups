---
title: Docker系列（一）——学习Docker的技巧/线路
date: 2020-04-14 10:22:55
tags: [Docker]
categories: Docker
---

## Docker概念
### 是什么？
Docker是一个开源的应用容器引擎，基于Go语言并遵从Apache2.0协议开源。

### 做什么？

### 怎么做？

## 学习Docker前需要了解的概念知识

## Docker学习线路

1、虚拟化？
虚拟化和容器化之间的区别，如何用容器解决虚拟化问题？

2、学习Docker命令行
先学会使用Docker基本命令，再使用GUI工具。就好比Git，先学会了git命令，再使用类似SourceTree的工具。

Docker的GUI：Kubernetes、Docker Swarm、Docker Compose. etc.

首先学习Docker基础知识，然后转到Docker Compose和Docker Machine

K8s集群???

3、Docker网络
了解容器网络
如何创建Docker集群并使用编排系统？

什么是顶层可写层？

镜像和容器的区别？

CoW策略？

如何在Docker镜像和容器中存储和管理数据？

4、容器编排
业务流程。
容器编排允许从事物（容器）转移到抽象（服务），允许简化和优化部署。

刚入步，你可以使用Docker Swarm，然后转移到更复杂的系统，如K8S

5、尝试基于Docker做开发

尝试用Docker API开发东西。
使用Docker对并行计算集群进行原型设计
使用Docker对无服务系统进行原型设计
了解如何使用Docker API，编写orchestrator原型或自我修复系统。


Docker特征

灵活：即使最复杂的应用也可以被集装箱化；
轻量：CPU/内存低耗；比虚拟机效率更高；
便捷：本地构建，部署到云，运行在任何地方；
低耦合：容器替换或更新时不会干扰到其他
可扩展：可通过数据中心增加并自动分发容器副本；
安全：速度快，优雅的隔离框架

CPU/内存低耗；
快速开/关机；
跨云计算基础架构；

Docker组件与元素
组件：
* Docker Client 是用户界面，它支持用户与Docker Daemon之间通信。
* Docker Daemon运行于主机上，处理服务请求。
* Docker Index是中央registry，支持拥有公有与私有访问权限的Docker容器镜像的备份。

基本要素：
* Docker Containers负责应用程序的运行，包括操作系统、用户添加的文件以及元数据。
* Docker Images是一个只读模板，用来运行Docker容器。
* DockerFile是文件指令集，用来说明如何自动创建Docker镜像。

Docker使用以下操作系统的功能来提高容器技术效率：
* Namespaces 充当隔离的第一级。确保一个容器中运行一个进程而且不能看到或影响容器外的其它进程。
* Control Groups是LXC的重要组成部分，具有资源核算与限制的关键功能。
* UnionFS（文件系统）作为容器的构建块。为了支持Docker的轻量级以及速度快的特性，它创建了用户层。


参考资料：
- Docker学习线路：
https://www.cnblogs.com/zhizihuakai/p/11518897.html
http://dockone.io/question/915

- Docker入门教程：http://dockone.io/article/101

- 菜鸟教程：https://www.runoob.com/docker/docker-tutorial.html
