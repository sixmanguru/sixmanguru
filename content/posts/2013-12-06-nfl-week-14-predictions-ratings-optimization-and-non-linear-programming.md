---
title: "NFL Week 14 Predictions, Ratings, Optimization and Non-Linear Programming"
date: 2013-12-06T21:29:01+00:00
slug: "nfl-week-14-predictions-ratings-optimization-and-non-linear-programming"
author: "sixmanguru"
draft: false
tags:
  - "Optimization"
  - "non-linear prgramming"
  - "NFL"
  - "NLP"
  - "Football"
---

<!-- AdSense Now! V3.40 -->
<!-- Post[count: 1] -->
<div class="adsense adsense-leadin" style="float:right;margin: 12px;">
<!-- Guru2013 -->

</div><p>We finished classes yesterday, so all that is left for the semester is a homework assignment, three projects and three more exams. I have whittled this away to only needing to complete one last project and study for the exams. But, instead of finishing my database project, which is due Sunday, I elected to take a deeper dive into a classroom example for an exam I had yesterday.</p>
<p>They are not totally unrelated. The third db project involves converting the current NFL season data (mostly scores and teams) into a graph database model, but more on that at a later date.</p>
<p>While formatting the data, I was reminded of an example we worked in Optimization class Monday. The problem involved calculating NFL team ratings using Non-Linear Programming methods (<strong>with Excel</strong>). The example comes from our textbook, <em><strong>Practical Management Science</strong></em> by Winston and Albright (South-Western Cengage Learning, 4th Ed.).</p>
<p><strong>What is Non-Linear Programming?</strong></p>
<p>Almost verbatim from the book: It is the solving of an optimization problem where the objective or constraints are non-linear functions of the decision variables.</p>
<p>For the layman: It is a problem where there is an objective, but it is constrained by variables, which cannot be represented by simple straight lines. If you are interested or confused, there is plenty out there to help you understand Linear Programming (start with, <a href="http://en.wikipedia.org/wiki/Linear_programming">http://en.wikipedia.org/wiki/Linear_programming</a>).</p>
<p>The jump from linear to non-linear can be something simple. I like their revenue example, where revenue is a price multiplied by quantity sold. Well, quantity sold is a function of price, via a demand function. So revenue is price multiplied by a function of price. Even if demand is linear in price, the product of price and demand is quadratic because it includes a squared price.</p>
<p><strong>BACK TO FOOTBALL-THE PROBLEM</strong><br/>
The objective was to use NLP to create ratings for NFL teams that best predict the actual point spreads. By point spreads, they mean the actual score differential, not the betting lines.</p>
<p>As you may know, I have a little experience in this. In 1993, I created my own version of this and have applied it to both high school football (<a href="http://www.sixmanfootball.com/">www.sixmanfootball.com</a>) and college tennis (<a href="http://www.texascollegetennis.com/">www.texascollegetennis.com</a>). The basics of my programs use much of the same logic, but are more iterative and detailed.</p>
<p>In the classroom example, we set up the spreadsheet the following way.</p>
<p>First you create a table of team names and ratings. The ratings can be left blank or given any number, as they will be the values the Solver will change to meet our constraints. Somewhere near there, you can also add a home field advantage cell and make that also a variable cell to be tested in the Solver.</p>
<p>Next you create a table of played games, including home team, visiting team, home score and visitor score. From this you get what they call the point spread (score differential).</p>
<p>Extending that table, you create an expected point spread = home team rating – visiting team rating + home field advantage. Remember these are the variables that will be manipulated.</p>
<p>Again you extend that table, adding a squared predicted error value = (actual point spread (score differential) – predicted point spread) ^ 2 (squared).</p>
<p>Now you need to create a few constraints. The first is the objective. Yes, the ratings are our objective, but we want them to be optimized. To do this, we set the objective as being the sum of errors or to be more precise, the sum of squared errors. We want to minimize this.</p>
<p>Why squared errors? I think they gloss over this in the book, stating this is just has a long tradition in statistics. Yes, you can use the sum of absolute (value) errors as well. Like the authors, I prefer squared errors.</p>
<p>Think of it this way, when you get a big difference (error), like 10, the squared error is 100. When you get an error of 5, the squared error is only 25. I look at squared errors as a way to ‘punish’ the larger errors, bringing the results even tighter.</p>
<p>The final part of setting up the model is to set a boundary or what the authors term normalizing the data, so you only get one result. If you do not do this, there will not be a single unique answer. The idea is to bound the mean of the ratings to some number. They use 85, as that is what Jeff Sagarin does. Part of the logic is that a perfect team would approach 100, which seems like a pretty logical thing to people to understand. In my example, I used 20. This makes the results look more like football scores. I wouldn’t normally do this, but the variance in NFL scores is pretty tight.</p>
<p><strong>THE SOLUTION-2013 WEEK 14</strong><br/>
Instead of running the 2003 or 2009 data, as we did in class. I came across the current 2013 data. Once you have the data, it really only takes a second and boom, you get ratings. I even added last night’s Jags-Texans game.</p>
<p>Here’s a sample of what you get.</p>
<p>1 Seattle Seahawks 33.28<br/>
2 Carolina Panthers 31.55<br/>
3 Denver Broncos 31.37<br/>
4 San Francisco 49ers 29.56<br/>
5 New Orleans Saints 27.49</p>
<p><strong>So what does this mean?</strong></p>
<p>If the Seahawks played the Saints on a neutral field, they should be about a 5.5-point favorite (33.28-27.49).</p>
<p><strong>An even better question – How can we use this?</strong></p>
<p>Well, I just happen to have the current betting lines (from sportbook.com), so let’s compare.</p>
<table align="left" border="0" cellpadding="0" cellspacing="0">
<tbody>
<tr>
<td valign="top" width="95">Visitor</td>
<td valign="top" width="33">V-Rat</td>
<td valign="top" width="105">Home</td>
<td valign="top" width="33">H-Rat</td>
<td valign="top" width="27">Line</td>
<td valign="top" width="40">Exp</td>
<td valign="top" width="40">
<p align="center">Diff (raw)</p>
</td>
<td valign="top" width="40">
<p align="center">Diff/Line</p>
</td>
</tr>
<tr>
<td valign="top" width="95">Kansas City Chiefs</td>
<td valign="top" width="33">
<p align="center">25.24</p>
</td>
<td valign="top" width="105">Washington Redskins</td>
<td valign="top" width="33">
<p align="center">12.55</p>
</td>
<td valign="top" width="27">
<p align="center">-3.5</p>
</td>
<td valign="top" width="40">
<p align="center">-9.75</p>
</td>
<td valign="top" width="40">
<p align="center">6.25</p>
</td>
<td valign="top" width="40">
<p align="center">-179%</p>
</td>
</tr>
<tr>
<td valign="top" width="95">Minnesota Vikings</td>
<td valign="top" width="33">
<p align="center">13.30</p>
</td>
<td valign="top" width="105">Baltimore Ravens</td>
<td valign="top" width="33">
<p align="center">18.61</p>
</td>
<td valign="top" width="27">
<p align="center">7</p>
</td>
<td valign="top" width="40">
<p align="center">8.26</p>
</td>
<td valign="top" width="40">
<p align="center">-1.26</p>
</td>
<td valign="top" width="40">
<p align="center">-18%</p>
</td>
</tr>
<tr>
<td valign="top" width="95">Cleveland Browns</td>
<td valign="top" width="33">
<p align="center">12.72</p>
</td>
<td valign="top" width="105">New England Patriots</td>
<td valign="top" width="33">
<p align="center">24.62</p>
</td>
<td valign="top" width="27">
<p align="center">13</p>
</td>
<td valign="top" width="40">
<p align="center">14.84</p>
</td>
<td valign="top" width="40">
<p align="center">-1.84</p>
</td>
<td valign="top" width="40">
<p align="center">-14%</p>
</td>
</tr>
<tr>
<td valign="top" width="95">Oakland Raiders</td>
<td valign="top" width="33">
<p align="center">13.73</p>
</td>
<td valign="top" width="105">New York Jets</td>
<td valign="top" width="33">
<p align="center">10.07</p>
</td>
<td valign="top" width="27">
<p align="center">2.5</p>
</td>
<td valign="top" width="40">
<p align="center">-0.72</p>
</td>
<td valign="top" width="40">
<p align="center">3.22</p>
</td>
<td valign="top" width="40">
<p align="center">129%</p>
</td>
</tr>
<tr>
<td valign="top" width="95">Indianapolis Colts</td>
<td valign="top" width="33">
<p align="center">22.23</p>
</td>
<td valign="top" width="105">Cincinnati Bengals</td>
<td valign="top" width="33">
<p align="center">24.20</p>
</td>
<td valign="top" width="27">
<p align="center">6.5</p>
</td>
<td valign="top" width="40">
<p align="center">4.92</p>
</td>
<td valign="top" width="40">
<p align="center">1.58</p>
</td>
<td valign="top" width="40">
<p align="center">24%</p>
</td>
</tr>
<tr>
<td valign="top" width="95">Carolina Panthers</td>
<td valign="top" width="33">
<p align="center">31.55</p>
</td>
<td valign="top" width="105">New Orleans Saints</td>
<td valign="top" width="33">
<p align="center">27.49</p>
</td>
<td valign="top" width="27">
<p align="center">3.5</p>
</td>
<td valign="top" width="40">
<p align="center">-1.11</p>
</td>
<td valign="top" width="40">
<p align="center">4.61</p>
</td>
<td valign="top" width="40">
<p align="center">132%</p>
</td>
</tr>
<tr>
<td valign="top" width="95">Detroit Lions</td>
<td valign="top" width="33">
<p align="center">21.09</p>
</td>
<td valign="top" width="105">Philadelphia Eagles</td>
<td valign="top" width="33">
<p align="center">20.60</p>
</td>
<td valign="top" width="27">
<p align="center">3</p>
</td>
<td valign="top" width="40">
<p align="center">2.45</p>
</td>
<td valign="top" width="40">
<p align="center">0.55</p>
</td>
<td valign="top" width="40">
<p align="center">18%</p>
</td>
</tr>
<tr>
<td valign="top" width="95">Miami Dolphins</td>
<td valign="top" width="33">
<p align="center">20.43</p>
</td>
<td valign="top" width="105">Pittsburgh Steelers</td>
<td valign="top" width="33">
<p align="center">16.77</p>
</td>
<td valign="top" width="27">
<p align="center">3.5</p>
</td>
<td valign="top" width="40">
<p align="center">-0.71</p>
</td>
<td valign="top" width="40">
<p align="center">4.21</p>
</td>
<td valign="top" width="40">
<p align="center">120%</p>
</td>
</tr>
<tr>
<td valign="top" width="95">Buffalo Bills</td>
<td valign="top" width="33">
<p align="center">16.00</p>
</td>
<td valign="top" width="105">Tampa Bay Buccaneers</td>
<td valign="top" width="33">
<p align="center">17.43</p>
</td>
<td valign="top" width="27">
<p align="center">3</p>
</td>
<td valign="top" width="40">
<p align="center">4.37</p>
</td>
<td valign="top" width="40">
<p align="center">-1.37</p>
</td>
<td valign="top" width="40">
<p align="center">-46%</p>
</td>
</tr>
<tr>
<td valign="top" width="95">Tennessee Titans</td>
<td valign="top" width="33">
<p align="center">19.51</p>
</td>
<td valign="top" width="105">Denver Broncos</td>
<td valign="top" width="33">
<p align="center">31.37</p>
</td>
<td valign="top" width="27">
<p align="center">13</p>
</td>
<td valign="top" width="40">
<p align="center">14.80</p>
</td>
<td valign="top" width="40">
<p align="center">-1.80</p>
</td>
<td valign="top" width="40">
<p align="center">-14%</p>
</td>
</tr>
<tr>
<td valign="top" width="95">St Louis Rams</td>
<td valign="top" width="33">
<p align="center">22.39</p>
</td>
<td valign="top" width="105">Arizona Cardinals</td>
<td valign="top" width="33">
<p align="center">24.27</p>
</td>
<td valign="top" width="27">
<p align="center">6</p>
</td>
<td valign="top" width="40">
<p align="center">4.83</p>
</td>
<td valign="top" width="40">
<p align="center">1.17</p>
</td>
<td valign="top" width="40">
<p align="center">19%</p>
</td>
</tr>
<tr>
<td valign="top" width="95">New York Giants</td>
<td valign="top" width="33">
<p align="center">15.71</p>
</td>
<td valign="top" width="105">San Diego Chargers</td>
<td valign="top" width="33">
<p align="center">20.12</p>
</td>
<td valign="top" width="27">
<p align="center">3.5</p>
</td>
<td valign="top" width="40">
<p align="center">7.35</p>
</td>
<td valign="top" width="40">
<p align="center">-3.85</p>
</td>
<td valign="top" width="40">
<p align="center">-110%</p>
</td>
</tr>
<tr>
<td valign="top" width="95">Seattle Seahawks</td>
<td valign="top" width="33">
<p align="center">33.28</p>
</td>
<td valign="top" width="105">San Francisco 49ers</td>
<td valign="top" width="33">
<p align="center">29.56</p>
</td>
<td valign="top" width="27">
<p align="center">2.5</p>
</td>
<td valign="top" width="40">
<p align="center">-0.78</p>
</td>
<td valign="top" width="40">
<p align="center">3.28</p>
</td>
<td valign="top" width="40">
<p align="center">131%</p>
</td>
</tr>
<tr>
<td valign="top" width="95">Dallas Cowboys</td>
<td valign="top" width="33">
<p align="center">22.11</p>
</td>
<td valign="top" width="105">Chicago Bears</td>
<td valign="top" width="33">
<p align="center">17.92</p>
</td>
<td valign="top" width="27">
<p align="center">-1</p>
</td>
<td valign="top" width="40">
<p align="center">-1.25</p>
</td>
<td valign="top" width="40">
<p align="center">0.25</p>
</td>
<td valign="top" width="40">
<p align="center">-25%</p>
</td>
</tr>
</tbody>
</table>
<p>OK, now what does this mean?</p>
<p>Take it for what you want, but it appears to show us a few big differences between the betting lines and our programs’ expected lines. So we should bet, right? Not so fast my friends.</p>
<p>It appears the guys making the lines are fading on Kansas City, based on three straight losses. A team that looks like almost a 10-point favorite (even on the road) in our system, is only giving 3.5 points.</p>
<p>Another scary game would be Carolina getting 3.5 points at New Orleans. The system says the Panthers SHOULD actually be giving a point, instead of getting 3.5. I think the line of thinking goes that maybe the New Orleans home field advantage is worth a little more than the 2.9 points our system. New Orleans is also what the bettors term a very ‘Public’ team, meaning they are very popular among the casual bettors, compared to Carolina. This may skew the line even further.</p>
<p>Now to really get into evaluation a bit more (and avoid my project as well) I decided to go back a week and see how things worked out last week, based on last week’s ratings.</p>
<table border="0" cellpadding="0" cellspacing="0">
<tbody>
<tr>
<td valign="top" width="119">Visitor</td>
<td valign="top" width="40">V-Rat</td>
<td valign="top" width="119">Home</td>
<td valign="top" width="40">
<p align="center">H-Rat</p>
</td>
<td valign="top" width="27">
<p align="center">Line</p>
</td>
<td valign="top" width="40">
<p align="center">Exp</p>
</td>
<td valign="top" width="40">
<p align="center">Diff (raw)</p>
</td>
<td valign="top" width="40">
<p align="center">Diff/line</p>
</td>
<td valign="top" width="17">
<p align="center">V</p>
</td>
<td valign="top" width="17">
<p align="center">H</p>
</td>
<td valign="top" width="40">
<p align="center">Correct</p>
</td>
</tr>
<tr>
<td valign="top" width="119">Green Bay Packers</td>
<td valign="top" width="40">
<p align="right">19.65</p>
</td>
<td valign="top" width="119">Detroit Lions</td>
<td valign="top" width="40">
<p align="center">19.44</p>
</td>
<td valign="top" width="27">
<p align="center">6</p>
</td>
<td valign="top" width="40">
<p align="center">2.59</p>
</td>
<td valign="top" width="40">
<p align="center">3.41</p>
</td>
<td valign="top" width="40">
<p align="center">57%</p>
</td>
<td valign="top" width="17">
<p align="center">10</p>
</td>
<td valign="top" width="17">
<p align="center">40</p>
</td>
<td valign="top" width="40">
<p align="center">0</p>
</td>
</tr>
<tr>
<td valign="top" width="119">Oakland Raiders</td>
<td valign="top" width="40">
<p align="right">12.96</p>
</td>
<td valign="top" width="119">Dallas Cowboys</td>
<td valign="top" width="40">
<p align="center">22.35</p>
</td>
<td valign="top" width="27">
<p align="center">8</p>
</td>
<td valign="top" width="40">
<p align="center">12.18</p>
</td>
<td valign="top" width="40">
<p align="center">-4.18</p>
</td>
<td valign="top" width="40">
<p align="center">-52%</p>
</td>
<td valign="top" width="17">
<p align="center">24</p>
</td>
<td valign="top" width="17">
<p align="center">31</p>
</td>
<td valign="top" width="40">
<p align="center">0</p>
</td>
</tr>
<tr>
<td valign="top" width="119">Pittsburgh Steelers</td>
<td valign="top" width="40">
<p align="right">16.89</p>
</td>
<td valign="top" width="119">Baltimore Ravens</td>
<td valign="top" width="40">
<p align="center">19.52</p>
</td>
<td valign="top" width="27">
<p align="center">3</p>
</td>
<td valign="top" width="40">
<p align="center">5.42</p>
</td>
<td valign="top" width="40">
<p align="center">-2.42</p>
</td>
<td valign="top" width="40">
<p align="center">-81%</p>
</td>
<td valign="top" width="17">
<p align="center">20</p>
</td>
<td valign="top" width="17">
<p align="center">22</p>
</td>
<td valign="top" width="40">
<p align="center">0</p>
</td>
</tr>
<tr>
<td valign="top" width="119">Tennessee Titans</td>
<td valign="top" width="40">
<p align="right">19.25</p>
</td>
<td valign="top" width="119">Indianapolis Colts</td>
<td valign="top" width="40">
<p align="center">21.25</p>
</td>
<td valign="top" width="27">
<p align="center">3.5</p>
</td>
<td valign="top" width="40">
<p align="center">4.79</p>
</td>
<td valign="top" width="40">
<p align="center">-1.29</p>
</td>
<td valign="top" width="40">
<p align="center">-37%</p>
</td>
<td valign="top" width="17">
<p align="center">14</p>
</td>
<td valign="top" width="17">
<p align="center">22</p>
</td>
<td valign="top" width="40">
<p align="center">1</p>
</td>
</tr>
<tr>
<td valign="top" width="119">Denver Broncos</td>
<td valign="top" width="40">
<p align="right">30.86</p>
</td>
<td valign="top" width="119">Kansas City Chiefs</td>
<td valign="top" width="40">
<p align="center">25.41</p>
</td>
<td valign="top" width="27">
<p align="center">-6</p>
</td>
<td valign="top" width="40">
<p align="center">-2.65</p>
</td>
<td valign="top" width="40">
<p align="center">-3.35</p>
</td>
<td valign="top" width="40">
<p align="center">56%</p>
</td>
<td valign="top" width="17">
<p align="center">35</p>
</td>
<td valign="top" width="17">
<p align="center">28</p>
</td>
<td valign="top" width="40">
<p align="center">1</p>
</td>
</tr>
<tr>
<td valign="top" width="119">Jacksonville Jaguars</td>
<td valign="top" width="40">
<p align="right">6.31</p>
</td>
<td valign="top" width="119">Cleveland Browns</td>
<td valign="top" width="40">
<p align="center">14.05</p>
</td>
<td valign="top" width="27">
<p align="center">7.5</p>
</td>
<td valign="top" width="40">
<p align="center">10.54</p>
</td>
<td valign="top" width="40">
<p align="center">-3.04</p>
</td>
<td valign="top" width="40">
<p align="center">-40%</p>
</td>
<td valign="top" width="17">
<p align="center">32</p>
</td>
<td valign="top" width="17">
<p align="center">28</p>
</td>
<td valign="top" width="40">
<p align="center">0</p>
</td>
</tr>
<tr>
<td valign="top" width="119">Tampa Bay Buccaneers</td>
<td valign="top" width="40">
<p align="right">17.70</p>
</td>
<td valign="top" width="119">Carolina Panthers</td>
<td valign="top" width="40">
<p align="center">30.95</p>
</td>
<td valign="top" width="27">
<p align="center">6.5</p>
</td>
<td valign="top" width="40">
<p align="center">16.05</p>
</td>
<td valign="top" width="40">
<p align="center">-9.55</p>
</td>
<td valign="top" width="40">
<p align="center">-147%</p>
</td>
<td valign="top" width="17">
<p align="center">6</p>
</td>
<td valign="top" width="17">
<p align="center">27</p>
</td>
<td valign="top" width="40">
<p align="center">1</p>
</td>
</tr>
<tr>
<td valign="top" width="119">Chicago Bears</td>
<td valign="top" width="40">
<p align="right">18.47</p>
</td>
<td valign="top" width="119">Minnesota Vikings</td>
<td valign="top" width="40">
<p align="center">13.05</p>
</td>
<td valign="top" width="27">
<p align="center">1</p>
</td>
<td valign="top" width="40">
<p align="center">-2.62</p>
</td>
<td valign="top" width="40">
<p align="center">3.62</p>
</td>
<td valign="top" width="40">
<p align="center">362%</p>
</td>
<td valign="top" width="17">
<p align="center">20</p>
</td>
<td valign="top" width="17">
<p align="center">23</p>
</td>
<td valign="top" width="40">
<p align="center">0</p>
</td>
</tr>
<tr>
<td valign="top" width="119">Arizona Cardinals</td>
<td valign="top" width="40">
<p align="right">23.99</p>
</td>
<td valign="top" width="119">Philadelphia Eagles</td>
<td valign="top" width="40">
<p align="center">20.40</p>
</td>
<td valign="top" width="27">
<p align="center">3.5</p>
</td>
<td valign="top" width="40">
<p align="center">-0.80</p>
</td>
<td valign="top" width="40">
<p align="center">4.30</p>
</td>
<td valign="top" width="40">
<p align="center">123%</p>
</td>
<td valign="top" width="17">
<p align="center">21</p>
</td>
<td valign="top" width="17">
<p align="center">24</p>
</td>
<td valign="top" width="40">
<p align="center">1</p>
</td>
</tr>
<tr>
<td valign="top" width="119">Miami Dolphins</td>
<td valign="top" width="40">
<p align="right">19.78</p>
</td>
<td valign="top" width="119">New York Jets</td>
<td valign="top" width="40">
<p align="center">11.89</p>
</td>
<td valign="top" width="27">
<p align="center">2</p>
</td>
<td valign="top" width="40">
<p align="center">-5.09</p>
</td>
<td valign="top" width="40">
<p align="center">7.09</p>
</td>
<td valign="top" width="40">
<p align="center">355%</p>
</td>
<td valign="top" width="17">
<p align="center">23</p>
</td>
<td valign="top" width="17">
<p align="center">3</p>
</td>
<td valign="top" width="40">
<p align="center">1</p>
</td>
</tr>
<tr>
<td valign="top" width="119">Atlanta Falcons</td>
<td valign="top" width="40">
<p align="right">15.88</p>
</td>
<td valign="top" width="119">Buffalo Bills</td>
<td valign="top" width="40">
<p align="center">17.29</p>
</td>
<td valign="top" width="27">
<p align="center">4.5</p>
</td>
<td valign="top" width="40">
<p align="center">4.20</p>
</td>
<td valign="top" width="40">
<p align="center">0.30</p>
</td>
<td valign="top" width="40">
<p align="center">7%</p>
</td>
<td valign="top" width="17">
<p align="center">34</p>
</td>
<td valign="top" width="17">
<p align="center">31</p>
</td>
<td valign="top" width="40">
<p align="center">1</p>
</td>
</tr>
<tr>
<td valign="top" width="119">St Louis Rams</td>
<td valign="top" width="40">
<p align="right">21.78</p>
</td>
<td valign="top" width="119">San Francisco 49ers</td>
<td valign="top" width="40">
<p align="center">29.29</p>
</td>
<td valign="top" width="27">
<p align="center">7.5</p>
</td>
<td valign="top" width="40">
<p align="center">10.30</p>
</td>
<td valign="top" width="40">
<p align="center">-2.80</p>
</td>
<td valign="top" width="40">
<p align="center">-37%</p>
</td>
<td valign="top" width="17">
<p align="center">13</p>
</td>
<td valign="top" width="17">
<p align="center">23</p>
</td>
<td valign="top" width="40">
<p align="center">1</p>
</td>
</tr>
<tr>
<td valign="top" width="119">New England Patriots</td>
<td valign="top" width="40">
<p align="right">25.66</p>
</td>
<td valign="top" width="119">Houston Texans</td>
<td valign="top" width="40">
<p align="center">12.56</p>
</td>
<td valign="top" width="27">
<p align="center">-6.5</p>
</td>
<td valign="top" width="40">
<p align="center">-10.30</p>
</td>
<td valign="top" width="40">
<p align="center">3.80</p>
</td>
<td valign="top" width="40">
<p align="center">-58%</p>
</td>
<td valign="top" width="17">
<p align="center">34</p>
</td>
<td valign="top" width="17">
<p align="center">31</p>
</td>
<td valign="top" width="40">
<p align="center">1</p>
</td>
</tr>
<tr>
<td valign="top" width="119">Cincinnati Bengals</td>
<td valign="top" width="40">
<p align="right">24.41</p>
</td>
<td valign="top" width="119">San Diego Chargers</td>
<td valign="top" width="40">
<p align="center">20.14</p>
</td>
<td valign="top" width="27">
<p align="center">-1.5</p>
</td>
<td valign="top" width="40">
<p align="center">-1.47</p>
</td>
<td valign="top" width="40">
<p align="center">-0.03</p>
</td>
<td valign="top" width="40">
<p align="center">2%</p>
</td>
<td valign="top" width="17">
<p align="center">17</p>
</td>
<td valign="top" width="17">
<p align="center">10</p>
</td>
<td valign="top" width="40">
<p align="center">1</p>
</td>
</tr>
<tr>
<td valign="top" width="119">New York Giants</td>
<td valign="top" width="40">
<p align="right">15.19</p>
</td>
<td valign="top" width="119">Washington Redskins</td>
<td valign="top" width="40">
<p align="center">13.07</p>
</td>
<td valign="top" width="27">
<p align="center">1</p>
</td>
<td valign="top" width="40">
<p align="center">0.68</p>
</td>
<td valign="top" width="40">
<p align="center">0.32</p>
</td>
<td valign="top" width="40">
<p align="center">32%</p>
</td>
<td valign="top" width="17">
<p align="center">24</p>
</td>
<td valign="top" width="17">
<p align="center">17</p>
</td>
<td valign="top" width="40">
<p align="center">1</p>
</td>
</tr>
<tr>
<td valign="top" width="119">New Orleans Saints</td>
<td valign="top" width="40">
<p align="right">29.49</p>
</td>
<td valign="top" width="119">Seattle Seahawks</td>
<td valign="top" width="40">
<p align="center">31.07</p>
</td>
<td valign="top" width="27">
<p align="center">5</p>
</td>
<td valign="top" width="40">
<p align="center">4.38</p>
</td>
<td valign="top" width="40">
<p align="center">0.62</p>
</td>
<td valign="top" width="40">
<p align="center">12%</p>
</td>
<td valign="top" width="17">
<p align="center">7</p>
</td>
<td valign="top" width="17">
<p align="center">34</p>
</td>
<td valign="top" width="40">
<p align="center">0</p>
</td>
</tr>
</tbody>
</table>
<p>Now we are getting somewhere. The system actually went 10-5. In games where the expected vs line was greater (or less) than 100%, it went 3-1. Hmmm. In games where the absolute raw was greater than 2.5, it was 6-4.</p>
<p>So, the system says we should probably look again at the big differences.</p>
<p>Maybe we should consider taking Kansas City, Oakland, Carolina, Miami, San Diego and Seattle? A $5 wager would bring you $242.92 in winnings, if they ALL beat the spread.</p>
<p>I’m a little concerned about too many road teams. How about we drop it to KC, Oakland, Miami and San Diego? If you bet $5 here, you win $61.52 if they all win. Sounds good. Done. We will send Prof. Muthuraman a little something if we hit.</p>
<!-- AdSense Now! V3.40 -->
<!-- Post[count: 2] -->
<div class="adsense adsense-leadout" style="text-align:center;margin: 12px;">
<!-- Guru2013 -->

</div>
