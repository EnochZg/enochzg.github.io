---
layout: post
title: Socket在PHP中的使用
date: 2015-10-13
categories: php
tags: [Socket]
---

* content
{:toc}

### 开启Socket

phpinfo()中可查看socket是否开启

### 服务端写法

```php
<?php
error_reporting(E_ALL);
set_time_limit(0);
//ob_implicit_flush();

$address = '127.0.0.1';
$port = 10005;
//创建端口
if( ($sock = socket_create(AF_INET, SOCK_STREAM, SOL_TCP)) === false) {
	echo "socket_create() failed :reason:" . socket_strerror(socket_last_error()) . "\n";
}

//绑定
if (socket_bind($sock, $address, $port) === false) {
	echo "socket_bind() failed :reason:" . socket_strerror(socket_last_error($sock)) . "\n";
}

//监听
if (socket_listen($sock, 5) === false) {
	echo "socket_bind() failed :reason:" . socket_strerror(socket_last_error($sock)) . "\n";
}

do {
	//得到一个链接
	if (($msgsock = socket_accept($sock)) === false) {
		echo "socket_accepty() failed :reason:".socket_strerror(socket_last_error($sock)) . "\n";
		break;
	}
	//welcome  发送到客户端
	$msg = "<font color='red'>server send:welcome</font><br/>";
	socket_write($msgsock, $msg, strlen($msg));
	echo 'read client message\n';
	$buf = socket_read($msgsock, 8192);
	$talkback = "received message:$buf\n";
	echo $talkback;
	if (false === socket_write($msgsock, $talkback, strlen($talkback))) {
		echo "socket_write() failed reason:" . socket_strerror(socket_last_error($sock)) ."\n";
	} else {
		echo 'send success';
	}
	socket_close($msgsock);
} while(true);

socket_close($sock);
```

### 客户端写法

```php
<?php
//error_reporting(E_ALL);
echo "<h2>tcp/ip connection </h2>\n";
$service_port = 10005;
$address = '127.0.0.1';

$socket = socket_create(AF_INET, SOCK_STREAM, SOL_TCP);
if ($socket === false) {
	echo "socket_create() failed: reason: " . socket_strerror(socket_last_error()) . "\n";
} else {
	echo "OK. \n";
}

echo "Attempting to connect to '$address' on port '$service_port'...";
$result = socket_connect($socket, $address, $service_port);
if($result === false) {
	echo "socket_connect() failed.\nReason: ($result) " . socket_strerror(socket_last_error($socket)) . "\n";
} else {
	echo "OK \n";
}
$in = "HEAD / http/1.1\r\n";
$in .= "HOST: localhost \r\n";
$in .= "Connection: close\r\n\r\n";
$out = "";
echo "sending http head request ...";
socket_write($socket, $in, strlen($in));
echo  "OK\n";

echo "Reading response:\n\n";
while ($out = socket_read($socket, 8192)) {
	echo $out;
}
echo "closeing socket..";
socket_close($socket);
echo "ok .\n\n";
```