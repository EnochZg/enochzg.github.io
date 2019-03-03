---
layout: post
title: 二叉树的层次遍历
date: 2017-11-17
categories: 算法
tags: [算法]
---

* content
{:toc}

### 问题
给出一棵二叉树，返回其节点值的层次遍历（逐层从左往右访问）

### 样例
给一棵二叉树 {3,9,20,#,#,15,7} ：
```bash
  3
 / \
9  20
  /  \
 15   7
```
返回他的分层遍历结果：
```python
[
  [3],
  [9,20],
  [15,7]
]
```

### 分析
因为我们要查出每一层的数据并记录，所以不能采用递归的方式。那不用递归怎么查出每层的结点呢？已知一个结点，我们可以查询出它的左右子结点，并将查出的结点追加到数组中，如果有多个结点，我们可以采用遍历的形式将每一个结点的左右子结点追加到数组中（顺便记录每个结点的值到result数组）。而这个数组可以作为下次遍历的基础数组。

### Python代码
```python
class Solution:
    """
    @param: root: A Tree
    @return: Level order a list of lists of integer
    """
    def levelOrder(self, root):
        results = []
        if not root:
            return results
        q = [root]
        while q:
            new_q = []
            results.append([n.val for n in q])
            for node in q:
                if node.left:
                    new_q.append(node.left)
                if node.right:
                    new_q.append(node.right)
            q = new_q
        return results
```