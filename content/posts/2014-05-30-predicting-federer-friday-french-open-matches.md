---
title: "Predicting Federer-Tursunov and other Friday French Open Matches Using Markov Chain"
date: 2014-05-30T00:36:47+00:00
slug: "predicting-federer-friday-french-open-matches"
author: "sixmanguru"
draft: false
tags:
  - "Federer"
  - "Janowicz"
  - "Roland Garros"
  - "ATP World Tour"
  - "Markov Chain"
  - "tennis"
  - "Tursunov"
  - "French Open"
  - "Tsonga"
  - "grand slam"
---

<!-- AdSense Now! V3.40 -->
<!-- Post[count: 1] -->
<div class="adsense adsense-leadin" style="float:right;margin: 12px;">
<!-- Guru2013 -->

</div><p>Today I was enamored with the FiveThirtyEight.com article, <a href="http://fivethirtyeight.com/features/inside-the-shadowy-world-of-high-speed-tennis-betting/" title="538.com">Inside the Shadowy World of High-Speed Tennis Betting</a>. The article mentions the courtsiders who would sit court side at a tennis match and try to relay information quicker than the tournament computers to betting partners. Great read. Not sure these courtsiders were really doing anything illegal.</p>
<p>Buried deep in the article was a mention of the system this one organization created to predict the outcome of tennis matches for betting purposes. It links to a website, Summer of Jeff, and a post, <a href="http://summerofjeff.wordpress.com/2011/01/13/python-code-for-tennis-markov/" title="Summer of Jeff">Python Code for Tennis Markov</a>. If you follow the links to the gitHub site, there is some pretty elaborate Python code for generating probabilities based on <a href="http://en.wikipedia.org/wiki/Markov_chain" title="Markov">Markov Chain theory</a>. The code is pretty easy to use, if you understand Python and statistics, although it needs some cleaning up if you plan on using it for entire match prediction (hint: the matchProbs function needs some fixes to run).</p>
<p>The biggest issue is determining the initial probabilities. You need to create each server’s probability to win a point.</p>
<p>To do this, I decided to hit the trusty <a href="http://atpworldtour.com/" title="atp">ATPworldtour.com</a> website and pulled that information up.</p>
<p><strong>FEDERER-TURSUNOV</strong><br/>
For the year Roger Federer has won 90% of all service games, but only 70% of his service points. On clay this season, he is 89% and 67%. On the other hand, Dmitry Tursunov has won 22% of return games and 36% of return points. On clay he is 24% and 37%. Assuming the majority of these results came from ‘inferior’ players, we might suggest that these numbers regress to each other. I am going to say that Federer is likely to win 65% of his service points. One down.</p>
<p>Now when Tursunov serves, he’s won 75% of service games and 61 of service points, 70%-60% on clay. Federer has won 29% of service return games and 41% of points, 27%-40% on clay. That seems to work out quite nicely to 60-40, so Federer’s return probability will be 40%.</p>
<p>Plugging this into the handy code mentioned above, we get that Federer is a 78.5% favorite to win tomorrow.</p>
<p><strong>TSONGA-JANOWICZ</strong><br/>
Jo-Wilfried Tsonga has won 68% of service points, 65% on clay, while Jerzy Janowicz has won 34% of return points all season and an improved 36% on clay. What is crazy about this is you might suggest that Janowicz is a better clay court than hard court player. Well, amazingly, he had not won a single clay court match this spring before winning his first two rounds at Roland Garros. Oh well. I am still going to give his the benefit and place Tsonga as 65% to win a point on serve.</p>
<p>Returning, Tsonga has been 34% for the year and 35% on clay, while Janowicz has won 62% on serve and 68% on clay. Again Janowicz stats are much better on the terre battue. I am going to just split this straight and leave Tsonga’s return percentage at 34%.</p>
<p>We all know the French crowd will be pulling for their man, so that may be the edge, however, the stats say that Janowicz looks to be a slight favorite at 56.1%. Moving Tsonga’s serve percentage up just a point makes this a dead heat.</p>
<p><strong>THE ODDS</strong><br/>
Looking at the odds at SportsBook.com, Federer is -2500, so that’s a ridiculous bet, but Janowicz is actually +325 v. Tsonga, so that may be worth a play. I hope to look into this more as the tournament progresses.</p>
<!-- AdSense Now! V3.40 -->
<!-- Post[count: 2] -->
<div class="adsense adsense-leadout" style="text-align:center;margin: 12px;">
<!-- Guru2013 -->

</div>
