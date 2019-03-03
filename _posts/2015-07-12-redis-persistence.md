---
layout: post
title: Redis持久化的方式
date: 2015-07-12
categories: 数据库
tags: [redis, persistence, 持久化]
---

* content
{:toc}

Redis有两种持久化的方法：AOF、RDB。

### RDB

通过快照的方式备份数据，定时把当前的数据全量的保存起来，故障发生时可以选择某个时间点进行恢复。

### AOF

以追加文件的方式进行备份，就是将每次对Redis数据库的操作行为记录下来，故障发生时，可以逐行执行记录下来的命令重建数据。两种备份方式可以同时开启，但是当Redis重启时会优先以AOF的方式重建数据。