---
layout: algorithm
title: Maximum Product of Three Numbers
tags: 
    - Python
description: 
    - Given an integer array, find three numbers whose product is maximum and output the maximum product.


example: 
    - input: "[1,2,3]"
      output: 6
    - input: "[1,2,3, 4]"
      output: 24
note: 
    - The length of the given array will be in range [3,10<sup>4</sup>] and all elements are in the range [-1000, 1000].
    - Multiplication of any three numbers in the input won't exceed the range of 32-bit signed integer.
link: Maximum Product of Three Numbers - LeetCode
link_url: https://leetcode.com/problems/maximum-product-of-three-numbers/description/
---

<div>Python(answer 1)<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 72 ms, beats 39.09 % of python3 submissions.
{% highlight python %}
class Solution(object):
    def maximumProduct(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """       
        nums.sort()
        return max(nums[0] * nums[1] * nums[-1], nums[-1] * nums[-2] * nums[-3])
{% endhighlight %}

This answer is short, but slow. So, I avoid sorting `nums`.

<div>Python(answer 2)<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 64 ms, beats 76.96 % of python3 submissions.
{% highlight python %}
class Solution(object):
    def maximumProduct(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        
        max1 = max(nums)
        nums.remove(max1)
        
        max2 = max(nums)
        nums.remove(max2)
        
        max3 = max(nums)
        nums.remove(max3)
        
        min1 = max3
        min2 = max2
        
        if len(nums) > 0:
            min1 = min(nums)
            nums.remove(min1)
            
        if len(nums) > 0:
            min2 = min(nums)
            nums.remove(min2)
        
        return max(max1 * max2 * max3, max1 * min1 * min2)
{% endhighlight %}

I looked into discussion threads and found a nice answer written in Java:
<a href="https://leetcode.com/problems/maximum-product-of-three-numbers/discuss/157635/Java-very-simple-approach-beats-100">https://leetcode.com/problems/maximum-product-of-three-numbers/discuss/157635/Java-very-simple-approach-beats-100</a>
