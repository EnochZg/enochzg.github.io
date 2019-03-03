---
layout: post
title: 删除排序链表中的重复元素
date: 2018-01-18
categories: 算法
tags: [算法]
---

* content
{:toc}

### 问题
给定一个排序链表，删除所有重复的元素每个元素只留下一个。

### 样例
给出 1->1->2->null，返回 1->2->null
给出 1->1->2->3->3->null，返回 1->2->3->null

### 分析
本来没有看清楚题目中的`排序链表`，导致走向了一个误区：用列表记录已经存在的数值，每次遍历都要判断列表中的数是否存在，导致效率非常的低。
其实本题是一个比较简单的遍历链表的算法，由于是排序链表，相同的数值都在一起，只需要遍历链表时检查当前结点的值是否与下一个结点的值相同，如果相同则将当前结点的next指向下一个结点的next即可。

### Python代码
```python
class ListNode(object):
    def __init__(self, val, next=None):
        self.val = val
        self.next = next

class Solution:
    """
    @param: head: head is the head of the linked list
    @return: head of linked list
    """
    def deleteDuplicates(self, head):
        if head == None:
            return head
        cur = head
        while cur.next != None:
            if cur.next.val == cur.val:
                cur.next = cur.next.next
                continue
            if cur.next != None:
                cur = cur.next
        return head

e = ListNode(3)
d = ListNode(3, e)
c = ListNode(2, d)
b = ListNode(1, c)
a = ListNode(1, b)
s = Solution()
head = s.deleteDuplicates(a)
while head != None:
    print(head.val)
    head = head.next
```