---
layout: post
title: 插入区间
date: 2016-05-15
categories: lintcode
tags: [算法]
---

* content
{:toc}

### 问题
```bash
给出一个无重叠的按照区间起始端点排序的区间列表。

在列表中插入一个新的区间，你要确保列表中的区间仍然有序且不重叠（如果有必要的话，可以合并区间）。
```

### 样例
插入区间[2, 5] 到 [[1,2], [5,9]]，我们得到 [[1,9]]。
插入区间[3, 4] 到 [[1,2], [5,9]]，我们得到 [[1,2], [3,4], [5,9]]。

### 分析
由题目得知几个关键要素：无重叠、排序的列表，合并区间。因为要求无重叠，所以我们需要判断怎样才是不重叠，第二个关键点是`排序的列表`，也就是说我们要插入的区间的左边大于其中区间的右边就是不重叠，同理，要插入区间的右边小于其中区间的左边也是不重叠。那么剩下的就是重叠的区间，怎么处理重叠的区间呢？这就牵扯到题目中的第三个要素`合并区间`，我们可以把两个区间的左边取最小值作为新区间的左边，并且把两个区间的右边取最大值作为新区间的右边，这样一个新的区间就诞生了。接下来，在遍历时，只需要记录需要插入区间的位置即可。

### Python代码
```python
"""
Definition of Interval.
class Interval(object):
    def __init__(self, start, end):
        self.start = start
        self.end = end
"""


class Solution:
    """
    @param: intervals: Sorted interval list.
    @param: newInterval: new interval.
    @return: A new interval list.
    """
    def insert(self, intervals, newInterval):
        # write your code here
        result = []
        insertPos = 0
        for n in intervals:
            if newInterval.end < n.start:
                result.append(n)
            elif newInterval.start > n.end:
                result.append(n)
                insertPos += 1
            else:
                newInterval.start = min(newInterval.start, n.start)
                newInterval.end = max(newInterval.end, n.end)
        result.insert(insertPos, newInterval)
        return result

```