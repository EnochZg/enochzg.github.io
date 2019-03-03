---
layout: post
title: postgresql导入sql文件
date: 2016-04-01
categories: 数据库
tags: [postgresql, import]
---

* content
{:toc}

```bash
psql -d 数据库名 -h ip地址 -p 数据库端口 -U 用户名 -f 文件地址
```

例如：

```bash
psql -d huoshi -h 192.168.1.2 -p 5432 -U postgres -f /tmp/backup.sql
```