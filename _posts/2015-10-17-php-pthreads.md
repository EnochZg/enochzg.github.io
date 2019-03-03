---
layout: post
title: PHP多线程的实现
date: 2015-10-17
categories: php
tags: [php, thread, pthreads]
---

* content
{:toc}

### 安装pthreads扩展

- 下载地址：https://github.com/krakjoe/pthreads
- 编译安装
```bash
unzip pthreads-master.zip
cd pthreads-master
phpize
./configure –with-php-config=/Data/apps/php/bin/php-config
make
make install
```
- 添加扩展到配置文件
```bash
vi /Data/apps/php/etc/php.ini
添加：
extension = "pthreads.so"
```

### 继承Thread类

以下是PHP脚本的写法：

```php
<?php
class My extends Thread{
    function run(){
        for($i=1;$i<10;$i++){
            echo Thread::getCurrentThreadId() .  "\n";
            sleep(2);     // <------
        }
    }
}

for($i=0;$i<2;$i++){
    $pool[] = new My(); 
}

foreach($pool as $worker){
    $worker->start();
}
foreach($pool as $worker){
    $worker->join();
}
?>
```

Output:

```bash
6300
5816
6300
5816
6300
5816
6300
5816
6300
5816
6300
5816
6300
5816
6300
5816
6300
5816
```