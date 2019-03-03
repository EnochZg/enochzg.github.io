---
layout: post
title: Postgresql修改默认密码
date: 2016-03-24
categories: 数据库
tags: [sql]
---

* content
{:toc}

### 登录默认数据库
```bash
sudo su postgres
pgsql
```

### 设置密码
```bash
postgres=# \password postgres
Enter new password: 
Enter it again: 
postgres=#
```