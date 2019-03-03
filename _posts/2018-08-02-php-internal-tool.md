---
layout: post
title: 跟厂长学PHP7内核（二）：源码分析工具之GDB
date: 2018-08-02
categories: PHP内核
tags: [php, internal, 工具]
---

* content
{:toc}

### 源码下载地址
```
http://php.net/distributions/php-7.0.12.tar.gz
```

### 安装PHP
```bash
$ wget http://php.net/distributions/php-7.0.12.tar.gz
$ tar zxvf php-7.0.12.tar.gz
$ cd php-7.0.12/
$ ./configure --prefix=/usr/local/php7 --enable-debug --enable-fpm
$ make && make install
```

### 安装调试工具GDB
```bash
$ sudo apt install gdb
```

### 问题处理
- no acceptable C compiler found
```bash
$ sudo apt-get install build-essential
```

- configure: error: xml2-config not found
```bash
$ sudo apt-get install libxml2-dev
```

### 调试

- 创建php文件
```php
<?php
    echo "Hello world!";
?>
```

- 打开gdb

```
$ gdb php //将显示如下内容

GNU gdb (Debian 7.12-6) 7.12.0.20161007-git
Copyright (C) 2016 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
<http://www.gnu.org/software/gdb/documentation/>.
For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from php...done.
(gdb) 
```

- 调试创建的php文件

```
//断点main函数
(gdb) b main
(gdb) run index.php

Starting program: /usr/local/bin/php index.php
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".

Breakpoint 1, main (argc=2, argv=0x7fffffffcd48) at /home/enoch/Source/php-7.0.12/sapi/cli/php_cli.c:1172
1172		int exit_status = SUCCESS;

//next执行下一行
(gdb) next
1173		int module_started = 0, sapi_started = 0;
(gdb) next
1174		char *php_optarg = NULL;
(gdb) next
1175		int php_optind = 1, use_extended_info = 0;
(gdb) next
1176		char *ini_path_override = NULL;

//print可以打印变量、表达式
(gdb) print php_optarg
$1 = 0x0
```

关于GDB的具体指令，可以参考官方文档，这里不再一一赘述。

### Docker如何GDB调试

```
docker run --security-opt seccomp=unconfined -it ubuntu bash
```
