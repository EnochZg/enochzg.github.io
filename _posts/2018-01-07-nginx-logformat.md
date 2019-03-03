---
layout: post
title: Nginx配置文件中log_format参数
date: 2018-01-07
categories: nginx
tags: [nginx, log_format]
---

* content
{:toc}

### 简介
Nginx中的log_format是用于格式化Nginx接收到的请求日志的，还有一条access_log与log_format相辅相成，前者用于格式化日志内容，后者决定日志的存放位置。

### 默认参数
```bash
'$remote_addr – $remote_user [$time_local] "$request" '
'$status $body_bytes_sent "$http_referer" '
'"$http_user_agent" "$http_x_forwarded_for"';
```

### 参数说明

| 参数        | 说明    |  示例  |
| --------   | -----:   | :----: |
| $remote_addr	        	| 客户端地址									| 219.227.111.255
| $remote_user	        	| 客户端用户名称								| —
| $time_local	        	| 访问时间和时区								| 18/Jul/2014:17:00:01 +0800
| $request	            	| 请求的URI和HTTP协议							| GET /article-10000.html HTTP/1.1
| $http_host	        	| 请求地址，即浏览器中你输入的地址（IP或域名）	| www.baidu.com  198.98.120.87
| $status	            	| HTTP请求状态									| 200
| $upstream_status	    	| upstream状态									| 200
| $body_bytes_sent	    	| 发送给客户端文件内容大小						| 124
| $http_referer	url     	| 跳转来源										| https://www.baidu.com
| $http_user_agent	    	| 用户终端浏览器等信息							| Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.0; Trident/4.0; SV1; GTB7.0; .NET4.0C;
| $ssl_protocol	 			| SSL协议版本									| TLSv1
| $ssl_cipher				| 交换数据中的算法								| RC4-SHA
| $upstream_addr			| 后台upstream的地址，即真正提供服务的主机地址	| 100.26.10.80:80
| $request_time				| 整个请求的总时间								| 0.2
| $upstream_response_time	| 请求过程中，upstream响应时间					| 0.5