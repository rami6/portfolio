---
layout: algorithm
title: Array Partition I
tags: 
    - Python
description: 
    - Given an array of **2n** integers, your task is to group these integers into **n** pairs of integer, say (a<sub>1</sub>, b<sub>1</sub>), (a<sub>2</sub>, b<sub>2</sub>), ..., (a<sub>n</sub>, b<sub>n</sub>) which makes sum of min(a<sub>i</sub>, b<sub>i</sub>) for all i from 1 to n as large as possible.
example:
    - input: "[1,4,3,2]"
      output: 4
note:
    - "**n** is a positive integer, which is in the range of [1, 10000]."
    - All the integers in the array will be in the range of [-10000, 10000].

link: Array Partition I - LeetCode
link_url: https://leetcode.com/problems/array-partition-i/description/
---

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 112 ms, beats 93.77 % of python3 submissions.
{% highlight python %}
class Solution:
    def arrayPairSum(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        mins = sorted(nums)[::2]
        sum_min = 0
        for n in mins:
            sum_min += n
        
        return sum_min
{% endhighlight %}