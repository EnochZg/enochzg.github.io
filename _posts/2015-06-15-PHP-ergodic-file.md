---
layout: post
title: PHP遍历文件夹
date: 2015-06-15
categories: php
tags: [PHP, 遍历]
---

* content
{:toc}

```php

function getdir($path)
{
    $dirs = scandir($path);
    foreach($dirs as $name) {
        if($name == '.' || $name == '..') {
            continue;
        }
        $realpath = sprintf("%s/%s", $path, $name);
        echo $realpath . "\n\n";
        getdir($realpath);
    }
}

getdir('/tmp/test');

```