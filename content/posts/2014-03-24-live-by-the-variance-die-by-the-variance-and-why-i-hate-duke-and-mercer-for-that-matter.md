---
title: "Live by the Variance, Die by the Variance (and why I hate Duke [and Mercer] for that matter"
date: 2014-03-24T21:41:58+00:00
slug: "live-by-the-variance-die-by-the-variance-and-why-i-hate-duke-and-mercer-for-that-matter"
author: "sixmanguru"
draft: false
tags:
  - "March Madness"
  - "least squares"
  - "Optimization"
  - "NLP"
  - "non-linear programming"
  - "NCAA Basketball"
---

<!-- AdSense Now! V3.40 -->
<!-- Post[count: 1] -->
<div class="adsense adsense-leadin" style="float:right;margin: 12px;">
<!-- Guru2013 -->

</div><p>The first weekend of the NCAA Tournament was a wild one. In our competition, we chose models with high variance, knowing full well we could be in a world of hurt if a game or two did not go our way. Being scored on a log loss scale was new to us, and we knew of the risks, but did not really think things could get too bad.</p>
<p>We knew Wichita State was rated too high, but we thought, “hey, maybe they are just that good,” and rolled with it. Anyhow, we had figured they would eventually lose, but one game would not kill us since we could make it up somewhere else.</p>
<p>That was of course until Mercer took it to the Dukies. Most models had Duke as a very strong 3-seed. I believe the <a href="http://fivethirtyeight.com/">fivethirtyeight</a> blog even had Duke as a 93-94% favorite. Those kinds of numbers are for wimps. We had them as a prohibitive 98.4% favorite in one model and 98.9% in another. When you do something like this in a competition where the scoring is based on log loss, you better hope that they win, or else you are dead in the water.</p>
<p>The average score using this model (at least your goal) should be in the 0.4 to 0.5 range. The Duke loss was a 4.1 to 4.5 point penalty that just destroyed us. Unfortunately, no one else was dumb enough to match our probability.</p>
<p>By comparison, last year’s Cinderella, Florida Gulf Coast, had only a 4% chance to beat Georgetown. Using the same formula, you penalty is in the 3′s.</p>
<p>We could have easily solved all of this and handled the huge variance by increasing the variance when calculating our probabilities. But we were in win or go home mode… oh well.</p>
<p>Here is a quick updated simulation of the remaining teams. I ran a somewhat newer updated model 50,000 times.</p>
<p>UPDATED MONTE CARLO SIMULATION WITH NEW PROBABILITIES</p>
<table>
<tbody>
<tr>
<td><strong>Team</strong></td>
<td><strong>Sweet 16</strong></td>
<td><strong>Elite 8</strong></td>
<td><strong>Final 4</strong></td>
<td><strong>Final</strong></td>
<td><strong>Champion</strong></td>
</tr>
<tr>
<td>Louisville</td>
<td>9137</td>
<td>8891</td>
<td>12333</td>
<td>7167</td>
<td>12472</td>
</tr>
<tr>
<td>Arizona</td>
<td>7871</td>
<td>9126</td>
<td>13607</td>
<td>7425</td>
<td>11971</td>
</tr>
<tr>
<td>Florida</td>
<td>12205</td>
<td>4016</td>
<td>11482</td>
<td>10622</td>
<td>11675</td>
</tr>
<tr>
<td>Virginia</td>
<td>16372</td>
<td>7740</td>
<td>11536</td>
<td>7621</td>
<td>6731</td>
</tr>
<tr>
<td>Wisconsin</td>
<td>16889</td>
<td>22709</td>
<td>6769</td>
<td>2276</td>
<td>1357</td>
</tr>
<tr>
<td>Michigan St.</td>
<td>33628</td>
<td>6133</td>
<td>6169</td>
<td>2755</td>
<td>1315</td>
</tr>
<tr>
<td>Michigan</td>
<td>23402</td>
<td>18883</td>
<td>5046</td>
<td>1715</td>
<td>954</td>
</tr>
<tr>
<td>UCLA</td>
<td>37795</td>
<td>3240</td>
<td>5447</td>
<td>2581</td>
<td>937</td>
</tr>
<tr>
<td>Tennessee</td>
<td>26598</td>
<td>17198</td>
<td>4236</td>
<td>1266</td>
<td>702</td>
</tr>
<tr>
<td>Iowa St.</td>
<td>21098</td>
<td>20109</td>
<td>5932</td>
<td>2172</td>
<td>689</td>
</tr>
<tr>
<td>Kentucky</td>
<td>40863</td>
<td>5028</td>
<td>2921</td>
<td>810</td>
<td>378</td>
</tr>
<tr>
<td>Connecticut</td>
<td>28902</td>
<td>16018</td>
<td>3673</td>
<td>1139</td>
<td>268</td>
</tr>
<tr>
<td>San Diego St.</td>
<td>42129</td>
<td>4587</td>
<td>2510</td>
<td>562</td>
<td>212</td>
</tr>
<tr>
<td>Baylor</td>
<td>33111</td>
<td>13578</td>
<td>2578</td>
<td>570</td>
<td>163</td>
</tr>
<tr>
<td>Stanford</td>
<td>22166</td>
<td>23422</td>
<td>3430</td>
<td>860</td>
<td>122</td>
</tr>
<tr>
<td>Dayton</td>
<td>27834</td>
<td>19322</td>
<td>2331</td>
<td>459</td>
<td>54</td>
</tr>
</tbody>
</table>
<!-- AdSense Now! V3.40 -->
<!-- Post[count: 2] -->
<div class="adsense adsense-leadout" style="text-align:center;margin: 12px;">
<!-- Guru2013 -->

</div>
