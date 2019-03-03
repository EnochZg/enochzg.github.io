---
layout: post
title: 岛屿的个数
date: 2018-01-19
categories: 算法
tags: [算法]
---

* content
{:toc}

### 问题
给一个01矩阵，求不同的岛屿的个数。
0代表海，1代表岛，如果两个1相邻，那么这两个1属于同一个岛。我们只考虑上下左右为相邻。

### 样例
```python
[
  [1, 1, 0, 0, 0],
  [0, 1, 0, 0, 1],
  [0, 0, 0, 1, 1],
  [0, 0, 0, 0, 0],
  [0, 0, 0, 0, 1]
]
```

### 分析
首先，我们遍历每一个结点，当该结点是岛屿的时候进行深度搜索，也就是递归查询横向以及纵向的结点是否也是岛屿，把所有的岛屿都打一个False的标记，以免其他结点会重复搜索。每次深度搜索结束就将岛屿的数值累加1，这样到最后就可以算出所有的岛屿的数量。

### Python代码
```python
class Solution:
    """
    @param: grid: a boolean 2D matrix
    @return: an integer
    """
    def numIslands(self, grid):
        # write your code here
        if len(grid) == 0:
            return 0
        h = len(grid)
        w = len(grid[0])
        count = 0
        for x in range(0, h):
            for y in range(0, w):
                if grid[x][y]:
                    count += 1
                    self.dfs(grid, x, y)
        return count

    def dfs(self, grid, x, y):
        if x < 0 or y < 0 or x >= len(grid) or y >= len(grid[0]) or grid[x][y]!=1:
            return
        grid[x][y] = False
        self.dfs(grid, x-1, y)
        self.dfs(grid, x+1, y)
        self.dfs(grid, x, y-1)
        self.dfs(grid, x, y+1)
```