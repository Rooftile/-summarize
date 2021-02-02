

[TOC]



# 操作系统

## 操作命令

1. **[操作系统命令总结](docs/operating-system/操作系统命令.md)**

## 系统调用

## 内存管理

## CPU管理

## Shell

1. **[shell脚本](docs/operating-system/shell脚本.md)**
2. **[常用功能Shell代码片段](docs/operating-system/常用功能Shell代码片段)**

# 计算机网络

## 网络协议

1. IP协议
2. UDP协议
3. TCP协议
4. Socket编程
5. HTTP协议
6. 流媒体协议
7. P2P协议
8. DNS
9. CDN

# 数据结构与算法

1. 基础数据与算法
2. 操作系统中数据结构与算法应用
3. Java容器中对常用数据结构的封装

# 编程语言

## Java

### 基础

1. **[Java 基础知识](docs/language/java/basis/Java基础知识.md)**
2. **[Java 基础知识疑难点/易错点](docs/language/java/basis/Java基础知识疑难点.md)**

**重要知识点详解：**

1. [枚举](docs/language/java/basis/用好Java中的枚举真的没有那么简单.md) 
2. [Java 常见关键字总结：final、static、this、super!](docs/language/java/basis/Java常见关键字总结.md)
3. [什么是反射机制?反射机制的应用场景有哪些?](docs/language/java/basis/反射机制.md)
4. [代理模式详解：静态代理+JDK/CGLIB 动态代理实战](docs/language/java/basis/代理模式详解.md)
5. [BIO,NIO,AIO 总结 ](docs/language/java/basis/BIO,NIO,AIO总结.md)

### 容器 

### 并发

### JVM

1. 内存模型
2. 常用分析工具

## C++

### 基础语法

### 设计模式

## Go

1. 基础语法
2. 异常处理
3. 日志

## Python

1. python基本语法
2. 常用第三方库
   1. numpy
   2. pandas常用第三方库

## Scala

1. 基础语法
2. Akka框架

# 工具框架

## 队列

### Kafka

1. 基本概念及原理
2. 安装
3. 使用
4. 常见问题

## 关系型数据库

### Mysql

1. 安装
2. 权限管理

### Oracle

1. 安装
2. 权限管理

## 缓存数据库

### Redis

1. 常用命令
2. 集群模式
3. 原理

## 数据一致性

### Zookeeper

1. 安装部署
2. 源码分析
3. 常用命令
4. Api

### Etcd

## 分布式数据存储

### HDFS

### Hive

### HBase

## OLAP

### Impala

1. impala使用

### Clickhouse

1. clickhouse使用
2. 基本架构

### Kudu

### Elasticsearch

### Oozie

## 数据计算

### Yarn

1. **[Yarn架构与原理](docs/language/java/basis/Java基础知识疑难点.md)**
2. **[Yarn核心部分源码分析](docs/language/java/basis/Java基础知识疑难点.md)**

### Spark

### Flink

## CDH/CDP

### 集群搭建

1. CDH集群搭建
2. CDH扩容
3. CDP集群搭建

### API

1. CDH rest api
2. CDH java api

### 第三方服务集成

1. parcels 打包

## 监控

### prometheus

1. prometheus基本概念及原理
2. prometheus使用

https://www.prometheus.wang/quickstart/why-monitor.html

# 微服务

## kubeneties

## docker

## 服务拆分原则





```flow
st=>start: 开始

e=>end: 结束

op=>operation: 操作

sub=>subroutine: 子程序

cond=>condition: 是或者不是?

io=>inputoutput: 输出


st(right)->op->cond

cond(yes)->io(right)->e

cond(no)->sub(right)->op


```









