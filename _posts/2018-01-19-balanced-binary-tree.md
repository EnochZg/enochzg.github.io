---
layout: post
title: 平衡二叉树
date: 2018-01-19
categories: 算法
tags: [算法]
---

* content
{:toc}

### 问题
给定一个二叉树,确定它是高度平衡的。对于这个问题,一棵高度平衡的二叉树的定义是：一棵二叉树中每个节点的两个子树的深度相差不会超过1。 

### 样例
给出二叉树 A={3,9,20,#,#,15,7}, B={3,#,20,15,7}

### 分析
首先，根据定义，如果分析树是否平衡，需要知道树左右子树的高度，又由于树层次不确定，所以需要使用到递归。又因为递归是从最后一层逐步向上返回的，所以我们需要从底向上返回层数及是否平衡。针对最后一层进行编码，平衡由左子树高度和右子树高度差的绝对值确定，层数为最高的子树加1。因为最小的子树是None，所以当结点为None时直接返回平衡、层数为1。

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
    @param: root: The root of binary tree.
    @return: True if this Binary tree is Balanced, or false.
    """
    def isBalanced(self, root):
        balanced, level = self.validate(root)
        return balanced

    def validate(self, root):
        if root == None: return True, 0
        balanced, leftHeight = self.validate(root.left)
        if not balanced:
            return False, 0
        balanced, rightHeight = self.validate(root.right)
        if not balanced:
            return False, 0
        return abs(rightHeight - leftHeight) <= 1, max(rightHeight, leftHeight) + 1
```