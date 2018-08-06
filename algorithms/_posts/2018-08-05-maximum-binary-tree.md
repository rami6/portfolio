---
layout: algorithm
title: Maximum Binary Tree
tags: 
    - Python
description: 
    - "Given an integer array with no duplicates. A maximum tree building on this array is defined as follow:"
    - "1) The root is the maximum number in the array."
    - "2) The left subtree is the maximum tree constructed from left part subarray divided by the maximum number."
    - "3) The right subtree is the maximum tree constructed from right part subarray divided by the maximum number."
    - Construct the maximum tree by the given array and output the root node of this tree.

example: 
    - input: [3,2,1,6,0,5]
      output: "return the tree root node representing the following tree:<br>
      &nbsp;&nbsp;&nbsp;&nbsp;6<br>
      &nbsp;/&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#92;<br>
      3&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;5<br>
      &nbsp;&#92;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/<br>
      &nbsp;&nbsp;2&nbsp;&nbsp;0<br>  
      &nbsp;&nbsp;&nbsp;&#92;<br>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1"
note: 
    - The size of the given array will be in the range [1,1000].
link: Maximum Binary Tree - LeetCode
link_url: https://leetcode.com/problems/maximum-binary-tree/description/
---

<div>Python(answer 1)<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 164 ms, beats 15.66 % of python3 submissions.
{% highlight python %}
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def constructMaximumBinaryTree(self, nums):
        """
        :type nums: List[int]
        :rtype: TreeNode
        """
        
        maxNum = nums[0]
        maxIdx = 0

        for idx, num in enumerate(nums):
            if num > maxNum:
                maxNum = num
                maxIdx = idx

        node = TreeNode(maxNum)
        if len(nums) > 1:
            if maxIdx != 0:
                node.left = self.constructMaximumBinaryTree(nums[:maxIdx])
            if maxIdx != len(nums) - 1:
                node.right = self.constructMaximumBinaryTree(nums[maxIdx + 1:])

        return node
{% endhighlight %}

I tried to improve complexity. I put if-statement to filter lists of 1 length, and replaced for-loop with `max()` + while-loop.

<div>Python(answer 2)<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 116 ms, beats 88.08 % of python3 submissions.
{% highlight python %}
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def constructMaximumBinaryTree(self, nums):
        """
        :type nums: List[int]
        :rtype: TreeNode
        """
        
        if len(nums) == 1:
            return TreeNode(nums[0])
        
        maxNum = max(nums)
        maxIdx = 0
        
        while nums[maxIdx] != maxNum:
            maxIdx += 1

        node = TreeNode(maxNum)
        
        if maxIdx != 0:
            node.left = self.constructMaximumBinaryTree(nums[:maxIdx])

        if maxIdx != len(nums) - 1:
            node.right = self.constructMaximumBinaryTree(nums[maxIdx + 1:])

        return node
{% endhighlight %}