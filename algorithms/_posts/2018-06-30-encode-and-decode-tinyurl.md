---
layout: algorithm
title: Encode and Decode TinyURL
tags: 
    - Python
description: 
    - TinyURL is a URL shortening service where you enter a URL such as `https://leetcode.com/problems/design-tinyurl` and it returns a short URL such as `http://tinyurl.com/4e9iAk`.
    - Design the `encode` and `decode` methods for the TinyURL service. There is no restriction on how your encode/decode algorithm should work. You just need to ensure that a URL can be encoded to a tiny URL and the tiny URL can be decoded to the original URL.


example: 
note: 
link: Encode and Decode TinyURL - LeetCode
link_url: https://leetcode.com/problems/encode-and-decode-tinyurl/description/
---

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 49 ms, beats 77.73 % of python3 submissions.
{% highlight python %}
import random


class Codec:
    code_dict = {}
    digits = 1

    def encode(self, longUrl):
        """Encodes a URL to a shortened URL.

        :type longUrl: str
        :rtype: str
        """
        unique = Codec.random_str_factory(self)

        while unique in Codec.code_dict:
            unique = Codec.random_str_factory(self)

        Codec.code_dict[unique] = longUrl

        if len(Codec.code_dict) > 36 ** Codec.digits:
            Codec.digits += 1

        return "http://tinyurl.com/" + unique

    def decode(self, shortUrl):
        """Decodes a shortened URL to its original URL.

        :type shortUrl: str
        :rtype: str
        """
        unique = shortUrl[19:]
        return Codec.code_dict[unique]

    def random_str_factory(self):
        rand_str = ""
        for i in range(Codec.digits):
            rand_num = random.randint(87, 123)
            if rand_num < 97:
                rand_num -= 87
                rand_str += str(rand_num)
            else:
                rand_str += str(chr(rand_num))
        return rand_str

# Your Codec object will be instantiated and called as such:
# codec = Codec()
# codec.decode(codec.encode(url))
{% endhighlight %}