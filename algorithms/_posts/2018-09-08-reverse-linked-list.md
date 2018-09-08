---
layout: algorithm
title: Reverse Linked List
tags: 
    - Python
description: 
    - Reverse a singly linked list.


example: 
    - input: 1->2->3->4->5->NULL
      output: 5->4->3->2->1->NULL
      explanation:
note: 
link: Reverse Linked List - LeetCode
link_url: https://leetcode.com/problems/reverse-linked-list/description/
---

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 24 ms, beats 100.00 % of python3 submissions.
{% highlight python %}
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        previous = None
        while head:
            temp = head.next
            head.next = previous
            previous = head
            head = temp
        
        return previous
{% endhighlight %}
