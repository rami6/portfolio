---
layout: algorithm
title: Move Zeroes
tags: 
    - Swift
description: "Given an array `nums`, write a function to move all `0`'s to the end of it while maintaining the relative order of the non-zero elements."
example:
    - input: "[0,1,0,3,12]"
      output: "[1,3,12,0,0]"
note:
    - You must do this in-place without making a copy of the array.
    - Minimize the total number of operations.
link: Move Zeroes - LeetCode
link_url: https://leetcode.com/problems/move-zeroes/description/
---

{% assign desc_var = page.description %}
{% assign example_var = page.example %}
{% assign note_var = page.note %}
{% assign link_var = page.link %}
{% assign url_var = page.link_url %}

{% include problem.html description=desc_var example=example_var note=note_var link=link_var url=url_var %}

<hr/>
<div>Swift<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
{% highlight swift %}
func moveZeroes(_ nums: inout [Int]) {
    var index = 0
    for num in nums {
        if num != 0 {
            nums[index] = num
            index += 1
        }
    }
    for i in index..<nums.count {
        nums[i] = 0
    }
}
{% endhighlight %}