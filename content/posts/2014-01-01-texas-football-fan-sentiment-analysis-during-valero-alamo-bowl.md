---
title: "Texas Football Fan Sentiment Analysis During Valero Alamo Bowl"
date: 2014-01-01T19:48:35+00:00
slug: "texas-football-fan-sentiment-analysis-during-valero-alamo-bowl"
author: "granger"
draft: false
tags:
  - "Alamo Bowl"
  - "Mack Brown"
  - "College Football"
  - "Oregon Ducks"
  - "Texas Football"
  - "Football"
  - "UT-Austin"
  - "Hookem"
---

<p>With Monday night’s Alamo Bowl being Coach Mack Brown’s final game as coach of the Texas Longhorns, it seemed like a good opportunity to test fan sentiment on the occasion via Twitter. I captured tweets containing certain words in an attempt to follow sentiment towards Mack Brown and Texas over time, leading up to the game, during the game and afterwards for a brief period.</p>
<p>I began collecting data around 2:25 PM CST and stopped just after 10:00 PM. The search terms I used were: Mack Brown, mackbrown, Texas Football, Texas Longhorn, hookem and hook em. During that time period, over 51,000 tweets were collected using these search terms. Please not that these terms could be used as regular words, a part of words as well as hashtags.</p>
<p><strong>Alamo Bowl Pre-Game</strong><br/>
Mack Brown is a good man and I have had the opportunity to meet him several times and have always found him amazing. I won’t go into the details, but he’s the type of guy that makes you feel important, despite the fact he’s probably the most important guy in whatever room he is in.</p>
<p>But things didn’t really end well on the 40 Acres, so I thought it might be interesting to see what transpired over the day.</p>
<p>To find sentiment, I utilized the R package, qdap (Quantitative Discourse Analysis Package), created by Tyler Rinker. The polarity function is based on <a href="http://www.inside-r.org/howto/mining-twitter-airline-consumer-sentiment">Jeffrey Breen’s work</a>.</p>
<p>Tweets are evaluated based on the words within them, utilizing the polarity function, which assigns this based on the sentiment dictionary (Hu and Liu, 2004). Approximately 50% of the tweets are neutral, earning a score of 0.</p>
<p>As I stated above, there were over 51,000 tweets, so plotting them over time would basically give you a huge cluster centered around the y-axis.</p>
<p>Instead, I decided to collect the tweets in 5-minute intervals and find average polarity. (You can click on the chart for a larger view)</p>
<div class="wp-caption alignnone" id="attachment_336" style="max-width: 310px"><a href="http://sixmanguru.com/wp-content/uploads/2014/01/UTFanSentiment.jpg"><img alt="" class="wp-image-336 size-medium" height="170" sizes="(max-width: 300px) 100vw, 300px" src="http://sixmanguru.com/wp-content/uploads/2014/01/UTFanSentiment-300x170.jpg" srcset="http://sixmanguru.com/wp-content/uploads/2014/01/UTFanSentiment-300x170.jpg 300w, http://sixmanguru.com/wp-content/uploads/2014/01/UTFanSentiment.jpg 550w" width="300"/></a><p class="wp-caption-text">Texas Fan Sentiment</p></div>
<p>As you can see, the average polarity was always positive during the pregame. Reading through the early tweets, you can see a bunch of congratulatory and well-wishing tweets directed at Coach Brown. As we near kickoff, the ‘positive’ flavor of the tweets drops dramatically, but the volume of tweets begins to take off.</p>
<p><strong>The First Half</strong><br/>
There’s a quick peak as kickoff approaches (almost 2k tweets in the five minute period around kickoff), then it tapers off a bit (300-500 tweets every five minutes).</p>
<p><a href="http://sixmanguru.com/wp-content/uploads/2014/01/Tweetsper5.jpg"><img alt="" class="alignnone wp-image-334 size-medium" height="153" sizes="(max-width: 300px) 100vw, 300px" src="http://sixmanguru.com/wp-content/uploads/2014/01/Tweetsper5-300x153.jpg" srcset="http://sixmanguru.com/wp-content/uploads/2014/01/Tweetsper5-300x153.jpg 300w, http://sixmanguru.com/wp-content/uploads/2014/01/Tweetsper5.jpg 549w" width="300"/></a></p>
<p>The first big change comes when Case McCoy through the pick six on the first possession of the game. Not only does sentiment fall, but the volume of tweets begins to rise following the interception.</p>
<p>Sentiment fluctuates back and forth throughout the first half. I am guessing these are directly related to the Texas defense (positive) and offense (not-so positive) being on the field.</p>
<p>Again, when Oregon makes the big drive and scores at the end of the half, Texas fans react with expected disdain.</p>
<p><strong>Second Half</strong><br/>
Sentiment stabilizes during halftime and doesn’t really dip too badly until the final pick six by McCoy at the end of the game.</p>
<p>The most interesting discovery are the peaks in volume and what I call ‘Plus-Minus’. Plus-Minus is the number of positive tweets minus the number of negative tweets during the five minute interval.</p>
<p><a href="http://sixmanguru.com/wp-content/uploads/2014/01/plus-minus.jpg"><img alt="" class="alignnone wp-image-335 size-medium" height="175" sizes="(max-width: 300px) 100vw, 300px" src="http://sixmanguru.com/wp-content/uploads/2014/01/plus-minus-300x175.jpg" srcset="http://sixmanguru.com/wp-content/uploads/2014/01/plus-minus-300x175.jpg 300w, http://sixmanguru.com/wp-content/uploads/2014/01/plus-minus.jpg 548w" width="300"/></a></p>
<p>The first major peak comes in the second half when Tyrone Swoopes enters the game. Swoopes is a very popular freshman quarterback many fans believe should have been given more playing time when Case McCoy struggled during the season.</p>
<p>Interestingly enough, the language was not as strongly positive as other times during the game, despite a preponderance of positive tweets.</p>
<p>The final big negative dip of the night came on Case McCoy’s second interception that went for a touchdown. The sentiment was so strong, it was the only time all evening where the average dipped below neutral.</p>
<p><strong>Post Game</strong><br/>
Texas fans appear to rebound fairly quickly after the game. It appears that fans were more interested in wishing Coach Brown well, than bashing the teams’ performance. Positive polarity reached its second-highest peak of the night, while tweet volume and Plus-Minus reach night-high peaks.</p>
<p><strong>Final Thoughts</strong><br/>
Obviously, when you limit yourself to search terms specifically tied to a person, team and school, you get skewed results. I did not include the term ‘Alamo Bowl’ specifically for this reason. I did not want Oregon fan or ‘bowl watcher’ sentiment included.</p>
<p>Since this past summer when I posted a twitter cloud of terms used in tweets at the 2013 NCAA Division I Tennis Championships, I have wanted to use R to do some ‘sentiment analysis’ on tweets during an event. I was initially stymied by Twitter’s move to OAuth, then by my fall class load.</p>
<p>Luckily, my cohort and friend, Taylor Smith was thinking the along the same lines and created an awesome pathway to try this out. <a href="https://github.com/tgsmith61591/Twitter-and-UT-Football">Taylor details his methods here.</a></p>
<p>I had to make some modifications to his code and also altered my methods a bit, but the main collection, cleaning and initial evaluation of the data was the same. I will detail my specific changes in a later post.</p>
