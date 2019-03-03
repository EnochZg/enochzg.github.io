---
layout: post
title: 合并排序数组 II
date: 2017-11-15
categories: 算法
tags: [算法]
---

* content
{:toc}

### 问题
合并两个排序的整数数组A和B变成一个新的数组。

### 样例
给出`A=[1,2,3,4]，B=[2,4,5,6]`，返回 `[1,2,2,3,4,4,5,6]`。

### 分析
由于两个数组都是排序数组，所以我们只需要将A和B中的数依次比较即可。比如，AB都拿出索引为1的数值进行比较，小的追加到空数组中，因为不确定小的下一个索引是否比大的那个值小，所以小的数组索引要加1，继续与大的进行比较，以此类推，将会把大部分的数字排好顺序。那假如有一个数组索引已经越界了怎么办呢？因为我们不知道哪个数组先遍历完了，所以我们可以继续单独遍历AB，将没遍历完的数字补全。

### Python代码
```python
class Solution:
    """
    @param: A: sorted integer array A
    @param: B: sorted integer array B
    @return: A new sorted integer array
    """
    def mergeSortedArray(self, A, B):
        # write your code here
        ans = []
        i, j = 0, 0
        n, m = len(A), len(B)
        while i < n and j < m:
            if A[i] < B[j]:
                ans.append(A[i])
                i += 1
            else:
                ans.append(B[j])
                j += 1
        while i < n:
            ans.append(A[i])
            i += 1
        while j < m:
            ans.append(B[j])
            j += 1
        return ans
```