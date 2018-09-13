---
layout: algorithm
title: Sock Merchant
tags: 
    - Python
description: 
    - See the source link below for the description.
link: Sock Merchant - HackerRank
link_url: https://www.hackerrank.com/challenges/sock-merchant/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=warmup
---

<div>Python (answer 1)<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
{% highlight python %}
def sockMerchant(n, ar):
    ar = sorted(ar)
    count = 0
    i = 0
    
    while i < n - 1:
        if ar[i] == ar[i + 1]:
            count += 1
            i += 2
        else:
            i += 1
    
    return count
{% endhighlight %}

I made another solution using Counter.

<div>Python (answer 2)<span class="write-date"> - {{ page.date | date_to_string }}</span></div>
{% highlight python %}
from collections import Counter


def sockMerchant(n, ar):
    c = Counter(ar)
    count = 0
    for item in c:
        count += c[item] // 2
    
    return count
{% endhighlight %}

