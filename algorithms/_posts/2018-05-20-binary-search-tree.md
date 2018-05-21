---
layout: algorithm
title: Binary Search Tree
tags: 
    - Python
description: 
    - "Binary search tree (BST) is a binary tree where the value of each node is larger or equal to the values in all the nodes in that node's left subtree and is smaller than the values in all the nodes in that node's right subtree."
    - "Write a function that checks if a given binary search tree contains a given value."
example:
    - input: "root = n2, value = 3 [tree: n1 (Value: 1, Left: null, Right: null), n2 (Value: 2, Left: n1, Right: n3), n3 (Value: 3, Left: null, Right: null)]"
      output: "True"
note:
link: 3. Binary Search Tree - Python Interview Questions | TestDome.com
link_url: https://www.testdome.com/d/python-interview-questions/9
---

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>

{% highlight Python %}
import collections

class BinarySearchTree:

  Node = collections.namedtuple('Node', ['left', 'right', 'value'])
    
  @staticmethod
  def contains(root, value):
    result = False
    if root:
      if root.value == value:
        return True
      elif root.value > value:
        result = BinarySearchTree.contains(root.left, value)
      else:
        result = BinarySearchTree.contains(root.right, value)
        
    return result
{% endhighlight %}