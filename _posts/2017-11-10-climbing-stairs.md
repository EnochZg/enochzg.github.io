---
layout: post
title: 爬楼梯
date: 2017-11-10
categories: 算法
tags: [算法]
---

* content
{:toc}

### 问题
假设你正在爬楼梯，需要n步你才能到达顶部。但每次你只能爬一步或者两步，你能有多少种不同的方法爬到楼顶部？

### 样例
比如n=3，1+1+1=1+2=2+1=3，共有3种不同的方法，返回 3

### Python代码
```python
class Solution:
    """
    @param n: An integer
    @return: An integer
    """
    def climbStairs(self, n):
        # write your code here
        if n == 0: return 0
        if n == 1: return 1
        if n == 2: return 2
        
        tmpList = [1, 2]
        for i in range(2, n):
            tmpList.append(tmpList[i-1] + tmpList[i-2])
        return tmpList[n-1]

```