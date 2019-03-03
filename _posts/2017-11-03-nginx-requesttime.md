---
layout: post
title: Nginx中request_time与upstream_response_time区别
date: 2017-11-03
categories: nginx
tags: [request_time, upstream_response_time]
---

* content
{:toc}

### request_time
> request processing time in seconds with a milliseconds resolution; time elapsed between the first bytes were read from the client and the log write after the last bytes were sent to the client 。

指的就是从接受用户请求的第一个字节到发送完响应数据的时间，即包括接收请求数据时间、程序响应时间、输出响应数据时间。

### upstream_reponse_time
> keeps times of responses obtained from upstream servers; times are kept in seconds with a milliseconds resolution. Several response times are separated by commas and colons like addresses in the $upstream_addr variable

是指从Nginx向后端（php-cgi)建立连接开始到接受完数据然后关闭连接为止的时间。