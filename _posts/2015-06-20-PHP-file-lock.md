---
layout: post
title: PHP解决多线程读取同一个文件问题
date: 2015-06-20
categories: php
tags: [PHP, 文件锁]
---

* content
{:toc}

```php
<?php
    $fp = fopen("/tmp/lock.txt","w+");
    if(flock($fp, LOCK_EX)){
        fwrite($fp,"Write something here\n");
        flock($fp, LOCK_UN);
    }else{
        echo "Couldn't lock the file !";
    }
    fclose($fp);
?>
```