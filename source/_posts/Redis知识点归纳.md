---
title: Redis知识点归纳
date: 2018-07-18 23:39:50
tags: redis
---
### 支持数据类型
1. String
1. List
1. Hash
1. Set
1. Sort Set

### Redis 与 Memcached 区别于对比
1. Redis 支持更多的数据类型 Memcached 只支持key-value
1. Redis 支持数据持久化 ，Memcached 不支持
1. Redis 速度比Memcached快
1. Redis 支持单条数据容量达到1G，Memcached只支持1M
1. Redis与Memcached都限制于物理内存大小，只适合做数据量较小的高性能操作与运算
1. Memcached可以通过HASH一致性实现分布式
1. Redis 支持事物，操作都是原子性（对数据操作要么全部执行，要么全部不执行）
1. 两者都可以设置过期时间，适合做缓存服务
1. Redis支持主从复制

### Redis是单进程单线程的
redis利用队列技术将并发访问变为串行访问，消除了传统数据库串行控制的开销

### Redis并发竞争问题
1. Redis 并没有锁的概念，多个客户端之间并不存在竞争。
1. 客户端对Redis访问时会发生连接超时、数据转换错误、阻塞、客户端关闭连接等问题，这些问题都是因为客户端连接混乱引起的。

### Redis数据持久化
1. 快照
1. AOF
1. 虚拟内存

### Redis适合的使用场景
1. 会话缓存
1. 页面缓存
1. 队列
1. 排行榜，计数器
1. 发布订阅
