---
layout: algorithm
title: Find and Replace Pattern
tags: 
    - Python
description: 
    - You have a list of `words` and a `pattern`, and you want to know which words in `words` matches the pattern.
    - A word matches the pattern if there exists a permutation of letters `p` so that after replacing every letter `x` in the pattern with `p(x)`, we get the desired word.
    - "(Recall that a permutation of letters is a bijection from letters to letters: every letter maps to another letter, and no two letters map to the same letter.)"
    - Return a list of the words in `words` that match the given pattern. 
    - You may return the answer in any order.


example: 
    - input: words = [&quot;abc&quot;,&quot;deq&quot;,&quot;mee&quot;,&quot;aqq&quot;,&quot;dkd&quot;,&quot;ccc&quot;], pattern = &quot;abb&quot;
      output: "[&quot;mee&quot;,&quot;aqq&quot;]"
      explanation: "&quot;mee&quot; matches the pattern because there is a permutation {a -> m, b -> e, ...}. 
&quot;ccc&quot; does not match the pattern because {a -> c, b -> c, ...} is not a permutation,
since a and b map to the same letter."
note:
    - "`1 <= words.length <= 50`"
    - "`1 <= pattern.length = words[i].length <= 20`"
link: Find and Replace Pattern - LeetCode
link_url: https://leetcode.com/problems/find-and-replace-pattern/description/
---

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 24 ms, beats 95.35 % of python3 submissions.
{% highlight python %}
class Solution(object):
    def findAndReplacePattern(self, words, pattern):
        """
        :type words: List[str]
        :type pattern: str
        :rtype: List[str]
        """
        answer = []
        dictionary = {}
            
        for word in words:
            for i in range(len(pattern)):
                if dictionary.get(pattern[i]) is None:
                    if word[i] in dictionary.values():
                        break
                    else:
                        dictionary[pattern[i]] = word[i]                        
                elif dictionary[pattern[i]] != word[i]:
                    break

                if i == len(pattern) - 1:
                    answer.append(word)
            dictionary = {}
        
        return answer
{% endhighlight %}
