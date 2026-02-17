---
title: "MLB Home Field Advantage this season"
date: 2014-09-09T12:46:34+00:00
slug: "mlb-home-field-advantage-this-season"
author: "sixmanguru"
draft: false
---

<!-- AdSense Now! V3.40 -->
<!-- Post[count: 1] -->
<div class="adsense adsense-leadin" style="float:right;margin: 12px;">
<!-- Guru2013 -->

</div><p>Honestly, it is hard to get fired up about the MLB Playoffs these days as a Houston Astros fan. But I figure it may be a way to test a few models and work on my programming.</p>
<p>After scrubbing the internet for scores, I decided to do a simple non-linear programming model to create some rankings. If you want to read more about NLP Optimization, please <a href="http://www.sixmanguru.com/super-bowl-least-squares-predictions-take-the-points/">read my earlier posts I ran during last year’s NFL season</a>.</p>
<p>I tried to apply home field advantage as a singular term, but found there wasn’t a generic home field advantage as in football. I then decided to try and determine if each teams’ individual HFA would have any effect on the ratings. With so many more games, this number had a better likelihood of showing some importance.</p>
<p>In general, the average score of a MLB game this year has been 4.11-4.09 in favor of the home team.</p>
<p>When you look at individual HFA, results are pretty amazing. As expected, the Colorado Rockies get almost a run and a half (1.47) bump at home. The Rockies are a solid 19 games better at home.</p>
<p>Next on the list are the Florida Marlins. First off, does anyone really call them the Miami Marlins? The Marlins have a little over a run per game advantage at home (1.14). Like the Rockies, they appear to be out of the hunt for the playoffs.</p>
<p>The team most likely to be able to take advantage of the home field advantage in the playoffs appears to be the Oakland A’s, who are more than 3/4 of a run (0.76) better at home. The A’s have nine more games at home in the regular season. Also, they get to finish the season at Texas, who are rating only slightly ahead of Colorado, Arizona and Miami as the worst teams in baseball. The Rangers also have no effective HFA either.</p>
<p>Washington (0.429), Pittsburgh (0.333) and Atlanta (0.154) are the only other teams in the playoff picture with significant home field advantages.</p>
<p>Here are a list of the current home field advantages. Those not listed have no significant HFA (0).</p>
<table border="0" cellpadding="0" cellspacing="0">
<colgroup>
<col span="2"/> </colgroup>
<tbody>
<tr>
<td><strong>Team</strong></td>
<td><strong>HFA</strong></td>
</tr>
<tr>
<td>COL</td>
<td>1.473564</td>
</tr>
<tr>
<td>MIA</td>
<td>1.14011</td>
</tr>
<tr>
<td>OAK</td>
<td>0.760433</td>
</tr>
<tr>
<td>SDP</td>
<td>0.704609</td>
</tr>
<tr>
<td>WSN</td>
<td>0.429156</td>
</tr>
<tr>
<td>PIT</td>
<td>0.33299</td>
</tr>
<tr>
<td>CHC</td>
<td>0.25553</td>
</tr>
<tr>
<td>CIN</td>
<td>0.239817</td>
</tr>
<tr>
<td>TBR</td>
<td>0.210181</td>
</tr>
<tr>
<td>ATL</td>
<td>0.153853</td>
</tr>
<tr>
<td>PHI</td>
<td>0.052209</td>
</tr>
<tr>
<td>TOR</td>
<td>0.016576</td>
</tr>
</tbody>
</table>
<p>Here are the current team ratings, as we head into the final few games of the season.</p>
<table border="0" cellpadding="0" cellspacing="0" width="128">
<colgroup>
<col span="2" width="64"/> </colgroup>
<tbody>
<tr>
<td height="20" width="64"><strong>Team</strong></td>
<td width="64"><strong>Rating</strong></td>
</tr>
<tr>
<td height="20">LAA</td>
<td>5.137348</td>
</tr>
<tr>
<td height="20">SEA</td>
<td>4.943415</td>
</tr>
<tr>
<td height="20">OAK</td>
<td>4.925794</td>
</tr>
<tr>
<td height="20">BAL</td>
<td>4.771614</td>
</tr>
<tr>
<td height="20">WSN</td>
<td>4.513368</td>
</tr>
<tr>
<td height="20">DET</td>
<td>4.462223</td>
</tr>
<tr>
<td height="20">LAD</td>
<td>4.363542</td>
</tr>
<tr>
<td height="20">SFG</td>
<td>4.326927</td>
</tr>
<tr>
<td height="20">KCR</td>
<td>4.305852</td>
</tr>
<tr>
<td height="20">TOR</td>
<td>4.229679</td>
</tr>
<tr>
<td height="20">CLE</td>
<td>4.184073</td>
</tr>
<tr>
<td height="20">TBR</td>
<td>4.164056</td>
</tr>
<tr>
<td height="20">NYM</td>
<td>4.038186</td>
</tr>
<tr>
<td height="20">STL</td>
<td>4.031671</td>
</tr>
<tr>
<td height="20">NYY</td>
<td>3.997041</td>
</tr>
<tr>
<td height="20">ATL</td>
<td>3.988839</td>
</tr>
<tr>
<td height="20">PIT</td>
<td>3.944171</td>
</tr>
<tr>
<td height="20">MIL</td>
<td>3.930484</td>
</tr>
<tr>
<td height="20">MIN</td>
<td>3.825875</td>
</tr>
<tr>
<td height="20">CIN</td>
<td>3.783494</td>
</tr>
<tr>
<td height="20">HOU</td>
<td>3.759729</td>
</tr>
<tr>
<td height="20">BOS</td>
<td>3.720102</td>
</tr>
<tr>
<td height="20">PHI</td>
<td>3.676738</td>
</tr>
<tr>
<td height="20">CHW</td>
<td>3.599442</td>
</tr>
<tr>
<td height="20">CHC</td>
<td>3.442758</td>
</tr>
<tr>
<td height="20">SDP</td>
<td>3.341322</td>
</tr>
<tr>
<td height="20">TEX</td>
<td>3.337711</td>
</tr>
<tr>
<td height="20">MIA</td>
<td>3.30692</td>
</tr>
<tr>
<td height="20">ARI</td>
<td>3.278469</td>
</tr>
<tr>
<td height="20">COL</td>
<td>2.669157</td>
</tr>
</tbody>
</table>
<p>The next step in the coming weeks will be to use the rating and home field advantage numbers to create a simulation of the playoffs.</p>
<!-- AdSense Now! V3.40 -->
<!-- Post[count: 2] -->
<div class="adsense adsense-leadout" style="text-align:center;margin: 12px;">
<!-- Guru2013 -->

</div>
