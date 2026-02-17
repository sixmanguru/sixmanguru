---
title: "Men’s Team Predictions for 2021 NCAA D1 XC Championships"
date: 2021-11-18T22:00:30+00:00
slug: "mens-team-predictions-for-2021-ncaa-d1-xc-championships"
author: "granger"
draft: false
---

<p>Saturday marks the running of the 2021 NCAA D1 Cross Country National Championships in Tallahassee with Northern Arizona on the brink of their fifth team title in six years.</p>
<p>It has been a while since I have publically published any new models in any sport, but yesterday on Twitter, <a href="https://citiusmag.com/">Citius Magazine</a> <a href="https://twitter.com/CitiusMag/status/1461034066736779268">posted something about a video</a> they had done with Isaac Wood at <a href="https://thewoodreportxc.com/">The Wood Report</a> on his prediction.</p>
<p>Being relatively new to the world of collegiate track and cross country, I had no idea who Isaac was and immediately went and subscribed to his website to see what he had built. I also like to see how others model sport and Isaac has an interesting website.</p>
<p>From both their tweet and checking out the website and his simulator, I began to wonder what I could produce before Saturday’s meet. My initial thought was to create my own individual runner ratings and simulate from there, but to be honest, that is something I have been thinking about for a few months now and is just too big a project. What I could do is take Isaac Woods’s individual runner rankings and try to expand on the team result.</p>
<p> </p>
<p><strong>PROJECT OVERVIEW</strong></p>
<p>I decided I would build a quick <a href="https://en.wikipedia.org/wiki/Monte_Carlo_method">Monte Carlo simulator</a> using the top-7 runners for each team racing Saturday, based on <a href="https://thewoodreportxc.com/">The Wood Report</a>, and calculate probabilities for how each team will do. I also figured I might as well look at individual runners and how the top-10 may look. (<strong>HUGE CAVEAT</strong> – I am not including any of the individual runners who are not competing within the team standings. I just didn’t have enough time to build everything from scratch.)</p>
<p> </p>
<p><strong>EDITOR’S NOTE</strong> – While writing this, I realized that most of you could care less about the methodology section, so please feel free to skip all of that and see what I came up with. I understand. I do these types of projects mostly to share my thinking so I can improve my methods at a later date as questions/data improvements come.</p>
<p><strong>METHODOLOGY</strong></p>
<p>The first step is to take the 31 teams and find the top-7 runner ratings. With such a short time horizon and not really having a chance to build my own ratings, I have to combine a little art to the science. The main weakness of doing something like this is that I have no idea how Isaac Wood (and his PhD student) created these and really no idea about the variability of each individual runner.</p>
<p>Cross Country is such a great event because every course is different every day. Hills, terrain, altitude, temperature and humidity vary even from day-to-day on the same course. I am not even going to get into teams racing at a variety of distances leading up to this weekend or where individual runners were within their training when they raced various events. That is not being captured here.</p>
<p>We have what we have. Each runner has been given a rating that from my point of view appears to be really solid.</p>
<p>What I can do is simulate variability. This is where art blends with science.</p>
<p>Let’s take BYU’s Connor Mantz with a rating of 9.97. Sure, he’s a favorite, but how much? In reality, we would have all of the variables I mentioned above already baked into his rating, plug Saturday’s expected variables into a formula, and see what his expected time would be. We would then do that for every runner and build the projected results.</p>
<p>But I don’t have that. I have a bunch of individual ratings. Wood simply uses those to build a final result. Instead of doing that, I prefer to throw some variability into the ratings and run the race thousands of times.</p>
<p>How much variability and where do you model this?</p>
<p>Back to Mantz. Sure he’s a favorite, but there are several guys who can win this race. Some people will have the race of their lives while others will struggle for one reason or another (<em>Think of the three H’s: hills, heat and humidity</em>).</p>
<p>I took the top runner for each school participating and found the standard deviation. I did this as well for the rest of the runners. Not surprisingly, as you go from the first runner for each team to the seventh, the variability explodes. This makes sense. Depth is where this thing is won.</p>
<p>I finally settled on a number closer to the standard deviation of the top runners for each team and used it for every runner in the field. This isn’t the best method, as each runner should have their own variance, but it’ll do.</p>
<p>FINALLY, I use a function to generate a random number within <a href="https://en.wikipedia.org/wiki/Standard_deviation">+/- 1 ‘standard deviation’</a> for each runner to figure out their ‘speed’ for the race, rank the runners and score the race. To understand this better, imagine some runners will run better and some worse, but they won’t always run right at their rating. Odds are they will be somewhere close. Of course there will be outliers, but let’s assume they stay ~ +/-34% of their rating in a ‘standard’ way. I also don’t want to talk about <a href="https://en.wikipedia.org/wiki/Outliers_(book)">Outliers</a> too much <a href="https://www.youtube.com/watch?v=LFFP5Y7DpFA">as this may send shivers down Chris Chavez’ spine. #TeamGladwell</a>. just Kidding.</p>
<p>I do this 10,000 times.</p>
<p>That is, I simulate the race 10,000 times and see how it all plays out. This should give us a pretty good indication of the probability each team has to finish this weekend in a particular place.</p>
<p><strong>TEAM RESULTS</strong></p>
<p>After running the simulation 10,000 times, the overwhelming favorite is Northern Arizona who wins the title 48.78% of the time. Oklahoma State captures the title 22.64%, with Iowa State winning 12% of the time.</p>
<p>Below shows how many times each team placed in the team standings.</p>
<table width="450">
<tbody>
<tr>
<td width="245"><strong>SCHOOL<br/>
</strong></td>
<td width="41"><strong>1ST</strong></td>
<td width="41"><strong>2ND</strong></td>
<td width="41"><strong>3RD</strong></td>
<td width="41"><strong>4TH</strong></td>
<td width="41"><strong>5TH</strong></td>
</tr>
<tr>
<td>Northern Arizona</td>
<td>4878</td>
<td>2479</td>
<td>1350</td>
<td>722</td>
<td>380</td>
</tr>
<tr>
<td>Oklahoma State</td>
<td>2264</td>
<td>2368</td>
<td>1978</td>
<td>1410</td>
<td>978</td>
</tr>
<tr>
<td>Iowa State</td>
<td>1200</td>
<td>1728</td>
<td>1782</td>
<td>1688</td>
<td>1501</td>
</tr>
<tr>
<td>Colorado</td>
<td>705</td>
<td>1257</td>
<td>1643</td>
<td>1782</td>
<td>1651</td>
</tr>
<tr>
<td>Notre Dame</td>
<td>573</td>
<td>1128</td>
<td>1538</td>
<td>1725</td>
<td>1772</td>
</tr>
<tr>
<td>BYU</td>
<td>280</td>
<td>637</td>
<td>946</td>
<td>1329</td>
<td>1702</td>
</tr>
<tr>
<td>Stanford</td>
<td>92</td>
<td>370</td>
<td>670</td>
<td>1093</td>
<td>1519</td>
</tr>
<tr>
<td>Tulsa</td>
<td>8</td>
<td>33</td>
<td>93</td>
<td>251</td>
<td>495</td>
</tr>
</tbody>
</table>
<p>How good is Northern Arizona? They have over and 87% chance to finish in the top-3.</p>

<p>Possibly the more interesting part of all of this is the fact that after the top two, the teams are very bunched together. The probabilities for Iowa State, Colorado, Notre Dame, BYU and Stanford are very close. Fighting through the end will be key and I wonder if something that was mentioned on the podcast could be a factor. Will the course favor track runners over those ‘mudders’ like Colorado?</p>
<p>This is even clearer when we look at the average team finish below.</p>
<p>And don’t ignore Tulsa! They actually won the whole thing 8 times out of 10,000. Sure, that’s only 0.08% of the time, but there’s a chance.</p>
<p>Here’s a table of each team’s AVERAGE FINISH within the simulation.</p>
<table width="400">
<tbody>
<tr>
<td width="175"><strong>SCHOOL</strong></td>
<td style="text-align: center;" width="225"><strong>AVERAGE TEAM FINISH</strong></td>
</tr>
<tr>
<td>Northern Arizona</td>
<td style="text-align: center;">1.99</td>
</tr>
<tr>
<td>Oklahoma State</td>
<td style="text-align: center;">2.99</td>
</tr>
<tr>
<td>Iowa State</td>
<td style="text-align: center;">3.80</td>
</tr>
<tr>
<td>Colorado</td>
<td style="text-align: center;">4.33</td>
</tr>
<tr>
<td>Notre Dame</td>
<td style="text-align: center;">4.49</td>
</tr>
<tr>
<td>BYU</td>
<td style="text-align: center;">5.30</td>
</tr>
<tr>
<td>Stanford</td>
<td style="text-align: center;">5.82</td>
</tr>
<tr>
<td>Tulsa</td>
<td style="text-align: center;">7.40</td>
</tr>
<tr>
<td>Oregon</td>
<td style="text-align: center;">9.93</td>
</tr>
<tr>
<td>Air Force</td>
<td style="text-align: center;">11.86</td>
</tr>
<tr>
<td>Arkansas</td>
<td style="text-align: center;">12.11</td>
</tr>
<tr>
<td>Furman</td>
<td style="text-align: center;">12.87</td>
</tr>
<tr>
<td>Washington</td>
<td style="text-align: center;">13.03</td>
</tr>
<tr>
<td>Wake Forest</td>
<td style="text-align: center;">13.51</td>
</tr>
<tr>
<td>Wisconsin</td>
<td style="text-align: center;">14.79</td>
</tr>
<tr>
<td>Gonzaga</td>
<td style="text-align: center;">15.27</td>
</tr>
<tr>
<td>Ole Miss</td>
<td style="text-align: center;">15.36</td>
</tr>
<tr>
<td>Alabama</td>
<td style="text-align: center;">18.19</td>
</tr>
<tr>
<td>Texas</td>
<td style="text-align: center;">20.51</td>
</tr>
<tr>
<td>Harvard</td>
<td style="text-align: center;">21.20</td>
</tr>
<tr>
<td>Southern Utah</td>
<td style="text-align: center;">21.23</td>
</tr>
<tr>
<td>Portland</td>
<td style="text-align: center;">23.53</td>
</tr>
<tr>
<td>Syracuse</td>
<td style="text-align: center;">24.00</td>
</tr>
<tr>
<td>North Carolina</td>
<td style="text-align: center;">24.01</td>
</tr>
<tr>
<td>Butler</td>
<td style="text-align: center;">24.28</td>
</tr>
<tr>
<td>Florida State</td>
<td style="text-align: center;">24.76</td>
</tr>
<tr>
<td>Princeton</td>
<td style="text-align: center;">25.32</td>
</tr>
<tr>
<td>Georgetown</td>
<td style="text-align: center;">26.06</td>
</tr>
<tr>
<td>Minnesota</td>
<td style="text-align: center;">28.16</td>
</tr>
<tr>
<td>Michigan</td>
<td style="text-align: center;">29.05</td>
</tr>
<tr>
<td>Michigan State</td>
<td style="text-align: center;">30.85</td>
</tr>
</tbody>
</table>
<p>I find it interesting to see the Big 10 Conference anchoring the bottom. If this pans out, then maybe the committee overvalued their quality. If they perform much better than the model, then I would suspect this means the Wood model possibly held those down too much.</p>
<p><strong>INDIVIDUALS</strong></p>
<p>Now, remember, I did not include the true individuals, running the event without their teams.</p>
<p>Here are the top-10 runners based on the simulation.</p>
<table width="885">
<tbody>
<tr>
<td width="156"><strong>INDIVIDUAL</strong></td>
<td width="179"><strong>SCHOOL</strong></td>
<td width="55"><strong>1ST</strong></td>
<td width="55"><strong>2ND</strong></td>
<td width="55"><strong>3RD</strong></td>
<td width="55"><strong>4TH</strong></td>
<td width="55"><strong>5TH</strong></td>
<td width="55"><strong>6TH</strong></td>
<td width="55"><strong>7TH</strong></td>
<td width="55"><strong>8TH</strong></td>
<td width="55"><strong>9TH</strong></td>
<td width="55"><strong>10TH</strong></td>
</tr>
<tr>
<td>Connor Mantz</td>
<td>BYU</td>
<td>4074</td>
<td>1696</td>
<td>975</td>
<td>715</td>
<td>576</td>
<td>498</td>
<td>433</td>
<td>335</td>
<td>263</td>
<td>192</td>
</tr>
<tr>
<td>Adiaan Wildschutt</td>
<td>Florida State</td>
<td>2272</td>
<td>1839</td>
<td>1096</td>
<td>834</td>
<td>646</td>
<td>551</td>
<td>460</td>
<td>442</td>
<td>431</td>
<td>339</td>
</tr>
<tr>
<td>Wesley Kiptoo</td>
<td>Iowa State</td>
<td>1840</td>
<td>1727</td>
<td>1193</td>
<td>826</td>
<td>688</td>
<td>593</td>
<td>501</td>
<td>480</td>
<td>435</td>
<td>401</td>
</tr>
<tr>
<td>Eduardo Herrera</td>
<td>Colorado</td>
<td>436</td>
<td>885</td>
<td>994</td>
<td>781</td>
<td>672</td>
<td>643</td>
<td>572</td>
<td>525</td>
<td>497</td>
<td>477</td>
</tr>
<tr>
<td>Abdihamid Nur</td>
<td>Northern Arizona</td>
<td>415</td>
<td>932</td>
<td>988</td>
<td>805</td>
<td>715</td>
<td>599</td>
<td>603</td>
<td>542</td>
<td>491</td>
<td>450</td>
</tr>
<tr>
<td>Nico Young</td>
<td>Northern Arizona</td>
<td>397</td>
<td>853</td>
<td>896</td>
<td>782</td>
<td>685</td>
<td>570</td>
<td>567</td>
<td>531</td>
<td>527</td>
<td>490</td>
</tr>
<tr>
<td>Charles Hicks</td>
<td>Stanford</td>
<td>187</td>
<td>505</td>
<td>764</td>
<td>716</td>
<td>646</td>
<td>579</td>
<td>589</td>
<td>538</td>
<td>543</td>
<td>513</td>
</tr>
<tr>
<td>Casey Clinger</td>
<td>BYU</td>
<td>165</td>
<td>496</td>
<td>656</td>
<td>724</td>
<td>638</td>
<td>660</td>
<td>520</td>
<td>516</td>
<td>502</td>
<td>504</td>
</tr>
<tr>
<td>Cooper Teare</td>
<td>Oregon</td>
<td>82</td>
<td>312</td>
<td>513</td>
<td>620</td>
<td>621</td>
<td>559</td>
<td>550</td>
<td>522</td>
<td>496</td>
<td>456</td>
</tr>
<tr>
<td>Ahmed Muhumed</td>
<td>Florida State</td>
<td>47</td>
<td>210</td>
<td>397</td>
<td>532</td>
<td>568</td>
<td>505</td>
<td>505</td>
<td>512</td>
<td>503</td>
<td>511</td>
</tr>
</tbody>
</table>
<p>The race is expected to be very close and Mantz (BYU), Wildschutt (FSU) and Kiptoo (ISU) are the clear favorites, but all of the big names are there. Once you venture past those first three, it appears to be wide open.</p>
<p>My model actually had 18 different runners who won the title at least once (way to go, Ky Robinson!) and 21 total who grabbed second at least one time.</p>
<p>I hope you enjoyed this and I understand this was a long and winding road, but I enjoyed diving into this for a day or so and seeing what the numbers showed. Best of luck to all of the runners, especially the ones I know… (go BTR!)</p>
