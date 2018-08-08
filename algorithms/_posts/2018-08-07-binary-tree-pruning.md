---
layout: algorithm
title: Binary Tree Pruning
tags: 
    - Python
description: 
    - We are given the head node `root` of a binary tree, where additionally every node's value is either a 0 or a 1.
    - Return the same tree where every subtree (of the given tree) not containing a 1 has been removed.
    - (Recall that the subtree of a node X is X, plus every node that is a descendant of X.)

example: 
    - input: "[1,null,0,0,1]"
      output: "[1,null,0,null,1]"
      explanation: Contains image. See source page.
note: 
    - The binary tree will have at most `100 nodes`.
    - The value of each node will only be `0` or `1`.
link: Binary Tree Pruning - LeetCode
link_url: https://leetcode.com/problems/binary-tree-pruning/description/
---

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 20 ms, beats 100.00 % of python3 submissions.
{% highlight python %}
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def pruneTree(self, root):
        """
        :type root: TreeNode
        :rtype: TreeNode
        """
        
        if root.left:
            if self.hasDescendant(root.left):
                self.pruneTree(root.left)
            if self.isRemoved(root.left):
                root.left = None
        
        if root.right:
            if self.hasDescendant(root.right):
                self.pruneTree(root.right)
            if self.isRemoved(root.right):
                root.right = None
            
        return root
    
    def hasDescendant(self, node):
        return node.left or node.right
    
    def isRemoved(self, node):
        return node.val == 0 and not self.hasDescendant(node) 
{% endhighlight %}
