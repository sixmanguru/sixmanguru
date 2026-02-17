---
title: "Using Microsoft’s TrueSkill to Rank Texas Six-Man Football Teams"
date: 2015-12-03T19:31:06+00:00
slug: "using-microsofts-trueskill-to-rank-texas-six-man-football-teams"
author: "granger"
draft: false
tags:
  - "six-man football"
  - "six-man"
  - "XBox"
  - "Trueskill"
  - "Texas high school football"
  - "TXHSFB"
---

<p>People have always compared six-man football to a computer game. With its wild scores and fast-paced style, six-man football can be just as exciting, if not more so.</p>
<p>So what if you played the entire six-man season on your Xbox?</p>
<p>That’s why I decided to use the <a href="http://research.microsoft.com/en-us/projects/trueskill/" target="_blank">TrueSkill Ranking System</a> created by Microsoft Research for Xbox Live games and apply it to the season.</p>
<p>Microsoft uses this algorithm to track the skill of gamers in order to place them in competitive matches. On the Microsoft Research website it explains that the ranking system is characterized by two attributes: a players average skill level (ranking) and the degree of uncertainty in the gamer’s skill (this would be the variation in the players level). If you would like to read more, it can be found at the Microsoft Research website, http://research.microsoft.com/en-us/projects/trueskill/</p>
<p>Heck, gamers love this thing. If you want to really know more about the math behind it, a guy named Jeff Moser has written a bunch on the subject.</p>
<p><strong>Very nerdy links—→</strong><br/>
<a href="http://www.moserware.com/assets/computing-your-skill/The%20Math%20Behind%20TrueSkill.pdf" target="_blank">Here http://www.moserware.com/assets/computing-your-skill/The%20Math%20Behind%20TrueSkill.pdf</a></p>
<p><strong>And here</strong><br/>
<a href="http://www.moserware.com/2010/03/computing-your-skill.html" target="_blank">http://www.moserware.com/2010/03/computing-your-skill.html</a></p>
<p>As with any algorithm, there are several ways you could implement it. I decided in the first trial I would start of with no priors. This means all teams started the season with the base ranking. Since I also program primarily in Python, I decided to use the Trueskill package developed by a South Korean game developer named Heungsub Lee. It seems to be well-written and moderately documented.</p>
<p>Let’s take a quick look at the top-10.</p>
<table width="255">
<tbody>
<tr>
<td width="30">1</td>
<td width="200">Richland Springs</td>
<td width="25">432</td>
</tr>
<tr>
<td>2</td>
<td>Borden County</td>
<td>425</td>
</tr>
<tr>
<td>3</td>
<td>Buena Vista</td>
<td>409</td>
</tr>
<tr>
<td>4</td>
<td>Austin Veritas</td>
<td>408</td>
</tr>
<tr>
<td>5</td>
<td>Happy</td>
<td>403</td>
</tr>
<tr>
<td>6</td>
<td>Gorman</td>
<td>403</td>
</tr>
<tr>
<td>7</td>
<td>Jonesboro</td>
<td>396</td>
</tr>
<tr>
<td>8</td>
<td>SA FEAST Homeschool</td>
<td>388</td>
</tr>
<tr>
<td>9</td>
<td>Crowell</td>
<td>381</td>
</tr>
<tr>
<td>10</td>
<td>Houston Emery-Weiner</td>
<td>381</td>
</tr>
</tbody>
</table>
<p>Not bad, but not stellar. Let’s see the next 20</p>
<table width="259">
<tbody>
<tr>
<td width="19">11</td>
<td width="201">Calvert</td>
<td width="39">379</td>
</tr>
<tr>
<td>12</td>
<td>Midland Trinity</td>
<td>377</td>
</tr>
<tr>
<td>13</td>
<td>Garden City</td>
<td>374</td>
</tr>
<tr>
<td>14</td>
<td>Valley</td>
<td>373</td>
</tr>
<tr>
<td>15</td>
<td>Dallas Inspired Vision</td>
<td>372</td>
</tr>
<tr>
<td>16</td>
<td>Follett</td>
<td>370</td>
</tr>
<tr>
<td>17</td>
<td>Zephyr</td>
<td>370</td>
</tr>
<tr>
<td>18</td>
<td>Abbott</td>
<td>369</td>
</tr>
<tr>
<td>19</td>
<td>Pasadena First Baptist</td>
<td>368</td>
</tr>
<tr>
<td>20</td>
<td>Gordon</td>
<td>366</td>
</tr>
<tr>
<td>21</td>
<td>Balmorhea</td>
<td>366</td>
</tr>
<tr>
<td>22</td>
<td>San Marcos Hill Country Christian</td>
<td>366</td>
</tr>
<tr>
<td>23</td>
<td>Bryan Christian Homeschool (BVCHEA)</td>
<td>366</td>
</tr>
<tr>
<td>24</td>
<td>Rochelle</td>
<td>364</td>
</tr>
<tr>
<td>25</td>
<td>Baytown Christian</td>
<td>364</td>
</tr>
<tr>
<td>26</td>
<td>Mt. Calm</td>
<td>363</td>
</tr>
<tr>
<td>27</td>
<td>Hermleigh</td>
<td>360</td>
</tr>
<tr>
<td>28</td>
<td>Nazareth</td>
<td>357</td>
</tr>
<tr>
<td>29</td>
<td>Chester</td>
<td>357</td>
</tr>
<tr>
<td>30</td>
<td>Sterling City</td>
<td>352</td>
</tr>
</tbody>
</table>
<p>OK, but again, you can see some flaws.</p>
<p>One of the really cool things TrueSkill brings is a pretty good ability to predict the winners of games. In the version I ran, I allowed TrueSkill to predict all of the games, but throwing out the really close ones where it determined the probabilities of a team were between 47%-53%. One of the reasons to do this would be that during all of week one games, with probabilities at 50-50, we can just throw those out.</p>
<p>For the season, TrueSkill predicted 832 of 1108 (75.1%) games, which isn’t bad. For the playoffs, it is even better at 82-20 (80.4%).</p>
<p>It will be interesting to see how it does this week.</p>
<p><strong>Matchup: Zephyr (11-2-0) at Abbott (11-2-0)</strong><br/>
Rating Before: 370~28 / 369~29<br/>
Match Quality: 0.82<br/>
Zephyr odds winning: 50.9%<br/>
<strong>Prediction: TOSS-UP –&gt; Zephyr</strong></p>
<p><strong>Matchup: Crowell (9-3-0) at Borden County (13-0-0)</strong><br/>
Rating Before: 381~28 / 425~33<br/>
Match Quality: 0.68<br/>
Crowell odds winning: 27.6%<br/>
<strong>Prediction: Borden County</strong></p>
<p><strong>Matchup: Follett (12-1-0) at Buena Vista (13-0-0)</strong><br/>
Rating Before: 370~31 / 409~37<br/>
Match Quality: 0.68<br/>
Follett odds winning: 30.2%<br/>
<strong>Prediction: Buena Vista</strong></p>
<p><strong>Matchup: Midland Trinity (11-2-0) at Houston Emery-Weiner (11-2-0)</strong><br/>
Rating Before: 377~28 / 381~28<br/>
Match Quality: 0.83<br/>
Midland Trinity odds winning: 47.4% [predict: TOSS-UP]<br/>
<strong>Prediction: TOSS-UP –&gt; Houston Emery-Weiner</strong></p>
<p><strong>Matchup: Guthrie (11-2-0) at Richland Springs (13-0-0)</strong><br/>
Rating Before: 351~29 / 432~35<br/>
Match Quality: 0.44<br/>
Guthrie odds winning: 13.8%<br/>
<strong>Prediction: Richland Springs</strong></p>
<p><strong>Matchup: San Marcos Hill Country Christian (11-1-0) at WF Notre Dame (9-2-0)</strong><br/>
Rating Before: 366~35 / 341~30<br/>
Match Quality: 0.75<br/>
San Marcos Hill Country Christian odds winning: 63.3%<br/>
<strong>Prediction: San Marcos Hill Country Christian (this one was played this morning-correct)</strong></p>
<p><strong>Matchup: Austin Veritas (12-0-0) at Waco Live Oak (10-2-0)</strong><br/>
Rating Before: 408~37 / 339~32<br/>
Match Quality: 0.51<br/>
Austin Veritas odds winning: 81.7%<br/>
<strong>Prediction: Austin Veritas (this one just finished-correct)<br/>
</strong></p>
<p>I plan on making some adjustments to this and seeing what comes up. Stay tuned.</p>
<p>Just for fun, here’s the entire list</p>

<table width="265">
<tbody>
<tr>
<td width="25">1</td>
<td width="201">Richland Springs</td>
<td width="39">432</td>
</tr>
<tr>
<td>2</td>
<td>Borden County</td>
<td>425</td>
</tr>
<tr>
<td>3</td>
<td>Buena Vista</td>
<td>409</td>
</tr>
<tr>
<td>4</td>
<td>Austin Veritas</td>
<td>408</td>
</tr>
<tr>
<td>5</td>
<td>Happy</td>
<td>403</td>
</tr>
<tr>
<td>6</td>
<td>Gorman</td>
<td>403</td>
</tr>
<tr>
<td>7</td>
<td>Jonesboro</td>
<td>396</td>
</tr>
<tr>
<td>8</td>
<td>SA FEAST Homeschool</td>
<td>388</td>
</tr>
<tr>
<td>9</td>
<td>Crowell</td>
<td>381</td>
</tr>
<tr>
<td>10</td>
<td>Houston Emery-Weiner</td>
<td>381</td>
</tr>
<tr>
<td>11</td>
<td>Calvert</td>
<td>379</td>
</tr>
<tr>
<td>12</td>
<td>Midland Trinity</td>
<td>377</td>
</tr>
<tr>
<td>13</td>
<td>Garden City</td>
<td>374</td>
</tr>
<tr>
<td>14</td>
<td>Valley</td>
<td>373</td>
</tr>
<tr>
<td>15</td>
<td>Dallas Inspired Vision</td>
<td>372</td>
</tr>
<tr>
<td>16</td>
<td>Follett</td>
<td>370</td>
</tr>
<tr>
<td>17</td>
<td>Zephyr</td>
<td>370</td>
</tr>
<tr>
<td>18</td>
<td>Abbott</td>
<td>369</td>
</tr>
<tr>
<td>19</td>
<td>Pasadena First Baptist</td>
<td>368</td>
</tr>
<tr>
<td>20</td>
<td>Gordon</td>
<td>366</td>
</tr>
<tr>
<td>21</td>
<td>Balmorhea</td>
<td>366</td>
</tr>
<tr>
<td>22</td>
<td>San Marcos Hill Country Christian</td>
<td>366</td>
</tr>
<tr>
<td>23</td>
<td>Bryan Christian Homeschool (BVCHEA)</td>
<td>366</td>
</tr>
<tr>
<td>24</td>
<td>Rochelle</td>
<td>364</td>
</tr>
<tr>
<td>25</td>
<td>Baytown Christian</td>
<td>364</td>
</tr>
<tr>
<td>26</td>
<td>Mt. Calm</td>
<td>363</td>
</tr>
<tr>
<td>27</td>
<td>Hermleigh</td>
<td>360</td>
</tr>
<tr>
<td>28</td>
<td>Nazareth</td>
<td>357</td>
</tr>
<tr>
<td>29</td>
<td>Chester</td>
<td>357</td>
</tr>
<tr>
<td>30</td>
<td>Sterling City</td>
<td>352</td>
</tr>
<tr>
<td>31</td>
<td>Guthrie</td>
<td>351</td>
</tr>
<tr>
<td>32</td>
<td>Cedar Park Summit</td>
<td>351</td>
</tr>
<tr>
<td>33</td>
<td>Watauga Harvest</td>
<td>349</td>
</tr>
<tr>
<td>34</td>
<td>Milford</td>
<td>347</td>
</tr>
<tr>
<td>35</td>
<td>Waco Methodist Childrens Home</td>
<td>347</td>
</tr>
<tr>
<td>36</td>
<td>Southland</td>
<td>346</td>
</tr>
<tr>
<td>37</td>
<td>Austin Hill Country</td>
<td>344</td>
</tr>
<tr>
<td>38</td>
<td>Granbury North Central Texas Academy</td>
<td>344</td>
</tr>
<tr>
<td>39</td>
<td>Rockwall Heritage</td>
<td>341</td>
</tr>
<tr>
<td>40</td>
<td>WF Notre Dame</td>
<td>341</td>
</tr>
<tr>
<td>41</td>
<td>Ira</td>
<td>339</td>
</tr>
<tr>
<td>42</td>
<td>Waco Live Oak</td>
<td>339</td>
</tr>
<tr>
<td>43</td>
<td>Newcastle</td>
<td>335</td>
</tr>
<tr>
<td>44</td>
<td>Stephenville Faith</td>
<td>334</td>
</tr>
<tr>
<td>45</td>
<td>Bastrop Tribe Consolidated</td>
<td>333</td>
</tr>
<tr>
<td>46</td>
<td>Fort Worth THESA</td>
<td>331</td>
</tr>
<tr>
<td>47</td>
<td>Walnut Springs</td>
<td>330</td>
</tr>
<tr>
<td>48</td>
<td>Fort Worth Nazarene</td>
<td>329</td>
</tr>
<tr>
<td>49</td>
<td>Motley County</td>
<td>328</td>
</tr>
<tr>
<td>50</td>
<td>Willow Park Trinity</td>
<td>328</td>
</tr>
<tr>
<td>51</td>
<td>Aspermont</td>
<td>323</td>
</tr>
<tr>
<td>52</td>
<td>Tioga</td>
<td>315</td>
</tr>
<tr>
<td>53</td>
<td>Blum</td>
<td>314</td>
</tr>
<tr>
<td>54</td>
<td>Coolidge</td>
<td>314</td>
</tr>
<tr>
<td>55</td>
<td>Longview Trinity</td>
<td>314</td>
</tr>
<tr>
<td>56</td>
<td>Conroe Covenant Christian</td>
<td>313</td>
</tr>
<tr>
<td>57</td>
<td>Savoy</td>
<td>311</td>
</tr>
<tr>
<td>58</td>
<td>Bryson</td>
<td>311</td>
</tr>
<tr>
<td>59</td>
<td>Klondike</td>
<td>308</td>
</tr>
<tr>
<td>60</td>
<td>Sugar Land HCYA Fort Bend</td>
<td>308</td>
</tr>
<tr>
<td>61</td>
<td>Austin NYOS</td>
<td>308</td>
</tr>
<tr>
<td>62</td>
<td>Decatur Victory Christian</td>
<td>308</td>
</tr>
<tr>
<td>63</td>
<td>Meadow</td>
<td>307</td>
</tr>
<tr>
<td>64</td>
<td>Seguin Lifegate</td>
<td>303</td>
</tr>
<tr>
<td>65</td>
<td>Houston Texas Christian</td>
<td>302</td>
</tr>
<tr>
<td>66</td>
<td>Capital City Christian Home School</td>
<td>300</td>
</tr>
<tr>
<td>67</td>
<td>Knox City</td>
<td>299</td>
</tr>
<tr>
<td>68</td>
<td>Sands</td>
<td>298</td>
</tr>
<tr>
<td>69</td>
<td>Giddings State School</td>
<td>298</td>
</tr>
<tr>
<td>70</td>
<td>Miami</td>
<td>297</td>
</tr>
<tr>
<td>71</td>
<td>Katy Faith West</td>
<td>297</td>
</tr>
<tr>
<td>72</td>
<td>Red Oak Ovilla Christian</td>
<td>297</td>
</tr>
<tr>
<td>73</td>
<td>Robert Lee</td>
<td>296</td>
</tr>
<tr>
<td>74</td>
<td>Union Hill</td>
<td>296</td>
</tr>
<tr>
<td>75</td>
<td>EP Faith</td>
<td>296</td>
</tr>
<tr>
<td>76</td>
<td>Santa Anna</td>
<td>295</td>
</tr>
<tr>
<td>77</td>
<td>Bronte</td>
<td>294</td>
</tr>
<tr>
<td>78</td>
<td>Spur</td>
<td>293</td>
</tr>
<tr>
<td>79</td>
<td>Rising Star</td>
<td>292</td>
</tr>
<tr>
<td>80</td>
<td>Evant</td>
<td>292</td>
</tr>
<tr>
<td>81</td>
<td>Dallas Academy</td>
<td>292</td>
</tr>
<tr>
<td>82</td>
<td>Marfa</td>
<td>290</td>
</tr>
<tr>
<td>83</td>
<td>Irving Faustina</td>
<td>290</td>
</tr>
<tr>
<td>84</td>
<td>Loraine</td>
<td>289</td>
</tr>
<tr>
<td>85</td>
<td>Marshall Christian Academy</td>
<td>288</td>
</tr>
<tr>
<td>86</td>
<td>Dallas Tyler Street</td>
<td>286</td>
</tr>
<tr>
<td>87</td>
<td>Weatherford Christian</td>
<td>286</td>
</tr>
<tr>
<td>88</td>
<td>Oglesby</td>
<td>283</td>
</tr>
<tr>
<td>89</td>
<td>Forestburg</td>
<td>281</td>
</tr>
<tr>
<td>90</td>
<td>SA Castle Hills</td>
<td>281</td>
</tr>
<tr>
<td>91</td>
<td>Williamson County Home School</td>
<td>281</td>
</tr>
<tr>
<td>92</td>
<td>Temple Centex Homeschool</td>
<td>280</td>
</tr>
<tr>
<td>93</td>
<td>Oakwood</td>
<td>279</td>
</tr>
<tr>
<td>94</td>
<td>Sugar Land Logos Prep</td>
<td>279</td>
</tr>
<tr>
<td>95</td>
<td>Huntsville Alpha Omega</td>
<td>279</td>
</tr>
<tr>
<td>96</td>
<td>Arlington St. Paul Prep</td>
<td>279</td>
</tr>
<tr>
<td>97</td>
<td>EP Immanuel Christian</td>
<td>278</td>
</tr>
<tr>
<td>98</td>
<td>Groom</td>
<td>277</td>
</tr>
<tr>
<td>99</td>
<td>Anton</td>
<td>274</td>
</tr>
<tr>
<td>100</td>
<td>Rankin</td>
<td>274</td>
</tr>
<tr>
<td>101</td>
<td>McLean</td>
<td>273</td>
</tr>
<tr>
<td>102</td>
<td>Gholson</td>
<td>273</td>
</tr>
<tr>
<td>103</td>
<td>Eden</td>
<td>272</td>
</tr>
<tr>
<td>104</td>
<td>Denton Calvary</td>
<td>272</td>
</tr>
<tr>
<td>105</td>
<td>Lucas Christian</td>
<td>272</td>
</tr>
<tr>
<td>106</td>
<td>Waco Vanguard College Prep</td>
<td>271</td>
</tr>
<tr>
<td>107</td>
<td>Whitharral</td>
<td>270</td>
</tr>
<tr>
<td>108</td>
<td>Westlake Academy</td>
<td>270</td>
</tr>
<tr>
<td>109</td>
<td>Corpus Christi WINGS</td>
<td>270</td>
</tr>
<tr>
<td>110</td>
<td>Bulverde Bracken Christian</td>
<td>268</td>
</tr>
<tr>
<td>111</td>
<td>Petersburg</td>
<td>267</td>
</tr>
<tr>
<td>112</td>
<td>Lefors</td>
<td>264</td>
</tr>
<tr>
<td>113</td>
<td>Corpus Christi Annapolis</td>
<td>263</td>
</tr>
<tr>
<td>114</td>
<td>Plano CHANT</td>
<td>263</td>
</tr>
<tr>
<td>115</td>
<td>Rule</td>
<td>262</td>
</tr>
<tr>
<td>116</td>
<td>Kress</td>
<td>261</td>
</tr>
<tr>
<td>117</td>
<td>WF Wichita Christian</td>
<td>261</td>
</tr>
<tr>
<td>118</td>
<td>May</td>
<td>259</td>
</tr>
<tr>
<td>119</td>
<td>Iredell</td>
<td>259</td>
</tr>
<tr>
<td>120</td>
<td>Fort Davis</td>
<td>259</td>
</tr>
<tr>
<td>121</td>
<td>Paint Rock</td>
<td>258</td>
</tr>
<tr>
<td>122</td>
<td>Sierra Blanca</td>
<td>257</td>
</tr>
<tr>
<td>123</td>
<td>Cotton Center</td>
<td>257</td>
</tr>
<tr>
<td>124</td>
<td>Fredericksburg Heritage</td>
<td>256</td>
</tr>
<tr>
<td>125</td>
<td>Athens Christian Prep</td>
<td>252</td>
</tr>
<tr>
<td>126</td>
<td>Westbrook</td>
<td>251</td>
</tr>
<tr>
<td>127</td>
<td>O’Donnell</td>
<td>251</td>
</tr>
<tr>
<td>128</td>
<td>Avalon</td>
<td>251</td>
</tr>
<tr>
<td>129</td>
<td>Water Valley</td>
<td>249</td>
</tr>
<tr>
<td>130</td>
<td>Paducah</td>
<td>249</td>
</tr>
<tr>
<td>131</td>
<td>Hart</td>
<td>249</td>
</tr>
<tr>
<td>132</td>
<td>High Island</td>
<td>249</td>
</tr>
<tr>
<td>133</td>
<td>Sidney</td>
<td>249</td>
</tr>
<tr>
<td>134</td>
<td>Blanket</td>
<td>248</td>
</tr>
<tr>
<td>135</td>
<td>Lubbock Home School</td>
<td>248</td>
</tr>
<tr>
<td>136</td>
<td>Dallas Lutheran</td>
<td>248</td>
</tr>
<tr>
<td>137</td>
<td>Dallas Lakehill</td>
<td>248</td>
</tr>
<tr>
<td>138</td>
<td>Campbell</td>
<td>246</td>
</tr>
<tr>
<td>139</td>
<td>Tyler HEAT</td>
<td>245</td>
</tr>
<tr>
<td>140</td>
<td>Wylie Preparatory</td>
<td>242</td>
</tr>
<tr>
<td>141</td>
<td>Abilene Christian</td>
<td>242</td>
</tr>
<tr>
<td>142</td>
<td>Azle Christian</td>
<td>241</td>
</tr>
<tr>
<td>143</td>
<td>Bellville Faith</td>
<td>241</td>
</tr>
<tr>
<td>144</td>
<td>Corpus Christi Abundant Life</td>
<td>240</td>
</tr>
<tr>
<td>145</td>
<td>Austin Brentwood Christian</td>
<td>239</td>
</tr>
<tr>
<td>146</td>
<td>Hedley</td>
<td>237</td>
</tr>
<tr>
<td>147</td>
<td>Houston Mount Carmel</td>
<td>237</td>
</tr>
<tr>
<td>148</td>
<td>SA The Winston</td>
<td>237</td>
</tr>
<tr>
<td>149</td>
<td>Amherst</td>
<td>234</td>
</tr>
<tr>
<td>150</td>
<td>Wellman-Union</td>
<td>233</td>
</tr>
<tr>
<td>151</td>
<td>Richardson Canyon Creek Christian</td>
<td>232</td>
</tr>
<tr>
<td>152</td>
<td>SA Lutheran</td>
<td>232</td>
</tr>
<tr>
<td>153</td>
<td>Strawn</td>
<td>231</td>
</tr>
<tr>
<td>154</td>
<td>Cherokee</td>
<td>231</td>
</tr>
<tr>
<td>155</td>
<td>Chillicothe</td>
<td>230</td>
</tr>
<tr>
<td>156</td>
<td>Orange Community Christian</td>
<td>230</td>
</tr>
<tr>
<td>157</td>
<td>Grandfalls-Royalty</td>
<td>229</td>
</tr>
<tr>
<td>158</td>
<td>Fannindel</td>
<td>228</td>
</tr>
<tr>
<td>159</td>
<td>Lorenzo</td>
<td>224</td>
</tr>
<tr>
<td>160</td>
<td>White Deer</td>
<td>223</td>
</tr>
<tr>
<td>161</td>
<td>Wilson</td>
<td>222</td>
</tr>
<tr>
<td>162</td>
<td>Lewisville Lakeland</td>
<td>221</td>
</tr>
<tr>
<td>163</td>
<td>Aquilla</td>
<td>219</td>
</tr>
<tr>
<td>164</td>
<td>Haslet Heritage Christian</td>
<td>219</td>
</tr>
<tr>
<td>165</td>
<td>McKinney Cornerstone</td>
<td>218</td>
</tr>
<tr>
<td>166</td>
<td>Higgins</td>
<td>217</td>
</tr>
<tr>
<td>167</td>
<td>Blackwell</td>
<td>216</td>
</tr>
<tr>
<td>168</td>
<td>Dawson</td>
<td>215</td>
</tr>
<tr>
<td>169</td>
<td>Spring Providence Classical</td>
<td>215</td>
</tr>
<tr>
<td>170</td>
<td>Pflugerville Concordia</td>
<td>215</td>
</tr>
<tr>
<td>171</td>
<td>Woodson</td>
<td>214</td>
</tr>
<tr>
<td>172</td>
<td>SA Great Hearts Monte Vista</td>
<td>214</td>
</tr>
<tr>
<td>173</td>
<td>New Home</td>
<td>212</td>
</tr>
<tr>
<td>174</td>
<td>Lueders-Avoca</td>
<td>212</td>
</tr>
<tr>
<td>175</td>
<td>Lingleville</td>
<td>211</td>
</tr>
<tr>
<td>176</td>
<td>Medina</td>
<td>211</td>
</tr>
<tr>
<td>177</td>
<td>Morgan</td>
<td>211</td>
</tr>
<tr>
<td>178</td>
<td>Covington</td>
<td>210</td>
</tr>
<tr>
<td>179</td>
<td>Apple Springs</td>
<td>208</td>
</tr>
<tr>
<td>180</td>
<td>Arlington Newman</td>
<td>208</td>
</tr>
<tr>
<td>181</td>
<td>Plainview Christian</td>
<td>207</td>
</tr>
<tr>
<td>182</td>
<td>Trinidad</td>
<td>204</td>
</tr>
<tr>
<td>183</td>
<td>Kerrville Our Lady of the Hills</td>
<td>203</td>
</tr>
<tr>
<td>184</td>
<td>Lockhart Lighthouse Christian</td>
<td>202</td>
</tr>
<tr>
<td>185</td>
<td>Victoria Home School</td>
<td>199</td>
</tr>
<tr>
<td>186</td>
<td>Silverton</td>
<td>198</td>
</tr>
<tr>
<td>187</td>
<td>Saint Jo</td>
<td>198</td>
</tr>
<tr>
<td>188</td>
<td>Crosby Victory and Praise</td>
<td>197</td>
</tr>
<tr>
<td>189</td>
<td>Ropes</td>
<td>196</td>
</tr>
<tr>
<td>190</td>
<td>Lewisville Founders Classical</td>
<td>196</td>
</tr>
<tr>
<td>191</td>
<td>Mullin</td>
<td>194</td>
</tr>
<tr>
<td>192</td>
<td>Lake Jackson Brazosport Christian</td>
<td>194</td>
</tr>
<tr>
<td>193</td>
<td>EP Jesus Chapel</td>
<td>192</td>
</tr>
<tr>
<td>194</td>
<td>Brownwood Victory Life</td>
<td>189</td>
</tr>
<tr>
<td>195</td>
<td>Amarillo Holy Cross</td>
<td>189</td>
</tr>
<tr>
<td>196</td>
<td>Jayton</td>
<td>188</td>
</tr>
<tr>
<td>197</td>
<td>Benjamin</td>
<td>187</td>
</tr>
<tr>
<td>198</td>
<td>Canton EXEL</td>
<td>187</td>
</tr>
<tr>
<td>199</td>
<td>Dell City</td>
<td>187</td>
</tr>
<tr>
<td>200</td>
<td>Throckmorton</td>
<td>186</td>
</tr>
<tr>
<td>201</td>
<td>Rotan</td>
<td>186</td>
</tr>
<tr>
<td>202</td>
<td>SA The Atonement</td>
<td>186</td>
</tr>
<tr>
<td>203</td>
<td>Johnson County Sports Association</td>
<td>185</td>
</tr>
<tr>
<td>204</td>
<td>Cranfills Gap</td>
<td>182</td>
</tr>
<tr>
<td>205</td>
<td>Carrollton Christian</td>
<td>182</td>
</tr>
<tr>
<td>206</td>
<td>Spring Branch Living Rock Academy</td>
<td>182</td>
</tr>
<tr>
<td>207</td>
<td>Waco Parkview</td>
<td>181</td>
</tr>
<tr>
<td>208</td>
<td>Alvin Living Stones</td>
<td>181</td>
</tr>
<tr>
<td>209</td>
<td>Odessa Latter Rain</td>
<td>180</td>
</tr>
<tr>
<td>210</td>
<td>Granbury Cornerstone</td>
<td>178</td>
</tr>
<tr>
<td>211</td>
<td>Dallas Fairhill</td>
<td>178</td>
</tr>
<tr>
<td>212</td>
<td>Grady</td>
<td>175</td>
</tr>
<tr>
<td>213</td>
<td>Fort Hancock</td>
<td>175</td>
</tr>
<tr>
<td>214</td>
<td>SA Sunnybrook</td>
<td>175</td>
</tr>
<tr>
<td>215</td>
<td>Veribest</td>
<td>172</td>
</tr>
<tr>
<td>216</td>
<td>Greenville Christian</td>
<td>171</td>
</tr>
<tr>
<td>217</td>
<td>New Braunfels Christian</td>
<td>171</td>
</tr>
<tr>
<td>218</td>
<td>Moran</td>
<td>169</td>
</tr>
<tr>
<td>219</td>
<td>EP Home School</td>
<td>165</td>
</tr>
<tr>
<td>220</td>
<td>Highland</td>
<td>163</td>
</tr>
<tr>
<td>221</td>
<td>Bryan Allen Academy</td>
<td>163</td>
</tr>
<tr>
<td>222</td>
<td>Sanderson</td>
<td>160</td>
</tr>
<tr>
<td>223</td>
<td>Lometa</td>
<td>159</td>
</tr>
<tr>
<td>224</td>
<td>Temple Holy Trinity Catholic</td>
<td>157</td>
</tr>
<tr>
<td>225</td>
<td>Kopperl</td>
<td>156</td>
</tr>
<tr>
<td>226</td>
<td>Arlington Flint Academy</td>
<td>156</td>
</tr>
<tr>
<td>227</td>
<td>Paint Creek</td>
<td>155</td>
</tr>
<tr>
<td>228</td>
<td>Midessa Homeschool</td>
<td>151</td>
</tr>
<tr>
<td>229</td>
<td>Panther Creek</td>
<td>149</td>
</tr>
<tr>
<td>230</td>
<td>Tyler King’s Academy</td>
<td>148</td>
</tr>
<tr>
<td>231</td>
<td>Fruitvale</td>
<td>148</td>
</tr>
<tr>
<td>232</td>
<td>Houston Sanchez Charter</td>
<td>148</td>
</tr>
<tr>
<td>233</td>
<td>Leverett’s Chapel</td>
<td>146</td>
</tr>
<tr>
<td>234</td>
<td>Bynum</td>
<td>145</td>
</tr>
<tr>
<td>235</td>
<td>Buckholts</td>
<td>144</td>
</tr>
<tr>
<td>236</td>
<td>Whiteface</td>
<td>143</td>
</tr>
<tr>
<td>237</td>
<td>Prairie Lea</td>
<td>143</td>
</tr>
<tr>
<td>238</td>
<td>West Columbia Charter</td>
<td>141</td>
</tr>
<tr>
<td>239</td>
<td>Gustine</td>
<td>140</td>
</tr>
<tr>
<td>240</td>
<td>Lohn</td>
<td>140</td>
</tr>
<tr>
<td>241</td>
<td>East Texas Home School</td>
<td>140</td>
</tr>
<tr>
<td>242</td>
<td>Northside</td>
<td>139</td>
</tr>
<tr>
<td>243</td>
<td>Irving Universal Academy</td>
<td>137</td>
</tr>
<tr>
<td>244</td>
<td>Brookesmith</td>
<td>136</td>
</tr>
<tr>
<td>245</td>
<td>Lazbuddie</td>
<td>132</td>
</tr>
<tr>
<td>246</td>
<td>Fayette County Sports Association</td>
<td>125</td>
</tr>
<tr>
<td>247</td>
<td>Fort Worth Hill</td>
<td>123</td>
</tr>
<tr>
<td>248</td>
<td>Round Rock Christian</td>
<td>122</td>
</tr>
<tr>
<td>249</td>
<td>Trent</td>
<td>119</td>
</tr>
<tr>
<td>250</td>
<td>Fort Elliott</td>
<td>119</td>
</tr>
<tr>
<td>251</td>
<td>Loop</td>
<td>116</td>
</tr>
<tr>
<td>252</td>
<td>Clear Lake Christian</td>
<td>113</td>
</tr>
<tr>
<td>253</td>
<td>Patton Springs</td>
<td>111</td>
</tr>
<tr>
<td>254</td>
<td>Conroe Lifestyle Christian</td>
<td>111</td>
</tr>
<tr>
<td>255</td>
<td>Penelope</td>
<td>108</td>
</tr>
<tr>
<td>256</td>
<td>Selma River City Believers</td>
<td>107</td>
</tr>
<tr>
<td>257</td>
<td>Gold-Burg</td>
<td>105</td>
</tr>
<tr>
<td>258</td>
<td>Killeen Memorial</td>
<td>101</td>
</tr>
<tr>
<td>259</td>
<td>SA River City</td>
<td>100</td>
</tr>
<tr>
<td>260</td>
<td>Harrold</td>
<td>97</td>
</tr>
</tbody>
</table>
