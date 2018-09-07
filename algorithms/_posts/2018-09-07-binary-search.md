---
layout: algorithm
title: Binary Search
tags: 
    - Python
description: 
    - Given a sorted (in ascending order) integer array `nums` of `n` elements and a `target` value, write a function to search `target` in `nums`. If `target` exists, then return its index, otherwise return `-1`.


example: 
    - input: "nums = [-1,0,3,5,9,12], target = 9"
      output: 4
      explanation: 9 exists in nums and its index is 4
    - input: "nums = [-1,0,3,5,9,12], target = 2"
      output: -1
      explanation: 2 does not exist in nums so return -1
note: 
    - You may assume that all elements in `nums` are unique.
    - "`n` will be in the range `[1, 10000]`."
    - The value of each element in `nums` will be in the range `[-9999, 9999]`.
link: Binary Search - LeetCode
link_url: https://leetcode.com/problems/binary-search/description/
---

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 32 ms, beats 99.04 % of python3 submissions.
{% highlight python %}
class Solution(object):
    def search(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        low = 0
        high = len(nums) - 1
        while low <= high:
            mid = (low + high) // 2
            if nums[mid] == target:
                return mid
            elif nums[mid] < target:
                low = mid + 1
            else:
                high = mid - 1
        return -1
{% endhighlight %}