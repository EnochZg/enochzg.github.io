---
layout: post
title: 把排序数组转换为高度最小的二叉搜索树
date: 2018-01-06
categories: 算法
tags: [算法]
---

* content
{:toc}

### 问题
给一个排序数组（从小到大），将其转换为一棵高度最小的排序二叉树。

### 样例
给出数组 [1,2,3,4,5,6,7], 返回
```bash
     4
   /   \
  2     6
 / \    / \
1   3  5   7
```

### 分析
由于二叉树满足根节点大于左儿子，小于又儿子，所以根据以上题目，可以将`[1,2,3,4,5,6,7]`从中间（以`4`）拆开一分为二`[1,2,3]`和`[5,6,7]`，然后左右部分分别以以上方式拆分，小的放左边，大的放右边。

### Python代码
```python
"""
Definition of TreeNode:
class TreeNode:
    def __init__(self, val):
        self.val = val
        self.left, self.right = None, None
"""


class Solution:
    """
    @param: A: an integer array
    @return: A tree node
    """
    def sortedArrayToBST(self, A):
        # write your code here
        return self.sort(A, 0, len(A) - 1)

    def sort(self, A, start, end):
        if start > end:
            return None
        if start == end:
            return TreeNode(A[start])
        mid = int((start + end) / 2)
        root = TreeNode(A[mid])
        root.left = self.sort(A, start, mid - 1)
        root.right = self.sort(A, mid + 1, end)
        return root

```