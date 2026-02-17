---
title: "2014 US Open Men’s Draw Simulation"
date: 2014-08-25T08:22:57+00:00
slug: "2014-us-open-mens-draw-simulation"
author: "sixmanguru"
draft: false
---

<!-- AdSense Now! V3.40 -->
<!-- Post[count: 1] -->
<div class="adsense adsense-leadin" style="float:right;margin: 12px;">
<!-- Guru2013 -->

</div><p>The U.S. Open main draw begins this morning and for the fourth year in a row, I will not be able to attend. Gone are the good ol’ days of working for the USTA and getting to take the trip up to New York to take it all in.</p>
<p>Since I cannot go, I decided to utilize Markov Chain models and Monte Carlo simulations to predict who will win.</p>
<p>Markov Models for tennis are essentially placing some initial inputs into a model and allow it to simulate an entire match, giving you the probabilities player A wins over player B. A Monte Carlo simulation is when you run an <strong>entire tournament</strong> over and over like this. Even if you can do the math, one of the most difficult parts is creating the initial inputs to run the Markov Model.</p>
<p><strong>MY METHODOLOGY</strong><br/>
I decided to experiment with an idea that begins with something I read in Dr. Kamran Aslam’s PhD <a href="http://digitallibrary.usc.edu/cdm/ref/collection/p15799coll3/id/12697">dissertation</a> he wrote at USC. Dr. Aslam and his advisor, Dr. Paul K. Newton published portions of this paper several times, including in the Journal of Quantitative Analysis in Sport back in 2009.</p>
<p>Dr. Aslam took the idea that you start by finding the overall mean probability to win a point while returning. This is defined as the returning average of ‘the field’. Let’s say this is 0.330. Then, if Roger Federer is playing Novak Djokovic and Roger’s average ability to win a point returning is 0.40, then he is 0.07 better than ‘the field’. If Novak’s average is 0.41, then he is 0.08 better than ‘the field’.</p>
<p>Then, if Roger’s percentage he wins serve is 0.7, you subtract Novak’s ability ‘above the field’ (0.08), making Roger’s effective serving percentage, 0.62.</p>
<p>Likewise, if Novak’s serving percentage is 0.68, then his effective serving percentage is 0.61. Therefore, the input to the program would be 0.62 and 0.39 for Roger (one minus Novak’s effective serving percentage). If you ran this for Novak, the inputs would be 0.61 and 0.38.</p>
<p><strong>Modifications</strong><br/>
To get the data, I scraped all serving and receiving stats from the <a href="http://www.atpworldtour.com/Tennis/Players/Top-Players/John-Isner.aspx?t=pa">ATP website</a> for each player in the draw. I also decided to scale the data.</p>
<p><strong>Scaling</strong><br/>
Using only hard court results for the 2014 season, I scaled the data based on the level of competition. This allowed me to include all Challenger data as well as ATP-level, which is available on the ATP site. If an opponent was inside the top-64, no scaling was done. If the opponent was ranked between 65 and 128, then I scaled it down by 1.5%. If the opponent was in the top-192, I scaled it another 1.5%. I scaled it another 1.5% for between 193-256 and another 1.5% for those over a 256 ranking.</p>
<p>For some matches, the opponent’s ranking is listed at N/A. In those cases, the scaling was done based on the player’s own ranking, which seemed to be close enough to the actual ranking, except in a few instances.</p>
<p>Scaling this way may not be the best solution, but this is a solid starting point.<br/>
I then found ‘the field’ by averaging the scaled percentages of all players in the tournament. Five players have not played on the hard courts yet this season, so I removed them when calculating the field. Also, rather than placing zeroes in the data for them, I substituted numbers slightly below the averages for both serving and receiving.</p>
<p>In future versions, I may substitute scaled, full season statistics, irrelevant of surface for these players.</p>
<p><strong>Noah Rubin</strong><br/>
Then there was the case of <a href="http://www.atpworldtour.com/Tennis/Players/Ru/N/Noah-Rubin.aspx?t=pa">Noah Rubin</a>, who only had one hard court match, where he had some pretty good numbers, despite losing last week in Winston-Salem. In this case, I decided to manually modify his percentages down closer to the five I had to manually enter who had not played a single hard court match.</p>
<p><strong>Shortcomings</strong><br/>
Most of the problems come from too little data on some players. Some of this can be handled by using more stringent scaling for Challenger-level matches. Two of the most noticeable are Gilles Muller and <a href="http://www.atpworldtour.com/Tennis/Players/Do/J/Jared-Donaldson.aspx?t=pa">Jared Donaldson</a>. Muller won the Guadalajara Challenger and none of his opponents’ rankings are listed in the data, so they were only scaled per his No.68-ranking. Donaldson also had a lot of Challenger results that were not scaled sufficiently.</p>
<p><strong>Coding</strong><br/>
Jeff Sackman at tennisabstract.com <a href="http://summerofjeff.wordpress.com/2011/01/13/python-code-for-tennis-markov/">published some python code</a> to run the Markov Models a few years ago (<a href="http://tennisabstract.com/current/2014USOpenMenForecast.html">here’s a link to his 2014 predictions</a>, which you may like more than mine). He uses similar inputs and generates a probability player A wins the match. I modified Jeff’s code for my purposes, then wrapped it within a Monte Carlo Simulation and ran it 50,000 times.</p>
<p>I am not posting my entire code just yet on <a href="https://github.com/sixmanguru">github</a>, but hope to soon. I need to refine my entire process, soup-to-nuts, before I feel comfortable with that.</p>
<p><strong>THE RESULTS</strong><br/>
The table below shows howe far a player advances. For instance, Roger Federer lost 1802 out of 50,000 trials in the first round, but won the tournament 16895 times.</p>
<p>Federer seems to be the biggest winner here with Rafael Nadal out. I know this isn’t perfect, but it is a good start and something to work with moving forward. There are some basic assumptions I make and some data that needs refining, but overall I am satisfied with the outcome.</p>
<table border="0" cellpadding="0" cellspacing="0" width="458">
<colgroup>
<col width="124"/>
<col span="6" width="38"/>
<col width="31"/>
<col width="38"/>
<col width="37"/> </colgroup>
<tbody>
<tr>
<td height="15" width="124"><strong>PLAYER</strong></td>
<td width="38"><strong>R1</strong></td>
<td width="38"><strong>R2</strong></td>
<td width="38"><strong>R3</strong></td>
<td width="38"><strong>R16</strong></td>
<td width="38"><strong>Q</strong></td>
<td width="38"><strong>S</strong></td>
<td width="31"><strong>F</strong></td>
<td width="38"><strong>W</strong></td>
<td width="37"><strong>PCT</strong></td>
</tr>
<tr>
<td height="15">Roger-Federer</td>
<td>1802</td>
<td>1399</td>
<td>4752</td>
<td>5083</td>
<td>5099</td>
<td>8057</td>
<td>6913</td>
<td>16895</td>
<td>33.8%</td>
</tr>
<tr>
<td height="15">Tomas-Berdych</td>
<td>4984</td>
<td>1008</td>
<td>5294</td>
<td>6528</td>
<td>7710</td>
<td>11934</td>
<td>5119</td>
<td>7423</td>
<td>14.8%</td>
</tr>
<tr>
<td height="15">Novak-Djokovic</td>
<td>244</td>
<td>18702</td>
<td>4269</td>
<td>3604</td>
<td>5764</td>
<td>4425</td>
<td>5658</td>
<td>7334</td>
<td>14.7%</td>
</tr>
<tr>
<td height="15">Andy-Murray</td>
<td>795</td>
<td>7560</td>
<td>7183</td>
<td>7213</td>
<td>13748</td>
<td>5073</td>
<td>4877</td>
<td>3551</td>
<td>7.1%</td>
</tr>
<tr>
<td height="15">Gilles-Muller</td>
<td>5497</td>
<td>25948</td>
<td>3678</td>
<td>3013</td>
<td>3864</td>
<td>2726</td>
<td>2705</td>
<td>2569</td>
<td>5.1%</td>
</tr>
<tr>
<td height="15">Milos-Raonic</td>
<td>3273</td>
<td>16891</td>
<td>7391</td>
<td>7462</td>
<td>5420</td>
<td>5007</td>
<td>2704</td>
<td>1852</td>
<td>3.7%</td>
</tr>
<tr>
<td height="15">Stan-Wawrinka</td>
<td>10010</td>
<td>5230</td>
<td>11653</td>
<td>5295</td>
<td>7827</td>
<td>5558</td>
<td>2753</td>
<td>1674</td>
<td>3.3%</td>
</tr>
<tr>
<td height="15">Kei-Nishikori</td>
<td>9637</td>
<td>4005</td>
<td>2004</td>
<td>16234</td>
<td>7388</td>
<td>6449</td>
<td>2777</td>
<td>1506</td>
<td>3.0%</td>
</tr>
<tr>
<td height="15">David-Ferrer</td>
<td>6078</td>
<td>14349</td>
<td>3023</td>
<td>8772</td>
<td>9880</td>
<td>5189</td>
<td>1576</td>
<td>1133</td>
<td>2.3%</td>
</tr>
<tr>
<td height="15">Blaz-Kavcic</td>
<td>6213</td>
<td>9611</td>
<td>16077</td>
<td>5177</td>
<td>6755</td>
<td>3917</td>
<td>1524</td>
<td>726</td>
<td>1.5%</td>
</tr>
<tr>
<td height="15">Marin-Cilic</td>
<td>17736</td>
<td>6164</td>
<td>6662</td>
<td>8257</td>
<td>6488</td>
<td>3217</td>
<td>905</td>
<td>571</td>
<td>1.1%</td>
</tr>
<tr>
<td height="15">Peter-Gojowczyk</td>
<td>6533</td>
<td>24512</td>
<td>5850</td>
<td>5298</td>
<td>3446</td>
<td>2674</td>
<td>1152</td>
<td>535</td>
<td>1.1%</td>
</tr>
<tr>
<td height="15">Jared-Donaldson</td>
<td>21742</td>
<td>3033</td>
<td>10349</td>
<td>5732</td>
<td>6508</td>
<td>1532</td>
<td>677</td>
<td>427</td>
<td>0.9%</td>
</tr>
<tr>
<td height="15">David-Goffin</td>
<td>2882</td>
<td>3878</td>
<td>15412</td>
<td>13738</td>
<td>10691</td>
<td>2144</td>
<td>836</td>
<td>419</td>
<td>0.8%</td>
</tr>
<tr>
<td height="15">Roberto-Bautista-Agut</td>
<td>9661</td>
<td>6577</td>
<td>12280</td>
<td>16611</td>
<td>2253</td>
<td>1578</td>
<td>685</td>
<td>355</td>
<td>0.7%</td>
</tr>
<tr>
<td height="15">Adrian-Mannarino</td>
<td>9823</td>
<td>8095</td>
<td>13559</td>
<td>14600</td>
<td>1878</td>
<td>1270</td>
<td>528</td>
<td>247</td>
<td>0.5%</td>
</tr>
<tr>
<td height="15">Paolo-Lorenzi</td>
<td>4830</td>
<td>17542</td>
<td>13070</td>
<td>6225</td>
<td>6295</td>
<td>1285</td>
<td>515</td>
<td>238</td>
<td>0.5%</td>
</tr>
<tr>
<td height="15">Simone-Bolelli</td>
<td>12534</td>
<td>12440</td>
<td>6899</td>
<td>10541</td>
<td>4619</td>
<td>2052</td>
<td>681</td>
<td>234</td>
<td>0.5%</td>
</tr>
<tr>
<td height="15">Facundo-Bagnis</td>
<td>22299</td>
<td>5898</td>
<td>6488</td>
<td>11127</td>
<td>2308</td>
<td>1093</td>
<td>590</td>
<td>197</td>
<td>0.4%</td>
</tr>
<tr>
<td height="15">Bernard-Tomic</td>
<td>16933</td>
<td>18795</td>
<td>2488</td>
<td>5200</td>
<td>4245</td>
<td>1712</td>
<td>432</td>
<td>195</td>
<td>0.4%</td>
</tr>
<tr>
<td height="15">Igor-Sijsling</td>
<td>10360</td>
<td>6161</td>
<td>21214</td>
<td>6118</td>
<td>3278</td>
<td>2052</td>
<td>626</td>
<td>191</td>
<td>0.4%</td>
</tr>
<tr>
<td height="15">Ernests-Gulbis</td>
<td>10555</td>
<td>16235</td>
<td>7808</td>
<td>10532</td>
<td>2450</td>
<td>1743</td>
<td>487</td>
<td>190</td>
<td>0.4%</td>
</tr>
<tr>
<td height="15">Gael-Monfils</td>
<td>28258</td>
<td>2975</td>
<td>8844</td>
<td>4478</td>
<td>4152</td>
<td>860</td>
<td>292</td>
<td>141</td>
<td>0.3%</td>
</tr>
<tr>
<td height="15">Dominic-Thiem</td>
<td>13221</td>
<td>16989</td>
<td>7085</td>
<td>8985</td>
<td>1991</td>
<td>1272</td>
<td>317</td>
<td>140</td>
<td>0.3%</td>
</tr>
<tr>
<td height="15">Ivo-Karlovic</td>
<td>12126</td>
<td>5162</td>
<td>26714</td>
<td>3018</td>
<td>1564</td>
<td>938</td>
<td>342</td>
<td>136</td>
<td>0.3%</td>
</tr>
<tr>
<td height="15">Jo-Wilfried-Tsonga</td>
<td>20942</td>
<td>8099</td>
<td>8426</td>
<td>7785</td>
<td>3365</td>
<td>856</td>
<td>395</td>
<td>132</td>
<td>0.3%</td>
</tr>
<tr>
<td height="15">Richard-Gasquet</td>
<td>13310</td>
<td>18723</td>
<td>9403</td>
<td>4126</td>
<td>3460</td>
<td>664</td>
<td>222</td>
<td>92</td>
<td>0.2%</td>
</tr>
<tr>
<td height="15">Yen-Hsun-Lu</td>
<td>15007</td>
<td>14542</td>
<td>16524</td>
<td>1747</td>
<td>1306</td>
<td>530</td>
<td>254</td>
<td>90</td>
<td>0.2%</td>
</tr>
<tr>
<td height="15">Benoit-Paire</td>
<td>20522</td>
<td>10624</td>
<td>8481</td>
<td>6731</td>
<td>2643</td>
<td>642</td>
<td>277</td>
<td>80</td>
<td>0.2%</td>
</tr>
<tr>
<td height="15">Grigor-Dimitrov</td>
<td>15605</td>
<td>14089</td>
<td>10471</td>
<td>5488</td>
<td>3458</td>
<td>618</td>
<td>197</td>
<td>74</td>
<td>0.1%</td>
</tr>
<tr>
<td height="15">Philipp-Kohlschreiber</td>
<td>27701</td>
<td>5789</td>
<td>5829</td>
<td>8094</td>
<td>1545</td>
<td>654</td>
<td>317</td>
<td>71</td>
<td>0.1%</td>
</tr>
<tr>
<td height="15">Marcos-Baghdatis</td>
<td>32264</td>
<td>5563</td>
<td>4588</td>
<td>4262</td>
<td>2312</td>
<td>804</td>
<td>148</td>
<td>59</td>
<td>0.1%</td>
</tr>
<tr>
<td height="15">John-Isner</td>
<td>14229</td>
<td>12162</td>
<td>12604</td>
<td>8587</td>
<td>1547</td>
<td>599</td>
<td>217</td>
<td>55</td>
<td>0.1%</td>
</tr>
<tr>
<td height="15">Kevin-Anderson</td>
<td>3544</td>
<td>18025</td>
<td>16794</td>
<td>7219</td>
<td>3297</td>
<td>922</td>
<td>151</td>
<td>48</td>
<td>0.1%</td>
</tr>
<tr>
<td height="15">Juan-Monaco</td>
<td>29058</td>
<td>7290</td>
<td>6559</td>
<td>4912</td>
<td>1679</td>
<td>336</td>
<td>124</td>
<td>42</td>
<td>0.1%</td>
</tr>
<tr>
<td height="15">Sam-Querrey</td>
<td>2888</td>
<td>23684</td>
<td>19638</td>
<td>1877</td>
<td>1236</td>
<td>444</td>
<td>192</td>
<td>41</td>
<td>0.1%</td>
</tr>
<tr>
<td height="15">Alexander-Kudryavtsev</td>
<td>24959</td>
<td>5369</td>
<td>15596</td>
<td>2145</td>
<td>1205</td>
<td>570</td>
<td>117</td>
<td>39</td>
<td>0.1%</td>
</tr>
<tr>
<td height="15">Bradley-Klahn</td>
<td>21459</td>
<td>11049</td>
<td>12642</td>
<td>2322</td>
<td>1899</td>
<td>430</td>
<td>162</td>
<td>37</td>
<td>0.1%</td>
</tr>
<tr>
<td height="15">Evgeny-Donskoy</td>
<td>25041</td>
<td>5464</td>
<td>15495</td>
<td>2100</td>
<td>1199</td>
<td>560</td>
<td>116</td>
<td>25</td>
<td>0.1%</td>
</tr>
<tr>
<td height="15">Steve-Johnson</td>
<td>22309</td>
<td>10788</td>
<td>9442</td>
<td>5674</td>
<td>1130</td>
<td>539</td>
<td>93</td>
<td>25</td>
<td>0.1%</td>
</tr>
<tr>
<td height="15">Dudi-Sela</td>
<td>751</td>
<td>25740</td>
<td>14179</td>
<td>6185</td>
<td>2661</td>
<td>380</td>
<td>84</td>
<td>20</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Tommy-Robredo</td>
<td>19699</td>
<td>17062</td>
<td>5206</td>
<td>5582</td>
<td>1758</td>
<td>570</td>
<td>106</td>
<td>17</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Radek-Stepanek</td>
<td>11794</td>
<td>30753</td>
<td>3478</td>
<td>2102</td>
<td>1464</td>
<td>282</td>
<td>111</td>
<td>16</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Andreas-Beck</td>
<td>2542</td>
<td>27796</td>
<td>11149</td>
<td>6347</td>
<td>1739</td>
<td>323</td>
<td>89</td>
<td>15</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Sergiy-Stakhovsky</td>
<td>15749</td>
<td>11889</td>
<td>12577</td>
<td>7060</td>
<td>2052</td>
<td>550</td>
<td>109</td>
<td>14</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Julien-Benneteau</td>
<td>29478</td>
<td>9134</td>
<td>6133</td>
<td>3817</td>
<td>1163</td>
<td>200</td>
<td>61</td>
<td>14</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Wayne-Odesnik</td>
<td>40363</td>
<td>3301</td>
<td>1383</td>
<td>3746</td>
<td>849</td>
<td>295</td>
<td>54</td>
<td>9</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">James-McGee</td>
<td>10881</td>
<td>25214</td>
<td>7925</td>
<td>4574</td>
<td>1153</td>
<td>192</td>
<td>52</td>
<td>9</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Andrey-Kuznetsov</td>
<td>28541</td>
<td>9826</td>
<td>9132</td>
<td>1393</td>
<td>891</td>
<td>159</td>
<td>49</td>
<td>9</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Jiri-Vesely</td>
<td>39990</td>
<td>3818</td>
<td>3995</td>
<td>1132</td>
<td>811</td>
<td>202</td>
<td>44</td>
<td>8</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Tatsuma-Ito</td>
<td>27691</td>
<td>9767</td>
<td>7701</td>
<td>3842</td>
<td>650</td>
<td>298</td>
<td>43</td>
<td>8</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Lleyton-Hewitt</td>
<td>45016</td>
<td>1036</td>
<td>2024</td>
<td>1202</td>
<td>499</td>
<td>183</td>
<td>34</td>
<td>6</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Ivan-Dodig</td>
<td>21405</td>
<td>16081</td>
<td>8031</td>
<td>3614</td>
<td>590</td>
<td>241</td>
<td>32</td>
<td>6</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Mikhail-Youzhny</td>
<td>14304</td>
<td>19251</td>
<td>10826</td>
<td>4501</td>
<td>894</td>
<td>191</td>
<td>27</td>
<td>6</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Marco-Chiudinelli</td>
<td>20849</td>
<td>21573</td>
<td>4124</td>
<td>2442</td>
<td>820</td>
<td>164</td>
<td>22</td>
<td>6</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Dustin-Brown</td>
<td>33067</td>
<td>12283</td>
<td>1366</td>
<td>1966</td>
<td>1030</td>
<td>242</td>
<td>41</td>
<td>5</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Jan-Lennard-Struff</td>
<td>21002</td>
<td>16351</td>
<td>8368</td>
<td>3712</td>
<td>434</td>
<td>111</td>
<td>17</td>
<td>5</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Blaz-Rola</td>
<td>23408</td>
<td>15137</td>
<td>9150</td>
<td>1331</td>
<td>812</td>
<td>118</td>
<td>40</td>
<td>4</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Gilles-Simon</td>
<td>10414</td>
<td>5720</td>
<td>27011</td>
<td>4809</td>
<td>1745</td>
<td>265</td>
<td>32</td>
<td>4</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Thomaz-Bellucci</td>
<td>17702</td>
<td>25481</td>
<td>4806</td>
<td>1182</td>
<td>643</td>
<td>167</td>
<td>15</td>
<td>4</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Feliciano-Lopez</td>
<td>28595</td>
<td>13364</td>
<td>5638</td>
<td>2021</td>
<td>284</td>
<td>85</td>
<td>9</td>
<td>4</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Jeremy-Chardy</td>
<td>22487</td>
<td>19476</td>
<td>5697</td>
<td>1275</td>
<td>794</td>
<td>223</td>
<td>45</td>
<td>3</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Fernando-Verdasco</td>
<td>26592</td>
<td>13988</td>
<td>7748</td>
<td>1047</td>
<td>529</td>
<td>77</td>
<td>17</td>
<td>2</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Jerzy-Janowicz</td>
<td>25303</td>
<td>14188</td>
<td>7428</td>
<td>2276</td>
<td>656</td>
<td>132</td>
<td>15</td>
<td>2</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Ryan-Harrison</td>
<td>34395</td>
<td>9438</td>
<td>4306</td>
<td>1399</td>
<td>417</td>
<td>34</td>
<td>9</td>
<td>2</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Dusan-Lajovic</td>
<td>24697</td>
<td>14643</td>
<td>7500</td>
<td>2296</td>
<td>715</td>
<td>128</td>
<td>20</td>
<td>1</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Alejandro-Falla</td>
<td>27513</td>
<td>16945</td>
<td>4151</td>
<td>827</td>
<td>449</td>
<td>97</td>
<td>17</td>
<td>1</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Edouard-Roger-Vasselin</td>
<td>30301</td>
<td>13073</td>
<td>3280</td>
<td>2566</td>
<td>648</td>
<td>120</td>
<td>11</td>
<td>1</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Jack-Sock</td>
<td>17867</td>
<td>26513</td>
<td>1780</td>
<td>3228</td>
<td>486</td>
<td>114</td>
<td>11</td>
<td>1</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Fabio-Fognini</td>
<td>15873</td>
<td>23836</td>
<td>7021</td>
<td>2983</td>
<td>230</td>
<td>47</td>
<td>9</td>
<td>1</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Sam-Groth</td>
<td>16829</td>
<td>31352</td>
<td>1087</td>
<td>534</td>
<td>148</td>
<td>41</td>
<td>8</td>
<td>1</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Guillermo-Garcia-Lopez</td>
<td>34993</td>
<td>9023</td>
<td>5491</td>
<td>333</td>
<td>124</td>
<td>27</td>
<td>8</td>
<td>1</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Illya-Marchenko</td>
<td>29151</td>
<td>16700</td>
<td>2530</td>
<td>1245</td>
<td>321</td>
<td>47</td>
<td>5</td>
<td>1</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Victor-Estrella-Burgos</td>
<td>39640</td>
<td>4215</td>
<td>5357</td>
<td>598</td>
<td>145</td>
<td>39</td>
<td>5</td>
<td>1</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Kenny-De-Schepper</td>
<td>39445</td>
<td>7622</td>
<td>1860</td>
<td>930</td>
<td>112</td>
<td>26</td>
<td>4</td>
<td>1</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Mikhail-Kukushkin</td>
<td>28998</td>
<td>13406</td>
<td>5509</td>
<td>1915</td>
<td>134</td>
<td>34</td>
<td>3</td>
<td>1</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Andreas-Seppi</td>
<td>34251</td>
<td>8382</td>
<td>5378</td>
<td>1699</td>
<td>261</td>
<td>27</td>
<td>1</td>
<td>1</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Matthias-Bachinger</td>
<td>38206</td>
<td>11021</td>
<td>552</td>
<td>173</td>
<td>41</td>
<td>5</td>
<td>1</td>
<td>1</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Daniel-Gimeno-Traver</td>
<td>9294</td>
<td>29670</td>
<td>6064</td>
<td>4411</td>
<td>431</td>
<td>97</td>
<td>33</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Vasek-Pospisil</td>
<td>37466</td>
<td>7425</td>
<td>2746</td>
<td>1885</td>
<td>410</td>
<td>58</td>
<td>10</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Lukas-Rosol</td>
<td>3411</td>
<td>36289</td>
<td>9252</td>
<td>834</td>
<td>174</td>
<td>33</td>
<td>7</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Lukas-Lacko</td>
<td>36779</td>
<td>9154</td>
<td>2435</td>
<td>1390</td>
<td>181</td>
<td>57</td>
<td>4</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Paul-Henri-Mathieu</td>
<td>44503</td>
<td>5116</td>
<td>256</td>
<td>70</td>
<td>41</td>
<td>10</td>
<td>4</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Tobias-Kamke</td>
<td>9550</td>
<td>7288</td>
<td>27984</td>
<td>4629</td>
<td>464</td>
<td>82</td>
<td>3</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Marinko-Matosevic</td>
<td>48198</td>
<td>762</td>
<td>571</td>
<td>318</td>
<td>113</td>
<td>35</td>
<td>3</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Tim-Smyczek</td>
<td>20643</td>
<td>22118</td>
<td>5015</td>
<td>2062</td>
<td>125</td>
<td>34</td>
<td>3</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Marcos-Giron</td>
<td>35771</td>
<td>8081</td>
<td>4583</td>
<td>1414</td>
<td>124</td>
<td>24</td>
<td>3</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Pere-Riba</td>
<td>40177</td>
<td>4868</td>
<td>3526</td>
<td>1305</td>
<td>104</td>
<td>17</td>
<td>3</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Teymuraz-Gabashvili</td>
<td>22253</td>
<td>21265</td>
<td>5983</td>
<td>390</td>
<td>91</td>
<td>15</td>
<td>3</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Andreas-Haider-Maurer</td>
<td>40339</td>
<td>4504</td>
<td>3543</td>
<td>1481</td>
<td>108</td>
<td>23</td>
<td>2</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Filip-Krajinovic</td>
<td>29357</td>
<td>16801</td>
<td>2890</td>
<td>900</td>
<td>40</td>
<td>10</td>
<td>2</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Donald-Young</td>
<td>43787</td>
<td>3968</td>
<td>1813</td>
<td>305</td>
<td>106</td>
<td>20</td>
<td>1</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Denis-Istomin</td>
<td>36690</td>
<td>9754</td>
<td>2577</td>
<td>701</td>
<td>260</td>
<td>17</td>
<td>1</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Jarkko-Nieminen</td>
<td>37874</td>
<td>4004</td>
<td>7699</td>
<td>332</td>
<td>73</td>
<td>17</td>
<td>1</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Nicolas-Mahut</td>
<td>32298</td>
<td>15471</td>
<td>1808</td>
<td>306</td>
<td>102</td>
<td>14</td>
<td>1</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Alejandro-Gonzalez</td>
<td>24004</td>
<td>22641</td>
<td>2772</td>
<td>478</td>
<td>101</td>
<td>3</td>
<td>1</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Andrey-Golubev</td>
<td>34127</td>
<td>13201</td>
<td>2166</td>
<td>478</td>
<td>25</td>
<td>2</td>
<td>1</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Yoshihito-Nishioka</td>
<td>45170</td>
<td>3981</td>
<td>714</td>
<td>113</td>
<td>21</td>
<td>0</td>
<td>1</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Damir-Dzumhur</td>
<td>43922</td>
<td>4573</td>
<td>607</td>
<td>655</td>
<td>215</td>
<td>28</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Benjamin-Becker</td>
<td>43467</td>
<td>5726</td>
<td>551</td>
<td>194</td>
<td>54</td>
<td>8</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Pablo-Andujar</td>
<td>32133</td>
<td>16181</td>
<td>760</td>
<td>850</td>
<td>70</td>
<td>6</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Marcel-Granollers</td>
<td>12044</td>
<td>29804</td>
<td>7917</td>
<td>210</td>
<td>19</td>
<td>6</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Martin-Klizan</td>
<td>12104</td>
<td>35990</td>
<td>1429</td>
<td>390</td>
<td>82</td>
<td>5</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Nick-Kyrgios</td>
<td>35696</td>
<td>10478</td>
<td>3088</td>
<td>667</td>
<td>66</td>
<td>5</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Santiago-Giraldo</td>
<td>27747</td>
<td>17902</td>
<td>4055</td>
<td>243</td>
<td>48</td>
<td>5</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Frank-Dancevic</td>
<td>17016</td>
<td>28639</td>
<td>3479</td>
<td>755</td>
<td>108</td>
<td>3</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Taro-Daniel</td>
<td>46727</td>
<td>2871</td>
<td>309</td>
<td>78</td>
<td>13</td>
<td>2</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Dmitry-Tursunov</td>
<td>25996</td>
<td>21351</td>
<td>2271</td>
<td>317</td>
<td>64</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Aleksandr-Nedovyesov</td>
<td>39119</td>
<td>9397</td>
<td>1234</td>
<td>239</td>
<td>10</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Niels-Desein</td>
<td>47118</td>
<td>1643</td>
<td>1091</td>
<td>139</td>
<td>8</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Radu-Albot</td>
<td>39586</td>
<td>4073</td>
<td>6027</td>
<td>279</td>
<td>35</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Leonardo-Mayer</td>
<td>9476</td>
<td>29457</td>
<td>10544</td>
<td>512</td>
<td>11</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Albert-Ramos-Vinolas</td>
<td>33171</td>
<td>16487</td>
<td>255</td>
<td>76</td>
<td>11</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Federico-Delbonis</td>
<td>23729</td>
<td>20814</td>
<td>5281</td>
<td>167</td>
<td>9</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Noah-Rubin</td>
<td>26271</td>
<td>19393</td>
<td>4197</td>
<td>131</td>
<td>8</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Matthew-Ebden</td>
<td>40450</td>
<td>4523</td>
<td>4807</td>
<td>213</td>
<td>7</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Joao-Sousa</td>
<td>32984</td>
<td>15840</td>
<td>1045</td>
<td>125</td>
<td>6</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Michael-Llodra</td>
<td>40706</td>
<td>8643</td>
<td>555</td>
<td>93</td>
<td>3</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Robin-Haase</td>
<td>49205</td>
<td>666</td>
<td>115</td>
<td>11</td>
<td>3</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Pablo-Cuevas</td>
<td>46456</td>
<td>3144</td>
<td>374</td>
<td>24</td>
<td>2</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Steve-Darcis</td>
<td>37896</td>
<td>11966</td>
<td>124</td>
<td>14</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Jurgen-Melzer</td>
<td>37956</td>
<td>11030</td>
<td>1005</td>
<td>9</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Albert-Montanes</td>
<td>40524</td>
<td>8732</td>
<td>738</td>
<td>6</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Pablo-Carreno-Busta</td>
<td>47458</td>
<td>2446</td>
<td>93</td>
<td>3</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Diego-Schwartzman</td>
<td>49756</td>
<td>234</td>
<td>8</td>
<td>2</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Maximo-Gonzalez</td>
<td>47112</td>
<td>2751</td>
<td>136</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Carlos-Berlocq</td>
<td>49249</td>
<td>733</td>
<td>17</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
<tr>
<td height="15">Borna-Coric</td>
<td>46589</td>
<td>3335</td>
<td>76</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>0.0%</td>
</tr>
</tbody>
</table>
<!-- AdSense Now! V3.40 -->
<!-- Post[count: 2] -->
<div class="adsense adsense-leadout" style="text-align:center;margin: 12px;">
<!-- Guru2013 -->

</div>
