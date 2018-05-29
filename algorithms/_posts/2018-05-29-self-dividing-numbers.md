---
layout: algorithm
title: Self Dividing Numbers
tags: 
    - Python
description: 
    - A self-dividing number is a number that is divisible by every digit it contains.
    - "For example, 128 is a self-dividing number because `128 % 1 == 0`, `128 % 2 == 0`, and `128 % 8 == 0`."
    - Also, a self-dividing number is not allowed to contain the digit zero.
    - Given a lower and upper number bound, output a list of every possible self dividing number, including the bounds if possible.
example:
    - input: left = 1, right = 22
      output: "[1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 12, 15, 22]"
note:
    - "The boundaries of each input argument are `1 <= left <= right <= 10000`."
link: Self Dividing Numbers - LeetCode
link_url: https://leetcode.com/problems/self-dividing-numbers/description/
---

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 52 ms, beats 98.29 % of python3 submissions.
{% highlight python %}
class Solution:
    def selfDividingNumbers(self, left, right):
        """
        :type left: int
        :type right: int
        :rtype: List[int]
        """
        nums = []
        for num in range(left, right + 1):
            n = num
            self_divide = True
            while n > 0:
                if n % 10 == 0 or num % (n % 10) != 0:
                    self_divide = False
                    break
                n //= 10
                
            if self_divide:
                nums.append(num)
        
        return nums
{% endhighlight %}