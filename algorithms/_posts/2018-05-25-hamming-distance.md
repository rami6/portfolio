---
layout: algorithm
title: Hamming Distance
tags: 
    - Python
description: 
    - "The Hamming distance between two integers is the number of positions at which the corresponding bits are different."
    - "Given two integers `x` and `y`, calculate the Hamming distance."
example:
    - input: x = 1, y = 4
      output: 2
note:
    - "0 ≤ `x`, `y` < 2<sup>31</sup>"
link: Hamming Distance - LeetCode
link_url: https://leetcode.com/problems/hamming-distance/description/
---

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 36 ms, beats 100.00 % of python3 submissions at this time!
{% highlight python %}
class Solution:
    def hammingDistance(self, x, y):
        """
        :type x: int
        :type y: int
        :rtype: int
        """
        bin_x = str(bin(x)[2:])
        bin_y = str(bin(y)[2:])
        longer = bin_x
        shorter = bin_y
        distance = 0
        
        if len(bin_x) - len(bin_y) < 0:
            longer = bin_y
            shorter = bin_x
            
        for i in range(len(shorter)):
            if longer[len(longer) - 1 - i] != shorter[len(shorter) - 1 - i]:
                distance += 1
                
        if len(shorter) != len(longer):
            for i in range(len(shorter), len(longer)):
                if longer[len(longer) - 1 - i] == "1":
                    distance += 1
        
        return distance
{% endhighlight %}