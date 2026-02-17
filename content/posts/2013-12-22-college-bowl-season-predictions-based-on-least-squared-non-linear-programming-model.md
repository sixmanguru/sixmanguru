---
title: "College Bowl Season Predictions Based on Least Squared Non-Linear Programming Model"
date: 2013-12-22T03:45:12+00:00
slug: "college-bowl-season-predictions-based-on-least-squared-non-linear-programming-model"
author: "granger"
draft: false
tags:
  - "non-linear programming"
  - "least squares"
  - "College Football"
  - "Optimization"
  - "Gurobi"
  - "Football"
  - "NLP"
  - "gambling"
---

<p>There’s no shortage of data out there when it comes to college football, so I decided to take the time to create a least squares model, based on the same principals I have been using for the NFL, and <a href="http://www.sixmanguru.com/nfl-week-14-predictions-ratings-optimization-and-non-linear-programming/">outlined here</a>.</p>
<p>The idea was to take all 752 schools that played college football, cross that with all 4138 games that were played (up to last weekend) and see how they predict the games (especially versus the Vegas lines).</p>
<p>When you try to create a model with 753 variables (I also included home field advantage for the regular season games as a variable), you quickly begin to test the limitations of Excel and Solver. After a little digging, I discovered that <a href="http://www.solver.com/">Frontline Solver</a>, the company that developed Solver for Excel, limits the version included with the Microsoft product to 200 variables.</p>
<p>Not to be stopped, I found they have some advanced pro models and engines that will handle significantly more and downloaded a 16-day trial of these.</p>
<p>You set it to pick the best engine and it runs. For this particular problem, it happened to run the <a href="http://en.wikipedia.org/wiki/Gurobi">Gurobi Optimization</a> engine.</p>
<p>From there, it is fairly plain and simple. You run the solver and it calculates a ranking for each team. I just plugged in the bowl games and here’s what we get.</p>
<table cellpadding="0" cellspacing="0">
<tbody>
<tr>
<td valign="middle"><strong>Team A</strong></td>
<td valign="middle"><strong>Team B</strong></td>
<td valign="middle"><strong>Exp</strong></td>
<td valign="middle"><strong>Vegas</strong></td>
<td valign="middle"><strong>Diff</strong></td>
<td valign="middle"><strong>% Diff</strong></td>
</tr>
<tr>
<td valign="middle">Colorado State</td>
<td valign="middle">Washington St</td>
<td valign="middle">7.68</td>
<td valign="middle">5.5</td>
<td valign="middle">2.18</td>
<td valign="middle">40%</td>
</tr>
<tr>
<td valign="middle">Southern Cal</td>
<td valign="middle">Fresno State</td>
<td valign="middle">-8.22</td>
<td valign="middle">-5</td>
<td valign="middle">-3.22</td>
<td valign="middle">64%</td>
</tr>
<tr>
<td valign="middle">Buffalo</td>
<td valign="middle">San Diego St</td>
<td valign="middle">-6.86</td>
<td valign="middle">-1.5</td>
<td valign="middle">-5.36</td>
<td valign="middle">357%</td>
</tr>
<tr>
<td valign="middle">Louisiana-Lafayette</td>
<td valign="middle">Tulane</td>
<td valign="middle">-0.67</td>
<td valign="middle">1.5</td>
<td valign="middle">-2.17</td>
<td valign="middle">-145%</td>
</tr>
<tr>
<td valign="middle">Ohio U.</td>
<td valign="middle">East Carolina</td>
<td valign="middle">16.48</td>
<td valign="middle">14</td>
<td valign="middle">2.48</td>
<td valign="middle">18%</td>
</tr>
<tr>
<td valign="middle">Oregon State</td>
<td valign="middle">Boise State</td>
<td valign="middle">-0.74</td>
<td valign="middle">-3.5</td>
<td valign="middle">2.76</td>
<td valign="middle">-79%</td>
</tr>
<tr>
<td valign="middle">Pittsburgh</td>
<td valign="middle">Bowling Green</td>
<td valign="middle">5.69</td>
<td valign="middle">5</td>
<td valign="middle">0.69</td>
<td valign="middle">14%</td>
</tr>
<tr>
<td valign="middle">Utah State</td>
<td valign="middle">Northern Illinois</td>
<td valign="middle">-5.46</td>
<td valign="middle">2</td>
<td valign="middle">-7.46</td>
<td valign="middle">-373%</td>
</tr>
<tr>
<td valign="middle">Marshall</td>
<td valign="middle">Maryland</td>
<td valign="middle">-5.11</td>
<td valign="middle">-2</td>
<td valign="middle">-3.11</td>
<td valign="middle">156%</td>
</tr>
<tr>
<td valign="middle">Syracuse</td>
<td valign="middle">Minnesota</td>
<td valign="middle">6.41</td>
<td valign="middle">5</td>
<td valign="middle">1.41</td>
<td valign="middle">28%</td>
</tr>
<tr>
<td valign="middle">Washington</td>
<td valign="middle">Brigham Young</td>
<td valign="middle">-8.75</td>
<td valign="middle">-3</td>
<td valign="middle">-5.75</td>
<td valign="middle">192%</td>
</tr>
<tr>
<td valign="middle">Rutgers</td>
<td valign="middle">Notre Dame</td>
<td valign="middle">20.75</td>
<td valign="middle">14</td>
<td valign="middle">6.75</td>
<td valign="middle">48%</td>
</tr>
<tr>
<td valign="middle">Cincinnati</td>
<td valign="middle">North Carolina</td>
<td valign="middle">5.93</td>
<td valign="middle">3</td>
<td valign="middle">2.93</td>
<td valign="middle">98%</td>
</tr>
<tr>
<td valign="middle">Miami FL</td>
<td valign="middle">Louisville</td>
<td valign="middle">3.60</td>
<td valign="middle">3.5</td>
<td valign="middle">0.10</td>
<td valign="middle">3%</td>
</tr>
<tr>
<td valign="middle">Michigan</td>
<td valign="middle">Kansas State</td>
<td valign="middle">3.23</td>
<td valign="middle">3.5</td>
<td valign="middle">-0.27</td>
<td valign="middle">-8%</td>
</tr>
<tr>
<td valign="middle">Middle Tennessee St.</td>
<td valign="middle">Navy</td>
<td valign="middle">9.60</td>
<td valign="middle">6</td>
<td valign="middle">3.60</td>
<td valign="middle">60%</td>
</tr>
<tr>
<td valign="middle">Mississippi</td>
<td valign="middle">Georgia Tech</td>
<td valign="middle">3.71</td>
<td valign="middle">-3.5</td>
<td valign="middle">7.21</td>
<td valign="middle">-206%</td>
</tr>
<tr>
<td valign="middle">Texas</td>
<td valign="middle">Oregon</td>
<td valign="middle">18.33</td>
<td valign="middle">14</td>
<td valign="middle">4.33</td>
<td valign="middle">31%</td>
</tr>
<tr>
<td valign="middle">Texas Tech</td>
<td valign="middle">Arizona St</td>
<td valign="middle">20.19</td>
<td valign="middle">14.5</td>
<td valign="middle">5.69</td>
<td valign="middle">39%</td>
</tr>
<tr>
<td valign="middle">Boston College</td>
<td valign="middle">Arizona</td>
<td valign="middle">12.46</td>
<td valign="middle">7.5</td>
<td valign="middle">4.96</td>
<td valign="middle">66%</td>
</tr>
<tr>
<td valign="middle">Virginia Tech</td>
<td valign="middle">UCLA</td>
<td valign="middle">11.22</td>
<td valign="middle">7.5</td>
<td valign="middle">3.72</td>
<td valign="middle">50%</td>
</tr>
<tr>
<td valign="middle">Mississippi State</td>
<td valign="middle">Rice</td>
<td valign="middle">-9.02</td>
<td valign="middle">-7</td>
<td valign="middle">-2.02</td>
<td valign="middle">29%</td>
</tr>
<tr>
<td valign="middle">Duke</td>
<td valign="middle">Texas A&amp;M</td>
<td valign="middle">9.69</td>
<td valign="middle">13</td>
<td valign="middle">-3.31</td>
<td valign="middle">-25%</td>
</tr>
<tr>
<td valign="middle">Nebraska</td>
<td valign="middle">Georgia</td>
<td valign="middle">10.82</td>
<td valign="middle">9</td>
<td valign="middle">1.82</td>
<td valign="middle">20%</td>
</tr>
<tr>
<td valign="middle">Nevada-Las Vegas</td>
<td valign="middle">North Texas</td>
<td valign="middle">7.91</td>
<td valign="middle">6.5</td>
<td valign="middle">1.41</td>
<td valign="middle">22%</td>
</tr>
<tr>
<td valign="middle">Wisconsin</td>
<td valign="middle">South Carolina</td>
<td valign="middle">-2.33</td>
<td valign="middle">0</td>
<td valign="middle">-2.33</td>
<td valign="middle">-233%</td>
</tr>
<tr>
<td valign="middle">Iowa</td>
<td valign="middle">LSU</td>
<td valign="middle">7.21</td>
<td valign="middle">8</td>
<td valign="middle">-0.79</td>
<td valign="middle">-10%</td>
</tr>
<tr>
<td valign="middle">Michigan State</td>
<td valign="middle">Stanford</td>
<td valign="middle">9.24</td>
<td valign="middle">6</td>
<td valign="middle">3.24</td>
<td valign="middle">54%</td>
</tr>
<tr>
<td valign="middle">Central Florida</td>
<td valign="middle">Baylor</td>
<td valign="middle">24.64</td>
<td valign="middle">17</td>
<td valign="middle">7.64</td>
<td valign="middle">45%</td>
</tr>
<tr>
<td valign="middle">Oklahoma</td>
<td valign="middle">Alabama</td>
<td valign="middle">14.31</td>
<td valign="middle">16</td>
<td valign="middle">-1.69</td>
<td valign="middle">-11%</td>
</tr>
<tr>
<td valign="middle">Oklahoma State</td>
<td valign="middle">Missouri</td>
<td valign="middle">-1.74</td>
<td valign="middle">1.5</td>
<td valign="middle">-3.24</td>
<td valign="middle">-216%</td>
</tr>
<tr>
<td valign="middle">Clemson</td>
<td valign="middle">Ohio State</td>
<td valign="middle">2.49</td>
<td valign="middle">2.5</td>
<td valign="middle">-0.01</td>
<td valign="middle">0%</td>
</tr>
<tr>
<td valign="middle">Houston</td>
<td valign="middle">Vanderbilt</td>
<td valign="middle">-5.73</td>
<td valign="middle">3</td>
<td valign="middle">-8.73</td>
<td valign="middle">-291%</td>
</tr>
<tr>
<td valign="middle">Arkansas St</td>
<td valign="middle">Ball St</td>
<td valign="middle">10.52</td>
<td valign="middle">9.5</td>
<td valign="middle">1.02</td>
<td valign="middle">11%</td>
</tr>
<tr>
<td valign="middle">Auburn</td>
<td valign="middle">Florida State</td>
<td valign="middle">19.81</td>
<td valign="middle">7.5</td>
<td valign="middle">12.31</td>
<td valign="middle">164%</td>
</tr>
</tbody>
</table>
<p>Here’s what the table means. Vegas has Auburn as a (+7.5) underdog to Florida State, however, the model shows FSU as an almost 20-point favorite, an almost 12-point difference.</p>
<p>One of the most interesting lines is Clemson as a 2.5-point underdog to Ohio State. The LS model has that game as a 2.49-point spread, almost exactly spot on.</p>
<p>Several others are extremely close like that: Miami-Louisville (3%), Michigan-Kansas State (8%), Iowa-LSU (10%), Oklahoma-Alabama (11%) and Arkansas State-Ball State (11%).</p>
<p>Here’s a quick rundown of which side the computer is on for each game (including the Vegas lines): Washington State (-5.5), USC (-5), Buffalo (-1.5), Louisiana-Lafayette (+1.5), East Carolina (-14), Boise State (+3.5), Bowling Green (-5), Utah State (+2), Marshall (-2), Minnesota (-5), Washington (-3), Notre Dame (-14), North Carolina (-3), Louisville (-3.5), Michigan (+3.5), Navy (-6), Georgia Tech (+3.5), Oregon (-14), Arizona State (-14.5), Arizona (-7.5), UCLA (-7.5), Mississippi State (-7), Duke (+13), Georgia (-9), North Texas (-6.5), Wisconsin (0), Iowa (+8), Stanford (-6), Baylor (-17), Oklahoma (+16), Oklahoma State (+1.5), Clemson (+2.5), Houston (+3), Ball State (-9.5) and Florida State (-7.5).</p>
<p>Of course bowl games are strange for a variety of reasons, (hitting the buffet circuit, poor practices, lack of focus…) so there always seems to be a lack of consistency.</p>
<p>We will check back in a few weeks on how well this did.</p>
