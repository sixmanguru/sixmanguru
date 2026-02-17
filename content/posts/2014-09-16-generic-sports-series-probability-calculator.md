---
title: "Generic Sports Series Probability Calculator"
date: 2014-09-16T13:32:28+00:00
slug: "generic-sports-series-probability-calculator"
author: "sixmanguru"
draft: false
tags:
  - "tennis"
  - "baseball"
  - "gambling"
  - "probability"
  - "series"
  - "hockey"
  - "Python"
---

<!-- AdSense Now! V3.40 -->
<!-- Post[count: 1] -->
<div class="adsense adsense-leadin" style="float:right;margin: 12px;">
<!-- Guru2013 -->

</div><p>With the baseball playoffs upon us, I have decided to start building a simulator to determine series outcomes once they start. I decided to make this as generic as possible. This simulator is not specific to baseball or even to a particular series length.</p>
<p>Obviously, the first parts to think about <a href="http://www.sixmanguru.com/mlb-home-field-advantage-this-season/">I addressed in my previous post relating to home field advantage</a>, ratings and the probability a team would win a single game versus a specific opponent.</p>
<p>I will come back to this later in the month, as we get closer to the playoffs and I tie this all together.</p>
<p>Let’s assume for today that we know the probability a specific that Team A will defeat Team B. Let’s also assume, for matters of simplicity, that this single-game probability remains the same throughout the a series, regardless of any possible home field advantage.</p>
<p>Since we are dealing with a single probability and no perceived home field advantage, all we need for inputs are: p(Team A wins a single game), the current series record of the two teams and the numbers of games to win the series (e.g., 1 for a one-game series, 3 for a five-game series and 4 for a seven-game series).</p>
<p>All of my code is listed here on github, <a href="https://gist.github.com/sixmanguru">https://gist.github.com/sixmanguru</a></p>
<p><strong>INPUTS</strong><br/>
Like I said, let’s keep this simple. Probabilities, current series record, length of series.</p>
<p>seriesProb(.54,0,0,4)</p>
<p>The function calls for the series probabilities, give Team A holding a 54% chance to win a single game, the series is just beginning (0-0) and it takes for games to win the series (seven-game series).</p>
<p>That’s all.</p>
<p><strong>OUPUT</strong><br/>
Here’s the abbreviated (rounded to four digits).</p>
<p>([0.085, 0.1565, 0.1799, 0.1655], 0.5869, [0.0448, 0.0967, 0.1306, 0.141], 0.4131)</p>
<p>The first list contains the probabilities that Team A wins the series EXACTLY 4-0, 4-1, 4-2 or 4-3. The number trailing is the total probability Team A wins the series.</p>
<p>The second list contains the probabilities Team A loses the series EXACTLY 0-4, 1-4, 2-4, 3-4, with the total probability they lose the series following.</p>
<p><strong>ALTERNATE EXAMPLES</strong><br/>
Let’s assume the only thing you change is the fact that Team A now leads the series 3-0.</p>
<p>seriesProb(.54,3,0,4)</p>
<p>([0.54, 0.2484, 0.1143, 0.0526], 0.9553, [0, 0, 0, 0.0448], 0.0448)</p>
<p>As you can see above, there exists no change for Team B to win the series now 4-0, 4-1 or 4-2 and they have a 4.5% chance to even win the series at all. This can be verified by 0.46^4, which is approximately 0.0448.</p>
<p>Now let’s assume that it is a one game series.</p>
<p>seriesProb(.54,0,0,1)</p>
<p>([0.54], 0.54, [0.46], 0.46)</p>
<p>As you can see, it is one game, so the original probabilities are returned.</p>
<p>Finally, as a test, we say Team A trails the series 3-4 in a seven-game series.</p>
<p>seriesProb(.54,3,4,4)</p>
<p>It quickly returns (0,1). It is impossible for Team A to win and certain that Team B will win.</p>
<p><strong>LIMITATIONS</strong><br/>
The two biggest limitations to resolve (assuming you accept the theory that you can actually assign a probability to the function at all) remain to be the possibility of a home field advantage and how it would play out based on the series’ format (i.e., 2-3-2 vs. 2-2-1-1-1 and such)</p>
<p>Lastly, I would like to thank Jeff Sackmann, the author of Tennis Abstract and several other endeavors. His original python code for simulating a tennis match was the foundation for this project. His Python code for tennis Markov Chains can be found here, <a href="http://summerofjeff.wordpress.com/2011/01/13/python-code-for-tennis-markov/">http://summerofjeff.wordpress.com/2011/01/13/python-code-for-tennis-markov/</a></p>
<!-- AdSense Now! V3.40 -->
<!-- Post[count: 2] -->
<div class="adsense adsense-leadout" style="text-align:center;margin: 12px;">
<!-- Guru2013 -->

</div>
