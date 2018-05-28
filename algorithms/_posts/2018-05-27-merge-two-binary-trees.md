---
layout: algorithm
title: Merge Two Binary Trees
tags: 
    - Python
description: 
    - Given two binary trees and imagine that when you put one of them to cover the other, some nodes of the two trees are overlapped while the others are not.
    - You need to merge them into a new binary tree. The merge rule is that if two nodes overlap, then sum node values up as the new value of the merged node. Otherwise, the NOT null node will be used as the node of new tree.
example:
    - input: 
      output: 
note:
    - The merging process must start from the root nodes of both trees.
link: Merge Two Binary Trees - LeetCode
link_url: https://leetcode.com/problems/merge-two-binary-trees/description/
---

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- I wasn't able to solve this problem. I found an answer written in Java and converted that code to python code.
{% highlight python %}
class Solution:
    def mergeTrees(self, t1, t2):
        """
        :type t1: TreeNode
        :type t2: TreeNode
        :rtype: TreeNode
        """
        merged_node = TreeNode(0)
        if t1 is None:
            return t2
        elif t2 is None:
            return t1
        
        t1.val += t2.val
        t1.left = self.mergeTrees(t1.left, t2.left)
        t1.right = self.mergeTrees(t1.right, t2.right)
        
        return t1
{% endhighlight %}