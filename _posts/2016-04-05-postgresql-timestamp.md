---
layout: post
title: Postgresql将时间戳转换为字符串
date: 2016-04-05
categories: 数据库
tags: [postgresql, 时间戳]
---

* content
{:toc}

```sql
select to_char(to_timestamp(1462600292),'yyyy-MM-dd');
```