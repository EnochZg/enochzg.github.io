---
layout: post
title: 'Github pages如何被百度收录'
subtitle: '在博客园挣扎了很久又想搬回来了，但是github屏蔽了百度的收录，写的博客百度搜不到很没成就感，找了很多方法，发现还是在coding上同步博客最合适，接下来记录一下同步的方法。'
date: 2019-03-06
categories: 技术
cover: ''
tags: github pages
---

* content
{:toc}

### 1、准备工作
- 购买一个域名
- 注册coding账号

### 2、创建项目
在`coding.net`创建一个项目，项目名称与自己的用户名一致，如图所示
![image](http://pn44pnogo.bkt.clouddn.com/blog/1551880842399.png)

### 3、初始化仓库
点击`代码 -> 分支管理`，以及右侧的的`快速初始化仓库`
![image](http://pn44pnogo.bkt.clouddn.com/blog/1551881507252.png)

### 4、开启Coding Pages
点击左侧菜单中的`代码 -> Pages服务`，点击右侧的`一键开启Coding Pages`
![image](http://pn44pnogo.bkt.clouddn.com/blog/1551881345775.png)

显示如下内容就代表成功了
![image](http://pn44pnogo.bkt.clouddn.com/blog/1551881626251.png)

### 5、配置远程仓库
#### 5.1、添加远程仓库
为了达到一键推送到两个平台，要先多配置一个远程仓库，仓库地址从刚才新建的项目的`代码浏览`中查找
```bash
git remote add coding https://git.dev.tencent.com/EnochZg/EnochZg.git
```
检查是否添加成功
```bash
git remote -v
```
显示如下两个仓库地址就代表成功了
```bash
coding https://git.dev.tencent.com/EnochZg/EnochZg.git (fetch)
coding	https://git.dev.tencent.com/EnochZg/EnochZg.git (push)
origin	git@github.com:EnochZg/enochzg.github.io.git (fetch)
origin	git@github.com:EnochZg/enochzg.github.io.git (push)
```
#### 5.2、推送代码到coding
先把coding仓库的主分支拉下来
```bash
git pull coding master --allow-unrelated-histories
```
这个时候可能会出现冲突，因为coding初始化的时候可能生成`README.MD`文件，而你的github项目也存在这个文件，打开冲突文件，保留需要的内容，然后执行以下指令
```bash
git add .
git commit -m "resolve conflict"
git push --all
```
### 6、域名解析
项目根目录下创建CNAME文件，写上自己的域名地址并提交
```bash
www.enochzg.cn
```
打开域名解析平台（我的是万网域名），进行如下配置，境内解析到coding，境外访问解析到github，这样国外网友就能通过google搜到github pages，而国内网友就能通过百度搜到coding pages了。

![image](http://pn44pnogo.bkt.clouddn.com/blog/1551883729912.png)

大功告成！