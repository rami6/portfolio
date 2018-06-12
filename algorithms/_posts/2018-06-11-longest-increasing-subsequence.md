---
layout: algorithm
title: Longest Increasing Subsequence
tags: 
    - Java
    - Python
description: 
    - Given an unsorted array of integers, find the length of longest increasing subsequence.
example: 
    - input: [10,9,2,5,3,7,101,18]
      output: 4
      explanation: The longest increasing subsequence is [2,3,7,101], therefore the length is 4.
note: 
    - There may be more than one LIS combination, it is only necessary for you to return the length.
    - Your algorithm should run in O(n<sup>2</sup>) complexity.
    - (Follow up) Could you improve it to O(n log n) time complexity?
link: Longest Increasing Subsequence - LeetCode
link_url: https://leetcode.com/problems/longest-increasing-subsequence/description/
---

I coded the answer in both Java and Python.

<div>Java<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 31 ms, beats 35.48 % of Java submissions.
{% highlight java %}
class Solution {
    public int lengthOfLIS(int[] nums) {
        int[] arr = new int[nums.length];
        int max = 0;
        
        if (nums.length > 0) {
            arr[0] = 1;
            max = 1;
        
            for (int i = 1; i < nums.length; i++) {
                arr[i] = 1;
                for (int j = 0; j < i; j++) {
                    if (nums[j] < nums[i] && (arr[j] + 1) > arr[i]) {
                        arr[i] = arr[j] + 1;
                    }
                }
                if (arr[i] > max) {
                    max = arr[i];
                }
            }
        }
        return max;        
    }
}
{% endhighlight %}

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 920 ms, beats 54.45 % of python3 submissions.
{% highlight python %}
class Solution:
    def lengthOfLIS(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        arr = []
        max = 0

        if len(nums) > 0:
            arr.append(1)
            max = 1
            for i in range(1, len(nums)):
                arr.append(1)
                for j in range(0, i):
                    if nums[j] < nums[i] and arr[j] + 1 > arr[i]:
                        arr[i] = arr[j] + 1

                if max < arr[i]:
                    max = arr[i]

        return max
{% endhighlight %}