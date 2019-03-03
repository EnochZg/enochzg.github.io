---
layout: post
title: Git如何同时发布到多个远程仓库
date: 2018-07-21
categories: 工具技巧
tags: [git, 远程仓库] 
---

* content
{:toc}

> 用github pages写博客很久了，一直没有考虑过网站SEO，这两天了解到百度搜索引擎是搜不到github pages的，因为github禁用了baidu spider。于是便找了一家国内的类github平台--coding，准备两家平台同时发布博客，那怎么样才能用git同时推送两个仓库呢？其实很简单，两条命令即可搞定。

### 添加Git远程仓库
```bash
git remote set-url --add --push origin git@github.com:EnochZg/enochzg.github.io.git
```

### 查看当前远程仓库
```bash
git remote -v

origin	git@github.com:EnochZg/enochzg.github.io.git (fetch)
origin	git@git.coding.net:EnochZg/EnochZg.git (push)
```
本来以为已经有一条了，再添加一条就够了，结果发现原有仓库被覆盖了，下面再将原仓库地址追加进去。

```bash
git remote set-url --add --push origin git@git.coding.net:EnochZg/EnochZg.git
```

再查看一下，已经有了两个push类型的仓库了。
```bash
git remote -v

origin	git@github.com:EnochZg/enochzg.github.io.git (fetch)
origin	git@git.coding.net:EnochZg/EnochZg.git (push)
origin	git@github.com:EnochZg/enochzg.github.io.git (push)
```

### 测试
目前已经添加完成，我们来推送测试一下
```bash
git push origin master

Counting objects: 4, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 1.42 KiB | 0 bytes/s, done.
Total 4 (delta 2), reused 0 (delta 0)
To git.coding.net:EnochZg/EnochZg.git
   61bcd7f..e0a26aa  master -> master
Counting objects: 4, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 1.42 KiB | 0 bytes/s, done.
Total 4 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To github.com:EnochZg/enochzg.github.io.git
   61bcd7f..e0a26aa  master -> master

```
可以看出来，我们的文件已经成功推送到了两个仓库。

### 命令
我们来回顾一下，其实非常简单，一共只有两条命令
```bash
# 添加推送仓库的命令
git remote set-url --add --push [name] [address]

#查看当前仓库的命令
git remote -v
```
