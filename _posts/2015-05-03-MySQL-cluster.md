---
layout: post
title: MySQL分布式集群部署方案
date: 2015-05-03
categories: 数据库
tags: [mysql, cluster]
---

* content
{:toc}

![image](http://www.2cto.com/uploadfile/Collfiles/20170818/20170818103343279.jpg)

#### MyCAT

开源分布式数据库中间件，负责将后端的数据库进行分库分表、负载均衡、读写分离，对用户来说是透明的。

#### Haproxy

提供高可用、负载均衡以及基于TCP、HTTP的应用代理。可以保证MyCAT的高可用，它本身存在单点问题，可以采用keepalived的方式保证它的高可用。

#### keepalived

基于VRRP协议，VRRP协议是虚拟路由器冗余协议，它将多个相同功能的路由器组成一个群组，群组中分为主、备两种角色，主会不间断的发送广播消息给所有的备，当备有一段时间没有接收到主发来的消息时，就会自动选举出一个主路由器。