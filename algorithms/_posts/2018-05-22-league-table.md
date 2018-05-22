---
layout: algorithm
title: League Table
tags: 
    - Python
description: 
    - "The LeagueTable class tracks the score of each player in a league. After each game, the player records their score with the record_result function." 
    - "The player's rank in the league is calculated using the following logic:"
    - "- The player with the highest score is ranked first (rank 1). The player with the lowest score is ranked last."
    - "- If two players are tied on score, then the player who has played the fewest games is ranked higher."
    - "- If two players are tied on score and number of games played, then the player who was first in the list of players is ranked higher."
    - "Implement the player_rank function that returns the player at the given rank."
example:
note:
link: 5. League Table - Python Interview Questions | TestDome.com
link_url: https://www.testdome.com/d/python-interview-questions/9
---

<div>Python(1st answer)<span class="write-date"> - {{ page.date | date_to_string }}</span></div>

{% highlight Python %}
from collections import Counter
from collections import OrderedDict


class LeagueTable:
    def __init__(self, players):
        self.standings = OrderedDict([(player, Counter()) for player in players])

    def record_result(self, player, score):
        self.standings[player]['games_played'] += 1
        self.standings[player]['score'] += score

    def player_rank(self, rank):
        score_sorted = OrderedDict(sorted(self.standings.items(), 
        key=lambda t: t[1]['score'], reverse=True))
        games_sorted = []

        i = 0
        while i < len(score_sorted):
            sub_list = [list(score_sorted.items())[i]]
            if i < len(score_sorted) - 1:
                j = i + 1
                while j < len(score_sorted) and 
                list(score_sorted.items())[i][1]['score'] == 
                list(score_sorted.items())[j][1]['score']:
                    sub_list.append(list(score_sorted.items())[j])
                    j += 1

            sub_list.sort(key=lambda t: t[1]['games_played'])
            games_sorted.extend(sub_list)
            i = j

        return games_sorted[rank - 1][0]      
{% endhighlight %}

In one out of 4 test cases, running time exceeded the time limit. I will be back to this problem after learning.