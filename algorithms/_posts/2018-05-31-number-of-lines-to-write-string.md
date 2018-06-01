---
layout: algorithm
title: Number of Lines To Write String
tags: 
    - Python
description: 
    - "We are to write the letters of a given string `S`, from left to right into lines. Each line has maximum width 100 units, and if writing a letter would cause the width of the line to exceed 100 units, it is written on the next line. We are given an array `widths`, an array where widths[0] is the width of 'a', widths[1] is the width of 'b', ..., and widths[25] is the width of 'z'."
    - "Now answer two questions: how many lines have at least one character from `S`, and what is the width used by the last such line? Return your answer as an integer list of length 2."
example:
    - input: widths = [10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10] / S = "abcdefghijklmnopqrstuvwxyz"
      output: "[3, 60]"
    - input: widths = [4,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10,10] / S = "bbbcccdddaaa"
      output: "[2, 4]"
note:
    - "The length of `S` will be in the range [1, 1000]."
    - "`S` will only contain lowercase letters."
    - "`widths` is an array of length `26`."
    - "`widths[i]` will be in the range of `[2, 10]`."

link: Number of Lines To Write String - LeetCode
link_url: https://leetcode.com/problems/number-of-lines-to-write-string/description/
---

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 36 ms, beats 99.61 % of python3 submissions.
{% highlight python %}
class Solution:
    def numberOfLines(self, widths, S):
        """
        :type widths: List[int]
        :type S: str
        :rtype: List[int]
        """
        unit = 0
        line = 1
        
        for c in S:
            if unit + widths[ord(c) - 97] > 100:
                line += 1
                unit = 0
            unit += widths[ord(c) - 97]
        
        return [line, unit]
{% endhighlight %}