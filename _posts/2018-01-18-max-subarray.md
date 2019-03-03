---
layout: post
title: 最大子数组问题
date: 2018-01-18
categories: 算法
tags: [算法]
---

* content
{:toc}

### 问题
给定一个整数数组，找到一个具有最大和的子数组，返回其最大和。

### 样例
给出数组[−2,2,−3,4,−1,2,1,−5,3]，符合要求的子数组为[4,−1,2,1]，其最大和为6

### 分析
贪心算法，就像捡水果遇到好的拼命往包里塞并和包里的水果进行比较，把不太好的给扔掉。如题，从第一个元素逐个遍历相加，并记录最大的相加结果，相加结果小于0的直接抛弃，从下一个元素开始重新相加，相加结果大于最大值的就赋值给最大值，从而选出最大的和。

### Python代码示例
```python
class Solution:
    """
    @param: nums: A list of integers
    @return: A integer indicate the sum of max subarray
    """
    def maxSubArray(self, nums):
        total = 0
        max = nums[0]
        for number in nums:
            total += number
            if total > max:
                print(total)
                max = total
            if total < 0:
                total = 0
        return max

solution = Solution()
solution.maxSubArray([-2,2,-3,4,-1,2,1,-5,3])
```