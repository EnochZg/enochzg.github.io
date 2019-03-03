---
layout: post
title: 两人拿石头判断输赢问题
date: 2017-11-07
categories: php
tags: [拿石头]
---

* content
{:toc}

### 问题
桌面上有一堆石头，你和一个朋友轮流拿石头，谁最后把石头拿完谁赢。规则：你先拿，只能拿1-3个。（举例：一共四个石头，无论你先拿多少个，都会是朋友最后一个拿完。）请写出一个函数来判断某个数量的石头是否有赢的可能性。

### 代码示例
```php
function get($surplus, $player, $take_number)
{
    $surplus -= $take_number;
    $player = $player ? 0 : 1;
    if($surplus == 4)
        return $player ? true : false;
    if($surplus < 4)
        return $player ? false : true;

    if($player == 0) {
        if(get($surplus, $player, 1) || get($surplus, $player, 2) || get($surplus, $player, 3))
            return true;
    }else {
        if(get($surplus, $player, 1) && get($surplus, $player, 2) && get($surplus, $player, 3))
            return true;
    }
}

$surplus = 4;
$player = 0;
if(get($surplus, $player, 1) || get($surplus, $player, 2) || get($surplus, $player, 3)) {
    echo 'win!';
}else {
    echo 'defeat!';
}
```