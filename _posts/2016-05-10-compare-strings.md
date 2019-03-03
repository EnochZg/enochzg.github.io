---
layout: post
title: 比较字符串
date: 2016-05-10
categories: lintcode
tags: [算法]
---

* content
{:toc}

### 问题
比较两个字符串A和B，确定A中是否包含B中所有的字符。字符串A和B中的字符都是 大写字母。

### 样例
给出`A = "ABCD" B = "ACD"`，返回`true`
给出`A = "ABCD" B = "AABC"`， 返回`false`

### 分析
本题比较简单，可以遍历B逐个字符与A匹配，如果匹配的数量等于B字符的总数量，就断定AB相等。但是，这里会有个坑，就是如果B中有两个C，也会匹配成功，所以，每次匹配正确时，需要将A中对应的字母改为0或其他非字母字符，以免同一个字母重复匹配。

### Python代码
```python
class Solution:
    """
    @param: A: A string
    @param: B: A string
    @return: if string A contains all of the characters in B return true else return false
    """
    def compareStrings(self, A, B):
        # write your code here
        count = 0
        n, m = len(A), len(B)
        j = 0
        while j < m:
            strpos = A.find(B[j])
            if strpos != -1:
                count += 1
                A = A[:strpos] + '0' + A[strpos+1:]
            j += 1
        if count == m:
            return True
        else:
            return False
```