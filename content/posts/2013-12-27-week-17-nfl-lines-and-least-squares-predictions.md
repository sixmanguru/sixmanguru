---
title: "Week 17 NFL Lines and Least Squares Predictions"
date: 2013-12-27T15:34:18+00:00
slug: "week-17-nfl-lines-and-least-squares-predictions"
author: "granger"
draft: false
tags:
  - "non-linear programming"
  - "least squares"
  - "Optimization"
  - "NFL"
  - "Football"
  - "NLP"
  - "gambling"
---

<p>If you have not read any of my previous Least Squared posting, please refer to the initial post <a href="http://www.sixmanguru.com/nfl-week-14-predictions-ratings-optimization-and-non-linear-programming/">here</a>.</p>
<p><strong>Week 16 in review:</strong> Only one game was in the range where we have been fairly confident on the selections. New England was a favorite in the system, but getting 2.5 points from Vegas. New England destroyed the Ravens, so the &gt;100% difference between the expected and Vegas lines, bring that rule to 12-3 over the past four weeks.</p>
<p>Overall, the LS method went 8-7 (the Green Bay game again did not have a line, due to the unexpected status of Aaron Rodgers). This brings the Least Squares method to 35-24-1 over the last four weeks.</p>
<p>In games where the absolute raw difference was greater than 2.5 went 4-2, bringing its totals to 17-10 for the past four weeks.</p>
<p><strong>Week 17 schedule:</strong> Five games fulfill the greater than 100% difference between expected and Vegas lines. Miami (-6) is a heavy favorite over the New York Jets. Detroit (+3) is considered a favorite over Minnesota, despite getting points. Washington (+4) is in the same position, as they are getting points at the New York Giants, despite being the favorite. The Kansas City Chiefs (+9.5) are getting huge points, despite being straight up favorites against the San Diego Chargers. Dallas (+6.5) is getting points as well, although the system is considering them a favorite.</p>
<p><strong>Why these lines are probably so different</strong><br/>
Being the final weekend of the season, there are obvious reasons for the dramatic differences in the lines. One is that some games have almost zero playoff implications to one team, but mean everything to the other (Kansas City at San Diego, NY Jets at Miami). The other main reason is probably injuries and general chaos among one of the teams (Washington at NY Giants, Philly at Dallas).</p>
<p>Both Washington and Dallas are disasters. In Washington, Shanahan has benched RGIII and virtually ticked off everyone, including his son and OC, Kyle. Talk out of Dallas is that Tony Romo and maybe Dez Bryant are out or probable. With a playoff spot in the line, who knows who will actually play for the Cowboys? I suspect they will make a game of it, but then again, they may just be ready to implode. I am also surprised that Washington game is so out of whack, since the Giants have not been too great, despite how bad Washington may tank this game. Again, gamble at your own risk.</p>
<p>I have listed the data below.</p>
<table border="0" cellpadding="0" cellspacing="0" width="389">
<colgroup>
<col width="111"/>
<col width="104"/>
<col width="31"/>
<col width="49"/>
<col width="50"/>
<col width="44"/> </colgroup>
<tbody>
<tr>
<td height="14" width="111">Visitor</td>
<td width="104">Home</td>
<td width="31">Line</td>
<td width="49">Expected</td>
<td width="50">Diff (raw)</td>
<td width="44">Diff/line</td>
</tr>
<tr>
<td height="14">Carolina Panthers</td>
<td>Atlanta Falcons</td>
<td align="right">-6.5</td>
<td align="right">-10.28</td>
<td align="right">-3.78</td>
<td align="right">58%</td>
</tr>
<tr>
<td height="14">Baltimore Ravens</td>
<td>Cinncinati Bengals</td>
<td align="right">6.5</td>
<td align="right">8.30</td>
<td align="right">1.80</td>
<td align="right">28%</td>
</tr>
<tr>
<td height="14">Houston Texans</td>
<td>Tennessee Titans</td>
<td align="right">7</td>
<td align="right">9.88</td>
<td align="right">2.88</td>
<td align="right">41%</td>
</tr>
<tr>
<td height="14">Jacksonville Jaguars</td>
<td>Indianapolis Colts</td>
<td align="right">11.5</td>
<td align="right">16.83</td>
<td align="right">5.33</td>
<td align="right">46%</td>
</tr>
<tr>
<td height="14">New York Jets</td>
<td>Miami Dolphins</td>
<td align="right">6</td>
<td align="right">12.93</td>
<td align="right">6.93</td>
<td align="right">116%</td>
</tr>
<tr>
<td height="14">Detroit Lions</td>
<td>Minnesota Vikings</td>
<td align="right">3</td>
<td align="right">-1.90</td>
<td align="right">-4.90</td>
<td align="right">-163%</td>
</tr>
<tr>
<td height="14">Washington Redksins</td>
<td>New York Giants</td>
<td align="right">4</td>
<td align="right">-2.46</td>
<td align="right">-6.46</td>
<td align="right">-161%</td>
</tr>
<tr>
<td height="14">Cleveland Browns</td>
<td>Pittsburgh Steelers</td>
<td align="right">7</td>
<td align="right">7.01</td>
<td align="right">0.01</td>
<td align="right">0%</td>
</tr>
<tr>
<td height="14">Denver Broncos</td>
<td>Oakland Raiders</td>
<td align="right">-13</td>
<td align="right">-15.39</td>
<td align="right">-2.39</td>
<td align="right">18%</td>
</tr>
<tr>
<td height="14">Buffalo Bills</td>
<td>New England Patriots</td>
<td align="right">9.5</td>
<td align="right">11.19</td>
<td align="right">1.69</td>
<td align="right">18%</td>
</tr>
<tr>
<td height="14">Tampa Bay Buccaneers</td>
<td>New Orleans Saints</td>
<td align="right">13</td>
<td align="right">13.42</td>
<td align="right">0.42</td>
<td align="right">3%</td>
</tr>
<tr>
<td height="14">San Francisco 49ers</td>
<td>Arizona Cardinals</td>
<td align="right">-1</td>
<td align="right">-1.99</td>
<td align="right">-0.99</td>
<td align="right">99%</td>
</tr>
<tr>
<td height="14">Kansas City Chiefs</td>
<td>San Diego Chargers</td>
<td align="right">9.5</td>
<td align="right">-2.11</td>
<td align="right">-11.61</td>
<td align="right">-122%</td>
</tr>
<tr>
<td height="14">St. Louis Rams</td>
<td>Seattle Seahawks</td>
<td align="right">10.5</td>
<td align="right">14.53</td>
<td align="right">4.03</td>
<td align="right">38%</td>
</tr>
<tr>
<td height="14">Philadelphia Eagles</td>
<td>Dallas Cowboys</td>
<td align="right">-6.5</td>
<td align="right">3.73</td>
<td align="right">10.23</td>
<td align="right">-157%</td>
</tr>
</tbody>
</table>
