---
layout: algorithm
title: Student Attendance Record I
tags: 
    - Python
description: 
    - "You are given a string representing an attendance record for a student. The record only contains the following three characters:"
    - "'A' : Absent."
    - "'L' : Late."
    - "'P' : Present."
    - A student could be rewarded if his attendance record doesn't contain more than one 'A' (absent) or more than two continuous 'L' (late).
    - You need to return whether the student could be rewarded according to his attendance record.


example: 
    - input: "PPALLP"
      output: "True"
    - input: "PPALLL"
      output: "False"
note: 
link: Student Attendance Record I - LeetCode
link_url: https://leetcode.com/problems/student-attendance-record-i/description/
---

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 24 ms, beats 64.51 % of python3 submissions.
{% highlight python %}
class Solution(object):
    def checkRecord(self, s):
        """
        :type s: str
        :rtype: bool
        """
        
        if s.count('A') > 1:
            return False

        l_count = 0
        l_index = 0
        length = len(s)
        while s.find('L', l_index) > -1:
            l_index = s.find('L', l_index)
            while l_index < length and s[l_index] == 'L':
                l_count += 1
                l_index += 1
                if l_count > 2:
                    return False
            l_count = 0
            l_index += 1

        return True
{% endhighlight %}