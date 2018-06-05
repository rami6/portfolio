---
layout: algorithm
title: Shortest Distance to a Character
tags: 
    - Python
description: 
    - "Given a string `S` and a character `C`, return an array of integers representing the shortest distance from the character C in the string."
example: 
    - input: S = "loveleetcode", C = 'e'
      output: "[3, 2, 1, 0, 1, 0, 0, 1, 2, 2, 1, 0]"
      explanation: 
note: 
    - "`S` string length is in `[1, 10000]`."
    - "`C` is a single character, and guaranteed to be in string `S`."
    - "All letters in `S` and `C` are lowercase."
link: Shortest Distance to a Character - LeetCode
link_url: https://leetcode.com/problems/shortest-distance-to-a-character/description/
---

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 48 ms, runtime distribution didn't be shown because of less data.
{% highlight python %}
class Solution:
    def shortestToChar(self, S, C):
        """
        :type S: str
        :type C: str
        :rtype: List[int]
        """
        C_index_fw = S.find(C)
        C_index_bk = None
        output = []
        
        for i in range(len(S)):
            if S[i] == C:
                output.append(0)
                C_index_bk = i
                C_index_fw = S.find(C, i + 1)
            elif C_index_bk is None:
                output.append(C_index_fw - i)
            elif C_index_fw < 0:
                output.append(i - C_index_bk)
            else:
                output.append(min(C_index_fw - i, i - C_index_bk))
                    
        return output
{% endhighlight %}