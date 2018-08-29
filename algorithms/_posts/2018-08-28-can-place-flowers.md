---
layout: algorithm
title: Can Place Flowers
tags: 
    - Python
description: 
    - Suppose you have a long flowerbed in which some of the plots are planted and some are not. However, flowers cannot be planted in adjacent plots - they would compete for water and both would die.
    - Given a flowerbed (represented as an array containing 0 and 1, where 0 means empty and 1 means not empty), and a number n, return if n new flowers can be planted in it without violating the no-adjacent-flowers rule.
example: 
    - input: "flowerbed = [1,0,0,0,1], n = 1"
      output: "True"
    - input: "flowerbed = [1,0,0,0,1], n = 2"
      output: "False"
note: 
    - The input array won't violate no-adjacent-flowers rule.
    - The input array size is in the range of [1, 20000].
    - n is a non-negative integer which won't exceed the input array size.
link: Can Place Flowers - LeetCode
link_url: https://leetcode.com/problems/can-place-flowers/description/
---

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 52 ms, beats 22.42 % of python3 submissions.
{% highlight python %}
class Solution(object):
    def canPlaceFlowers(self, flowerbed, n):
        """
        :type flowerbed: List[int]
        :type n: int
        :rtype: bool
        """
        
        i = 0
        zeros = 1
        count = 0
        while i < len(flowerbed):
            if flowerbed[i] == 0:
                zeros += 1
                if i == len(flowerbed) - 1:
                    zeros += 1
            if flowerbed[i] == 1 or i == len(flowerbed) - 1:
                if zeros % 2 == 1 and zeros != 1:
                    count += zeros // 2
                elif zeros % 2 == 0:
                    count += zeros // 2 - 1
                zeros = 0
            i += 1
            
        return count >= n
{% endhighlight %}