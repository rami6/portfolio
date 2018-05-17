---
layout: algorithm
title: Palindrome
tags: 
    - Python
description: 
    - "A palindrome is a word that reads the same backward or forward."
    - "Write a function that checks if a given word is a palindrome. Character case should be ignored."
example:
    - input: "\"Deleveled\""
      output: "True"
note:
link: 2. Palindrome - Python Interview Questions | TestDome.com
link_url: https://www.testdome.com/d/python-interview-questions/9
---

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>

{% highlight Python %}
class Palindrome:

    @staticmethod
    def is_palindrome(word):
        word = word.lower()
        reversedWord = word[::-1]
        return word == reversedWord
{% endhighlight %}