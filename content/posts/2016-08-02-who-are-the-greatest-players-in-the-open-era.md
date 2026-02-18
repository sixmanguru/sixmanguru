---
title: "Tennis Note #36: Creme de la creme -- Identifying the best of each tennis cluster"
date: 2016-08-02T03:52:23+00:00
slug: "who-are-the-greatest-players-in-the-open-era"
author: "granger"
draft: false
tags:
  - "tennis"
  - "Rankings"
  - "ATP"
  - "cluster analysis"
  - "TrueSkill"
---

![Brand new tennis ball among eight used ones](/images/tennis-clusters/hero.jpeg)
*Photo by Horia Varlan [CC 2.0]*

We talk about it all of the time -- who is the greatest player of all-time?

Is it the player who won the most Grand Slam titles, the player ranked number one for the most weeks or the person with the best record against the premier players of that era? Is it a combination of these three things or more? What factors are important when it comes to this discussion?

These are the questions that arise while discussing the GOAT, and it is especially fun in the current era of Roger Federer, Novak Djokovic and Rafael Nadal.

I recently began pondering who even makes the cut if we were to construct a list of the greats. Another interesting proposition would be to determine the best second-tier players of all-time or even third-tier players. How can we identify the best of each hierarchical step in tennis?

In order to answer this question, I have turned to a common tool in analytics called cluster analysis.

## Methodology

In the effort of full disclosure, I drew inspiration from an article in the Journal of Quantitative Analysis of Sports entitled, "Match Play: Using Statistical Methods to Categorize PGA Tour Players' Careers" by Martin L. Puterman and Stefan M. Wittman at the University of British Columbia.

I decided to categorize male professional tennis players during most of the Open Era (1972-2015). Initially, I created over twenty categories from the year-end rankings. This included mean rank, best rank, range of ranks, years in top-10, percent of career improving and maximum single decline. However, I found this data, statistically speaking, did not describe overall career performance because it was too highly correlated.

Ultimately, I found overall career performance better described by the proportion of time a player spent ranked in various categories or buckets -- top 10, top 20, top 50, top 100, beyond 100.

![Chart](/images/tennis-clusters/chart-01.png)

![Chart](/images/tennis-clusters/chart-02.png)

![Chart](/images/tennis-clusters/chart-03.png)

To cut down on the sheer number of players being considered, find the creme de la creme, I required players to finish the year in the top 100 for a minimum of eight years.

Why top 100? It seems to be right around the cutoff for the Grand Slam tournaments each year and a bellwether of success.

Why eight years? Five years seems too little to be considered one of the 'greats' and 10 years was a bit of a stretch.

Of course due to these assumptions, several older players from the early years of the Open Era are eliminated or just plain misinterpreted within the analysis because their careers ended soon after 1972. Also, there are several younger players who did not reach the top-100 until after 2007 for the first time, and therefore not eight years. With constraints like these, I expected the cut offs.

In addition, I eliminated all year-end rankings greater than 600, since for the first 30 years of the rankings, the lists rarely passed that range. Also, it did not seem useful when comparing against each decade, since players are most likely playing only a few ITF tournaments and working their way into the main tour.

## K-Means Clustering

Clustering is a mathematical method of grouping in which k represents the number of categories. Interestingly enough, there was very little change between the top groups no matter the selection. The numbers suggested somewhere between five and seven clusters so I opted for six clusters.

## Understanding the Results

The table below represents the percentages that players from each group were within those ranking levels during their careers (using year-end rankings). For instance, Cluster A has spent approximately 72% of their collective career in the top-10 and about 8% outside the top-100. Based on this knowledge, we can identify the different groups.

![Cluster results table](/images/tennis-clusters/cluster-results.png)
*Group A spends 72% of their career in the top 10. Meanwhile Group D spends 46% of their career ranked between 21 and 50.*

## A. The Elites

**Players in Cluster: 13. Most Representative Player: Novak Djokovic**

These guys have been (or currently are) in the top-10 for more than 72% of their career and less than 9% outside of the top-100.

![Cluster A player list](/images/tennis-clusters/cluster-a-list.png)

There are 13 players in this group, which is pretty salty. Upon seeing this cluster, my first impression was that 12 of these would probably be consensus picks, with one surprise in there. But when you look at the career plot for these players versus a few that did not make the cut, this player fits right in.

Of course there are omissions, but we can get to that later.

All plots will illustrate age of the player vs. rank.

![Cluster A career plot](/images/tennis-clusters/cluster-a-plot.png)

Obviously Borg left us too early, but he entered the limelight sooner than the others and is just part of that crawl you see of these greats at the bottom. You can see Agassi's rough period where he jumped outside the top-100 and then climbed back into the top-5 for several years.

Roddick took to the stage about the same time as the others and consistently appeared in the top 10 before abruptly leaving the game at age 30.

When you mathematically search for the player who best represents this group (closest to the center), it is current world number one, Novak Djokovic. He has the same early rank trajectory as the others and continues to make his case as the greatest player of all time.

![Djokovic as representative player](/images/tennis-clusters/cluster-a-djokovic.png)

This is a fantastic group and I am not sure how you could exclude someone from it. It is also interesting because when you look at subsequent groups, I am not sure who you can add. Sure, a few players competed with this elite field, but none really had the consistency within the top-10 like these guys.

## B. The Second Tier

**Players in Cluster: 36. Most Representative Player: Tim Henman**

This is where things get even more interesting. As you can see from the earlier table of cluster definitions, Cluster B spent a third of their careers in the top-10 and over 50% in the top-20.

![Cluster B player list](/images/tennis-clusters/cluster-b-list.png)

The list includes 36 players, including many Grand Slam champions and former number ones. The biggest barrier to 'Elite' status for a few of the players in this group was longevity within the top-10.

![Cluster B career plot](/images/tennis-clusters/cluster-b-plot.png)
*Remember the axis: Age v Rank*

![Cluster B comparison](/images/tennis-clusters/cluster-b-chart1.png)
*Remember, Borg and Roddick were in group A.*

![Cluster B chart](/images/tennis-clusters/cluster-b-chart2.png)

Wilander may have the strongest argument of all to join the first group. Entering the top-10 as a teen, like Borg, he stayed there for several years, capturing seven grand slams along the way. The six year stretch from 1982-1988 was incredible. The main deterrent to his inclusion in the top group would be the fact he was on the decline by the age of 24.

Vilas also has a case. He won four majors and was a dominant force on tour in the 70's. Playing long into the 80's, Vilas continued to have success late in his career on clay. Like Wilander, he was a Wimbledon away from a career grand slam.

The player who personifies this group as a whole turns out to be Tim Henman. While not a Grand Slam champion, Henman was a staple of the top-20.

This group has many players like Henman, who reach the top-20 or 50, hang around a bit, stay in the top-100 a few years then retire. Household names and Tennis Hall-of-Famers, they just barely make the top cut.

## C. The Bouncers

**Players in Cluster: 33. Most Representative Player: Nicolas Almagro**

Cluster C is unique because most of the players spent their careers almost evenly between the 11-20, 21-50, 51-100 and 100+ ranges. Sure they sometimes had a taste of the top-10, but most of the time they were elsewhere.

![Cluster C player list](/images/tennis-clusters/cluster-c-list.png)

Nicolas Almagro is the perfect example of this group, spending a few years outside the top-100 before making his slow descent into the top-20, then bouncing back up into the 51-100 range.

![Cluster C career plot](/images/tennis-clusters/cluster-c-plot.png)

Almagro, Monfils, Fognini and Cilic are the new breed of this kind of career -- flashes of brilliance, scattered seasons rolling up and down the top-100.

## D. The Almost Famous

**Players in Cluster: 47. Most Representative Player: Jiri Novak**

I call the next group, cluster D, The Almost Famous, where players on average spent over 60% of their careers in the top-50, but the majority of that was between 21-50. A couple of players stick out because they were famous, but the Open Era started later in their careers.

![Cluster D player list](/images/tennis-clusters/cluster-d-list.png)

Specifically, Smith, Lutz and Dent were famous. However, Smith was 26 when 1972 ended and thus missing a few of his best years in the data. The other two are better known for their doubles acumen.

The rest of this cluster includes players who made a run here and there and had fantastic careers, but for the most part were always just right on the cusp. Jiri Novak was the most representative of this group of 47 players. The group of Krickstein, Santoro, Chesnokov, Nieminen and Ljubicic are classic examples, peaking 25-27, but surrounded by unpredictable movements.

![Cluster D career plot](/images/tennis-clusters/cluster-d-plot.png)

## E. The Popcorn

**Players in Cluster: 45. Most Representative Player: Dmitry Tursunov**

With cluster E, we get a group which has many similarities to clusters C, D and F, but where the players tended to spend more time outside the top-100 than any other group. They also averaged about a third of their careers in each of the 21-50, 51-100 and 101+ ranges.

![Cluster E player list](/images/tennis-clusters/cluster-e-list.png)

Dmitry Tursunov is the poster child for this group. When you look at the plots of their careers, they tend to be really jagged lines, like popcorn popping and falling.

![Cluster E career plot](/images/tennis-clusters/cluster-e-plot.png)

Mardy Fish, James Blake and Rainer Schuettler fall into this one as well and show how their careers, despite having some fantastic seasons, had their challenges.

## F. The Grinders

**Players in Cluster: 43. Most Representative Player: Horacio de la Pena**

At the far end of the spectrum would be Cluster F, where players spent less than 4% within the top-20 and almost 80% outside the top-50. They spent about a third of their careers even outside the top-100.

![Cluster F player list](/images/tennis-clusters/cluster-f-list.png)

These are your Grand Slam draw mainstays, who tend to appear in the first and second round. A solid career and quite a few household names sprinkle this list of 43 players.

![Cluster F career plot](/images/tennis-clusters/cluster-f-plot.png)

Some may grace the top-20 but most appear in the top-100. Some struggle to stay in the top-100. That's the life of a grinder on tour. Not to say none of these men never were successful. Remember, the prerequisite to even make this list is that you had to have eight years of finishing in the top-100 in the world. That by any measure is a wonderful accomplishment.

Horacio de la Pena is the player that best represents this group. A player that bounced between 50 and 150 throughout his career, de la Pena won several titles and reached a career-high 31.

## Final Thoughts

![Final chart](/images/tennis-clusters/final-chart.png)

Like all analysis, this type is not perfect, but it does present some solid groupings of similar players. The best part of doing this level of analysis is to promote the discussion, remember a few forgotten players from over the years, or if you did not know a player, discover them for the first time and their place in the tennis history.

---

*Granger Huntress is a former tennis player, who now spends his days looking at data. He spent 11 years working in the tennis industry, with the USTA in Texas and for the University of Texas. He is also behind the twitter accounts, @txcollege10s and @th3srt1ngth30ry. Huntress started the website texascollegetennis.com, where he created rankings independent of the ITA for several years and thestringtheory.net, where he attempted to explain the ITF ProCircuits.*

*An ITF junkie, he once attended 11 professional events in a single year. He even attempted to qualify for two events at the age of 39. Despite being the top-ranked player in Texas at the time in the Men's 35 and over division, his dream was crushed, 6-0 6-0, by then WR 514 Ryan Newport.*

---

*Originally published on [Medium - The Tennis Notebook](https://medium.com/the-tennis-notebook/who-are-the-greatest-players-in-the-open-era-e7af7f627cc5). Special thanks to Jeff Sackmann of Tennis Abstract and Greg Sharko (ATP) for helping find the missing pieces of the year-end ATP ranks.*
