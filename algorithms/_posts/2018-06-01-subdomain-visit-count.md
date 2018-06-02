---
layout: algorithm
title: Subdomain Visit Count
tags: 
    - Python
description: 
    - A website domain like "discuss.leetcode.com" consists of various subdomains. At the top level, we have "com", at the next level, we have "leetcode.com", and at the lowest level, "discuss.leetcode.com". When we visit a domain like "discuss.leetcode.com", we will also visit the parent domains "leetcode.com" and "com" implicitly.
    - Now, call a "count-paired domain" to be a count (representing the number of visits this domain received), followed by a space, followed by the address. An example of a count-paired domain might be "9001 discuss.leetcode.com".
    - "We are given a list `cpdomains` of count-paired domains. We would like a list of count-paired domains, (in the same format as the input, and in any order), that explicitly counts the number of visits to each subdomain."
example: 
    - input: "[“9001 discuss.leetcode.com”]"
      output: "[“9001 discuss.leetcode.com”, “9001 leetcode.com”, “9001 com”]"
      explanation: "We only have one website domain: “discuss.leetcode.com”. As discussed above, the subdomain “leetcode.com” and “com” will also be visited. So they will all be visited 9001 times."
    - input: "[“900 google.mail.com”, “50 yahoo.com”, “1 intel.mail.com”, “5 wiki.org”]"
      output: "[“901 mail.com”,“50 yahoo.com”,“900 google.mail.com”,“5 wiki.org”,“5 org”,“1 intel.mail.com”,“951 com”]"
      explanation: "We will visit “google.mail.com” 900 times, “yahoo.com” 50 times, “intel.mail.com” once and “wiki.org” 5 times. For the subdomains, we will visit “mail.com” 900 + 1 = 901 times, “com” 900 + 50 + 1 = 951 times, and “org” 5 times."
note: 
    - "The length of `cpdomains` will not exceed `100`." 
    - "The length of each domain name will not exceed `100`."
    - "Each address will have either 1 or 2 “.” characters."
    - "The input count in any count-paired domain will not exceed `10000`."
    - "The answer output can be returned in any order."
link: Subdomain Visit Count - LeetCode
link_url: https://leetcode.com/problems/subdomain-visit-count/description/
---

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
- Runtime: 64 ms, beats 98.76 % of python3 submissions.
{% highlight python %}
class Solution:
    def subdomainVisits(self, cpdomains):
        """
        :type cpdomains: List[str]
        :rtype: List[str]
        """
        domain_dict = {}
        output = []

        for domain in cpdomains:
            domain_list = domain.split(" ")
            word_list = domain_list[1].split(".")
            subdomain = ""
            
            for word in reversed(word_list):
                subdomain = word + subdomain

                if subdomain in domain_dict:
                    domain_dict[subdomain] += int(domain_list[0])
                else:
                    domain_dict[subdomain] = int(domain_list[0])
                    
                subdomain = "." + subdomain

        for key, val in domain_dict.items():
            output.append(str(val) + " " + key)

        return output
{% endhighlight %}