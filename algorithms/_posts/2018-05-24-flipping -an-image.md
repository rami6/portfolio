---
layout: algorithm
title: Flipping an Image
tags: 
    - Python
description: 
    - "Given a binary matrix `A`, we want to flip the image horizontally, then invert it, and return the resulting image."
    - "To flip an image horizontally means that each row of the image is reversed.  For example, flipping `[1, 1, 0]` horizontally results in `[0, 1, 1]`."
    - "To invert an image means that each `0` is replaced by `1`, and each `1` is replaced by `0`. For example, inverting `[0, 1, 1]` results in `[1, 0, 0]`."
example:
    - input: [[1,1,0],[1,0,1],[0,0,0]]
      output: [[1,0,0],[0,1,0],[1,1,1]]
      explanation: "First reverse each row: [[0,1,1],[1,0,1],[0,0,0]]. Then, invert the image: [[1,0,0],[0,1,0],[1,1,1]]"
    - input: [[1,1,0,0],[1,0,0,1],[0,1,1,1],[1,0,1,0]]
      output: [[1,1,0,0],[0,1,1,0],[0,0,0,1],[1,0,1,0]]
      explanation: "First reverse each row: [[0,0,1,1],[1,0,0,1],[1,1,1,0],[0,1,0,1]]."
Then invert the image: [[1,1,0,0],[0,1,1,0],[0,0,0,1],[1,0,1,0]]
note:
    - "`1 <= A.length = A[0].length <= 20`"
    - "`0 <= A[i][j] <= 1`"
link: Flipping an Image - LeetCode
link_url: https://leetcode.com/problems/flipping-an-image/description/
---

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 48 ms, runtime distribution didn't be shown because of less data.
{% highlight python %}
class Solution:
    def flipAndInvertImage(self, A):
        """
        :type A: List[List[int]]
        :rtype: List[List[int]]
        """
        output = []
        for arr_item in A:
            output.append(arr_item[::-1])

        for arr_item in output:
            for index, num in enumerate(arr_item):
                if num:
                    arr_item[index] = 0
                else:
                    arr_item[index] = 1

        return output
{% endhighlight %}