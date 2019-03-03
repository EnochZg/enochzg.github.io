---
layout: post
title: 斐波纳契数列
date: 2017-11-09
categories: lintcode
tags: [算法]
---

* content
{:toc}

### 问题
查找斐波纳契数列中第 N 个数。

所谓的斐波纳契数列是指：
前2个数是 0 和 1 。
第 i 个数是第 i-1 个数和第i-2 个数的和。
斐波纳契数列的前10个数字是：
```0, 1, 1, 2, 3, 5, 8, 13, 21, 34 ...```

### 样例
```bash
给定 1，返回 0

给定 2，返回 1

给定 10，返回 34
```

### Python代码
```python
class Solution:
    """
    @param: n: an integer
    @return: an ineger f(n)
    """
    def fibonacci(self, n):
        # write your code here
        if n == 1:
            return 0
        if n == 2:
            return 1
        n += 1
        a = 0
        b = 1
        for i in range (3, n):
            tmp = b
            b = a + b
            a = tmp
        return b
```