---
title: "Building the Wine Snob Twitter Bot"
date: 2015-05-22T10:08:20+00:00
slug: "building-the-wine-snob-twitter-bot"
author: "granger"
draft: false
---

<p>Yes, I built a Twitter bot. My bot tweets random, nonsensical wine reviews (you can find it here <a href="http://twitter.com/winesnobbot" target="_blank">@WineSnobBot</a>).</p>
<blockquote><p>of fresh peaches, this low-alcohol effort is further bolstered by sémillon, this is now past its peak.</p></blockquote>
<p>I know what you are all asking – WHY?</p>
<p>I have been working recently on a variety of projects. One of them included getting a new server running at the house to mine data and run various other automated scripts. As usual, these projects get bigger and bigger and I haven’t been able get much out the door.</p>
<p>Then I heard on one of my new favorite podcasts, <a href="http://www.partiallyderivative.com/" target="_blank">Partially Derivative</a>, about the <a href="http://www.gregreda.com/2015/03/30/beer-review-markov-chains/" target="_blank">Beer Snob Says twitter bot</a>, by Greg Reda. It was such a fun sounding project and he posted the code on <a href="https://github.com/gjreda/beer-snob-says" target="_blank">GitHub</a>.  Greg does an incredible job explaining the process behind the Markov Chains in the code that generates the reviews and I thought it would be fun to experiment with.</p>
<p>I decided a wine review bot would be a good challenge, so I plotted out a plan in three parts: getting data, modifying the Markov generator and automating a bot to post the results to Twitter.</p>
<p>Like any Markov process, the inputs are key. I needed a massive amount of data (real reviews) to make this work. Greg mentions this in his article, stating your likelihood of a more readable random tweet increases as you increase the size of the corpus.</p>
<p>I started with a few sites and quickly ran into problems. I just couldn’t get enough reviews that were well-written enough to be consistent. Many were amateur reviews with sloppy language.</p>
<p>I eventually found one site that had a database of about 100,000 short reviews of 40-60 words dating from 2000 to the present. I will delve into where more at a later date, since I somehow got away with over 12,000 calls to their website one night. I also plan on combining a few more sources in the future.</p>
<p>So now I have a corpus of over 4 million words. One of the things I first noticed was that certain punctuation works better than others – commas and periods look better in random sentences than parenthesis, colons and semi colons. The result thus far looks like this:</p>

<blockquote><p>the palate, though it’s infused with creme de cassis, dark chocolate, grilled bacon, fine herbs comprise the nose.</p></blockquote>
<p>You will notice it is all lowercase. It just seems to make more sense when it’s all lowercase, rather than just random capitalization. I plan on capitalizing the first word and any subsequent words after periods, but haven’t as yet.</p>
<blockquote><p>angeles—a cool-climate, coastal pinot, especially one that’s amply balanced by orangy acids. —this is a wine to foreign markets.</p></blockquote>
<p>I am also torn about dashes. They seem to crop up in numbers. The division of words like Los Angeles also concerns me, but I’m still formulating my thoughts on proper nouns.</p>
<p>To this point, I needed to get the Markov process running a little better. I started with the basic Python script Reda created and added a few new rules. One rule is to not start a tweet with the word ‘and’. The word ‘with’ is a tougher call, but for now I am keeping it simple.</p>
<blockquote><p>smooth, honeyed finish. grenache, cinsault and grenache are prevalent in the initial taste is your style.</p></blockquote>
<p>Here you can see some work still needs to be done on the Markov process. A layer to possibly eliminate duplication of ‘complex’ words, like Grenache, might help. One thought is to test words in length greater than 5 and force a redo when any are duplicated.</p>
<p>Lastly I needed to automate it. Since my python program will reside on a Mini Mac server, I created a Launchd file to fire off the bot every 4444 seconds (about one hour and 14 minutes). Within the python code, I create a tweet, using <a href="https://github.com/ryanmcgrath/twython" target="_blank">Twython</a>, and save it to a file (so I can check the language and perfect the code) but only actually tweet approximately every one in six times (randomly generated of course). I figure a bot tweeting about four times a day is enough.</p>
<p>This is obviously a work in progress. The first order of business was to get it out the door. The next part is to improve the logic it uses to craft the tweets. Please <a href="https://twitter.com/winesnobbot" target="_blank">follow along</a> and let the Wine Snob Bot know what you think. I will post code and more details in the future.</p>
