---
title: "Creating Maps on the Fly For UIL Realignment"
date: 2014-02-03T16:46:21+00:00
slug: "creating-maps-on-the-fly-for-uil-realignment"
author: "granger"
draft: false
tags:
  - "SQL"
  - "high school football"
  - "Streaming API"
  - "TXHSFB"
  - "twitter"
  - "six-man football"
  - "Texas Football"
  - "Football"
  - "Google Maps API v3"
  - "MySQL"
---

<p>This morning the high school football season officially started with the release of the much anticipated 2014-2016 UIL Football Alignments. This usually started with the UIL servers crashing due to the high volume of traffic (it did briefly, prior to release). This year the UIL was prepared and had a back-up plan to divert traffic off their site.</p>
<p>So at exactly 9:00 am, the Twitterverse was alive with the ramblings of everyone who cares about Texas high school football.</p>
<p>I downloaded the files and immediately started sorting the teams into an Excel spreadsheet I had prepared for the occasion. Once done, I placed the data into my main database online.</p>
<p>I had been modifying my map code I created and showed in a previous post to handle the different divisions, sort them by division and district and color code them. By recycling this code, I easily created three maps.</p>
<p>Here’s the one where I sort them by division (blue for d1, red for d2)<br/>
<a href="http://sixmanfootball.com/big_alignment_map.php">http://sixmanfootball.com/big_alignment_map.php</a></p>
<p>Here’s a look at it</p>
<p><a href="http://sixmanguru.com/wp-content/uploads/2014/02/Screen-Shot-2014-02-03-at-10.47.44-AM-300x245.png"><img alt="" class="alignleft wp-image-355 size-medium" height="245" src="http://sixmanguru.com/wp-content/uploads/2014/02/Screen-Shot-2014-02-03-at-10.47.44-AM-300x245-300x245.png" width="300"/></a></p>
<p>Then here are the ones where I separate Division 1 and 2 and then split up the districts.<br/>
<a href="http://sixmanfootball.com/alignment_map.php?did=1">http://sixmanfootball.com/alignment_map.php?did=1</a><br/>
<a href="http://sixmanfootball.com/alignment_map.php?did=2">http://sixmanfootball.com/alignment_map.php?did=2</a></p>
<p>Here’s an example shot of what they look like</p>
<p><a href="http://sixmanguru.com/wp-content/uploads/2014/02/Screen-Shot-2014-02-03-at-10.50.02-AM-300x223.png"><img alt="" class="alignright wp-image-356 size-medium" height="223" src="http://sixmanguru.com/wp-content/uploads/2014/02/Screen-Shot-2014-02-03-at-10.50.02-AM-300x223-300x223.png" width="300"/></a></p>
<p>Using the new google maps API, it took less than an hour to get everything up and running. All that was left was a little formatting and fine-tuning. The conversion of the data to an XML file makes all of the debugging so much easier.</p>
