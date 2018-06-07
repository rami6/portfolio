---
layout: algorithm
title: Single Number III
tags: 
    - Python
description: 
    - Given an array of numbers `nums`, in which exactly two elements appear only once and all the other elements appear exactly twice. Find the two elements that appear only once.
example: 
    - input: [1,2,1,3,2,5]
      output: [3,5]

note: 
    - The order of the result is not important. So in the above example, `[5, 3]` is also correct.
    - Your algorithm should run in linear runtime complexity. Could you implement it using only constant space complexity?
link: Single Number III - LeetCode
link_url: https://leetcode.com/problems/single-number-iii/description/
---

I encountered time limit excess so many times. This answer could pass the test, but still slow.
<div>Python(answer 1)<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 1460 ms, beats 0 % of python3 submissions.
{% highlight python %}
class Solution:
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        output = []
        while len(nums) > 0:
            if nums[0] not in nums[1:]:
                output.append(nums.pop(0))
                if len(output) == 2:                
                    return output
            else:
                num = nums.pop(0)
                del nums[nums.index(num)]     
{% endhighlight %}

Then, I kept trying hard to improve runtime complexity. This answer below is my best for now.

<div>Python(answer 2)<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 60 ms, beats 29.56 % of python3 submissions.
{% highlight python %}
class Solution:
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        nums.sort()

        while len(nums) > 2:
            if nums[0] == nums[1]:
                del nums[0:2]
            else:
                nums.append(nums.pop(0))
                    
        return nums
{% endhighlight %}