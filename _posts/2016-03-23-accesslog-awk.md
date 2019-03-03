---
layout: post
title: 查看access.log中前100个最频繁的页面
date: 2016-03-23
categories: 工具技巧
tags: [awk, access.log]
---

* content
{:toc}

```bash
cat access.log | awk '{print $7}' | sort | uniq -c | sort -rn | head -n 100
```