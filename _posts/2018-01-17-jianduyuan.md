---
layout: post
title: 顺序表穷尽式搜索算法之监督元
date: 2018-01-17
categories: 算法
tags: [算法]
---

* content
{:toc}

### 顺序表
顺序表是以数组形式存储在计算机内存空间的线性表，是存储在连续的存储单元当中的。那么如果有以下一串数字，我们要查询某一个数字时，应该怎么做呢？
```bash
[5, 2, 7, 8, 9, 20, 19]
```
最简单的方法是一端逐个搜索到末尾，查找对应的位置，也就是“穷尽式搜索算法”（本文只针对穷尽式搜索算法做阐述）。代码如下（PHP）：
```php
$array = [5, 2, 7, 8, 9, 20, 19];
function search($array, $number)
{
    $total = count($array);
    for($i = 0; $i < $total; $i++) {
        if($array[$i] == $number) {
            return $i;
        }
    }
}
echo search($array, 8);
```
在以上代码中得知，每次循环，我们做了两次判断：`$i < $total`和`$array[$i] == $number`，能不能简化为1个呢？这就要引入监督元技术了。

### 监督元
监督元，顾名思义，是起到监督作用的元素。为了避免上文中提到的`$i < $total`判断，我们可以增加一个监督作用的元素放到数组的首端，设置为要搜索的元素值，当遍历到监督元素还没找到被搜索的值时，代表数组内没有该元素。例如：
```php
$array = [5, 2, 7, 8, 9, 20, 19];
function search($array, $number)
{
    $i = count($array);
    array_unshift($array, $number);
    while($array[$i] != $number) {
        $i--;
    }
    return $i;
}
echo search($array, 8);
```
从以上代码中看出，逻辑中去掉了一次判断，整体的查询时间翻了一倍。