---
layout: algorithm
title: Unique Morse Code Words
tags: 
    - Python
description: 
    - International Morse Code defines a standard encoding where each letter is mapped to a series of dots and dashes, as follows&#58; <code>"a"</code> maps to <code>".-"</code>, <code>"b"</code> maps to <code>"-..."</code>, <code>"c"</code> maps to <code>"-.-."</code>, and so on.
    - Now, given a list of words, each word can be written as a concatenation of the Morse code of each letter. For example, "cab" can be written as "-.-.-....-", (which is the concatenation "-.-." + "-..." + ".-"). We'll call such a concatenation, the transformation of a word.
    - Return the number of different transformations among all words we have.
example:
    - input: words = ["gin", "zen", "gig", "msg"]
      output: 2
note:
    - "The length of `words` will be at most `100`."
    - "Each `words[i]` will have length in range `[1, 12]`."
    - "`words[i]` will only consist of lowercase letters."
link: Unique Morse Code Words - LeetCode
link_url: https://leetcode.com/problems/unique-morse-code-words/description/
---

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 36 ms, beats 100.00 % of python3 submissions at this time!
{% highlight python %}
class Solution:
    def uniqueMorseRepresentations(self, words):
        """
        :type words: List[str]
        :rtype: int
        """
        letter_codes = [".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."]
        codes_dict = {}
        codes = []
        length = len(words)
        count = 1
        
        if length == 0:
            return 0
        elif length == 1:
            return 1
        
        for index, code in enumerate(letter_codes):
            codes_dict[chr(ord('a') + index)] = code
        
        for word in words:
            code = ""
            for c in word:
                code += codes_dict[c]
            codes.append(code)
        
        codes.sort()
        
        for i in range(length - 1):
            if codes[i] != codes[i + 1]:
                count += 1
            
        return count
{% endhighlight %}