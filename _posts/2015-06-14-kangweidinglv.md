---
layout: post
title: 康威定律
date: 2015-06-14
categories: 架构
tags: [康威定律]
---

* content
{:toc}

> Any organization that design a system (defined broadly) will produce a design whose structure is a copy of the organization's communication structure. – Melvin Conway, 1968

直译为中文的意思就是“设计系统的组织，最终所产生的设计等同于组织之内、之间的沟通结构”。直白的说，你想要什么样的系统，就搭建什么样的团队。如果你的系统是按照业务边界划分的，大家按照一个业务目标去把自己的模块做出小系统，小产品的话，你的大系统就会长成下面的样子，即微服务的架构：

而微服务的理念团队间应该是 inter-operate, not integrate。inter-operate是定义好系统的边界和接口，在一个团队内全栈，让团队自治，原因就是因为如果团队按照这样的方式组建，将沟通的成本维持在系统内部，每个子系统就会更加内聚，彼此的依赖耦合能变弱，跨系统的沟通成本也就能降低。

反过来想，如果一个团队的组织结构并没有按照康威定律进行微服务改造，就开始着手微服务开发，最终设计出来的系统会不会还是原来的套路？这是个问题。