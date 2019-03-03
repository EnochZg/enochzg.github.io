---
layout: post
title: 二叉树的前序遍历
date: 2017-09-28
categories: lintcode
tags: [算法]
---

* content
{:toc}

### 问题
给出一棵二叉树，返回其节点值的前序遍历。

### 样例
给出一棵二叉树 {1,#,2,3}，返回[1,2,3]。

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
    @param: root: A Tree
    @return: Preorder in ArrayList which contains node values.
    """
    def preorderTraversal(self, root):
        # write your code here
        list = []
        return self.depth(root, list)

    def depth(self, root, list):
        if root == None: return []
        list.append(root.val)
        self.depth(root.left, list)
        self.depth(root.right, list)
        return list
```