---
layout: algorithm
title: File Owners
tags: 
    - Python
description: 
    - "Implement a group_by_owners function that:"
    - "- Accepts a dictionary containing the file owner name for each file name."
    - "- Returns a dictionary containing a list of file names for each owner name, in any order."
example:
    - input: "{'Input.txt': 'Randy', 'Code.py': 'Stan', 'Output.txt': 'Randy'}"
      output: "{'Randy': ['Input.txt', 'Output.txt'], 'Stan': ['Code.py']}"
note:
link: 1. File Owners - Python Interview Questions | TestDome.com
link_url: https://www.testdome.com/d/python-interview-questions/9
---

<div>Python<span class="write-date"> - {{ page.date | date_to_string }}</span></div>

{% highlight Python %}
class FileOwners:

    @staticmethod
    def group_by_owners(files):
        result = {}
        for fileName, owner in files.items():
            if not owner in result:
                result[owner] = [fileName]
            else:
                result[owner].append(fileName)
        
        return result
{% endhighlight %}