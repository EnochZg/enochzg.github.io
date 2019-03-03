---
layout: post
title: Nginx负载均衡的5种算法
date: 2015-09-10
categories: nginx
tags: [nginx, 负载均衡]
---

* content
{:toc}

### 轮询

每一个请求按时间顺序逐一的请求不同服务器，如果服务器挂掉，可以自动剔除。

### Weight

指定某一个服务器的轮询概率，用于后端服务器性能不均匀的情况。

```bash
upstream bakend {  
	server 192.168.0.14 weight=10;  
	server 192.168.0.15 weight=10;  
}
```

### ip_hash

通过哈希用户请求的IP地址，将用户的请求转发到固定的服务器，这样可以解决Session的问题。

```bash
upstream bakend {  
	ip_hash;  
	server 192.168.0.14:88;  
	server 192.168.0.15:80;  
}  
```

### fair（第三方）

根据响应时间来分配请求，响应时间短的优先分配。

```bash
upstream backend {  
	server server1;  
	server server2;  
	fair;  
}  
```

### url_hash

根据url的哈希值分配请求。