---
layout: algorithm
title: Judge Route Circle
tags: 
    - Python
description: 
    - "Initially, there is a Robot at position (0, 0). Given a sequence of its moves, judge if this robot makes a circle, which means it moves back to the original place."
    - "The move sequence is represented by a string. And each move is represent by a character. The valid robot moves are `R` (Right), `L` (Left), `U` (Up) and `D` (down). The output should be true or false representing whether the robot makes a circle."
example:
    - input: \"UD\"
      output: "True"
    - input: \"LL\"
      output: "False"
note:
link: Judge Route Circle - LeetCode
link_url: https://leetcode.com/problems/judge-route-circle/description/
---

<div>Python(1st answer)<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 52 ms, beats 77.08 % of python3 submissions.
{% highlight python %}
from collections import Counter


class Solution:
    def judgeCircle(self, moves):
        """
        :type moves: str
        :rtype: bool
        """
        c = Counter(moves)

        if c['U'] == c['D'] and c['R'] == c['L']:
            return True

        return False
{% endhighlight %}

I tried to find faster code, using dictionary, loop, etc. Finally I found the one, and it was so simple.

<div>Python(2nd answer)<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 44 ms, beats 93.94 % of python3 submissions.
{% highlight python %}
class Solution:
    def judgeCircle(self, moves):
        """
        :type moves: str
        :rtype: bool
        """
        return moves.count('U') == moves.count('D') and moves.count('L') == moves.count('R')
{% endhighlight %}