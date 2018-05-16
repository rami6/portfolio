---
layout: algorithm
title: Jewels and Stones
tags: 
    - Python
description: 
    - "You're given strings `J` representing the types of stones that are jewels, and `S` representing the stones you have.  Each character in `S` is a type of stone you have.  You want to know how many of the stones you have are also jewels." 
    - The letters in <code>J</code> are guaranteed distinct, and all characters in <code>J</code> and <code>S</code> are letters. Letters are case sensitive, so <code>"a"</code> is considered a different type of stone from <code>"A"</code>.
example:
    - input: J = "aA", S = "aAAbbbb"
      output: "3"
note:
    - "`S` and `J` will consist of letters and have length at most 50."
    - "The characters in `J` are distinct."
link: Jewels and Stones - LeetCode
link_url: https://leetcode.com/problems/jewels-and-stones/description/
---

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>

{% highlight Python %}
class Solution:
    def numJewelsInStones(self, J, S):
        """
        :type J: str
        :type S: str
        :rtype: int
        """
        count = 0

        for stone in S:
            for jewel in J:
                if stone == jewel:
                    count += 1
                    break
        
        return count
{% endhighlight %}