---
layout: algorithm
title: Number Complement
tags: 
    - Python
description: 
    - "Given a positive integer, output its complement number. The complement strategy is to flip the bits of its binary representation."
example: 
    - input: 5
      output: 2
      explanation: The binary representation of 5 is 101 (no leading zero bits), and its complement is 010. So you need to output 2.
    - input: 1
      output: 0
      explanation: The binary representation of 1 is 1 (no leading zero bits), and its complement is 0. So you need to output 0.

note: 
    - The given integer is guaranteed to fit within the range of a 32-bit signed integer.
    - You could assume no leading zero bit in the integer’s binary representation.
link: Number Complement - LeetCode
link_url: https://leetcode.com/problems/number-complement/description/
---

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 40 ms, beats 90.18 % of python3 submissions.
{% highlight python %}
class Solution:
    def findComplement(self, num):
        """
        :type num: int
        :rtype: int
        """
        bin_num = "{0:b}".format(num)
        r_str = ""

        for num in bin_num:
            if num == "1":
                r_str += "0"
            else:
                r_str += "1"
        
        return int(r_str, base=2)
{% endhighlight %}