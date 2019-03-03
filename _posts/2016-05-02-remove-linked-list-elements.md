---
layout: post
title: 删除链表中的元素
date: 2016-05-02
categories: lintcode
tags: [算法]
---

* content
{:toc}

### 问题
删除链表中等于给定值val的所有节点。

### 样例
给出链表 1->2->3->3->4->5->3, 和 val = 3, 你需要返回删除3之后的链表：1->2->4->5。

### Python代码示例
```python
"""
Definition for singly-linked list.
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None
"""


class Solution:
    """
    @param: head: a ListNode
    @param: val: An integer
    @return: a ListNode
    """
    def removeElements(self, head, val):
        if head == None:
            return head
        cur = ListNode(0, head)
        head = cur
        while cur.next != None:
            if cur.next.val == val:
                cur.next = cur.next.next
                continue
            else:
                cur = cur.next
        return head.next
```