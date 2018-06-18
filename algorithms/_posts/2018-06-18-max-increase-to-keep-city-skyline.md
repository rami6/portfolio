---
layout: algorithm
title: Max Increase to Keep City Skyline
tags: 
    - Python
description: 
    - In a 2 dimensional array `grid`, each value `grid[i][j]` represents the height of a building located there. We are allowed to increase the height of any number of buildings, by any amount (the amounts can be different for different buildings). Height 0 is considered to be a building as well. 
    - At the end, the "skyline" when viewed from all four directions of the grid, i.e. top, bottom, left, and right, must be the same as the skyline of the original grid. A city's skyline is the outer contour of the rectangles formed by all the buildings when viewed from a distance. See the following example.

    - What is the maximum total sum that the height of the buildings can be increased?
example: 
    - input: grid = [[3,0,8,4],[2,4,5,7],[9,2,6,3],[0,3,1,0]]
      output: 35
      explanation: "<br/>The grid is:<br/>
[ [3, 0, 8, 4],<br/>
  [2, 4, 5, 7],<br/>
  [9, 2, 6, 3],<br/>
  [0, 3, 1, 0] ]<br/>

The skyline viewed from top or bottom is: [9, 4, 8, 7]<br/>
The skyline viewed from left or right is: [8, 7, 9, 3]<br/>

The grid after increasing the height of buildings without affecting skylines is:<br/>

gridNew = <br/>
[ [8, 4, 8, 7],<br/>
[7, 4, 7, 7],<br/>
[9, 4, 8, 7],<br/>
[3, 3, 3, 3] ]"
note: 
    - "`1 < grid.length = grid[0].length <= 50`."
    - All heights `grid[i][j]` are in the range `[0, 100]`.
    - "All buildings in `grid[i][j]` occupy the entire grid cell: that is, they are a `1 x 1 x grid[i][j]` rectangular prism."
link: Max Increase to Keep City Skyline - LeetCode
link_url: https://leetcode.com/problems/max-increase-to-keep-city-skyline/description/
---

I've mostly solved easy level problems, but I found out that I should challenge to medium level problems. Solving problems without researching does not help my skills to grow.<br/>
So, I will solve medium or the above level problems from now on.

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 56 ms, beats 78.09 % of python3 submissions.
{% highlight python %}
class Solution:
    def maxIncreaseKeepingSkyline(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        
        skyline_tb = []
        max_total = 0
        
        for i in range(len(grid)):
            max_num = 0
            for arr in grid:
                max_num = max(max_num, arr[i])
            skyline_tb.append(max_num)
        
        for arr in grid:
            max_num = 0
            for num in arr:
                max_num = max(max_num, num)
            for i in range(len(arr)):
                max_total += min(skyline_tb[i], max_num) - arr[i]
        
        return max_total
{% endhighlight %}