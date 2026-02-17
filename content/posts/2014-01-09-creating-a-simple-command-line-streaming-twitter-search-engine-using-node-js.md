---
title: "Creating a simple command line streaming twitter search engine using node.js"
date: 2014-01-09T14:57:00+00:00
slug: "creating-a-simple-command-line-streaming-twitter-search-engine-using-node-js"
author: "granger"
draft: false
tags:
  - "Streaming API"
  - "twitter"
  - "R"
  - "node.js"
  - "command line"
  - "twit"
---

<p><span style="line-height: 1.5;">About two weeks ago I published an article on <a href="http://www.sixmanguru.com/texas-football-fan-sentiment-analysis-during-valero-alamo-bowl/">Texas fan sentiment analysis</a>, based on over 50,000 tweets I collected the day of the Valero Alamo Bowl.</span></p>
<p>This was fairly straightforward, as I utilized the <a href="https://github.com/tgsmith61591/Twitter-and-UT-Football/commit/5f4a13ed6d54f9fb81d37f501bae07cf7f73f0b5">code my colleague Taylor Smith created</a> and modified it for my purposes. My biggest changes came with how I analyzed the data.</p>
<p>The problem I had was that the process of obtaining the tweets tied up my R console. This was problematic because I could neither use R, nor start looking at the data. Another problem was I had to determine up front how long I wanted to run the search. I could kill the process, but if the game ran past the time I had set, I would have to rush and restart it again.</p>
<p>I prefer using the command line on things like this. I don’t use the command line for too much, so I knew it would at least free up my software. Last summer, before twitter changed their OAuth requirements, you could login very easily via the command line.</p>
<p>Obviously that has changed. With the latest OAuth, logging in directly from the command line is not really an option. You need a registered application to make this happen.</p>
<p>This fall, <a href="http://twitter.com/lizwinks">Elizabeth Winkler at Mass Relevance</a> mentioned an <a href="https://github.com/sferik/t">open source package called ‘t’</a> that runs using Ruby. I set this up, but don’t really know enough Ruby to get much further than simple tweeting and a basic search from the command line.</p>
<p>What I really wanted was a way to run command line searches that could utilize the streaming API and parse them to a nice JSON file. I am fairly certain t does that, but like I said, my Ruby skills aren’t the best.</p>
<p>Talking this over with my brother-in-law at lunch on Sunday, he figured there had to be a good way to do this with node.js. I have a little experience in node.js and JavaScript is fairly forgiving, so I started looking into it.</p>
<p>I found several node.js modules, such as ‘twit’ and ‘twitter’. Both are open source and easily found on GitHub. I experimented with both and came up with a simple method for running a search using twit (basically modifying a bit of their sample code).</p>
<p><strong>Getting Started</strong><br/>
First make sure you have installed node.js on your computer</p>
<p>Then go to <a href="https://github.com/ttezel/twit">https://github.com/ttezel/twit</a> and follow the instructions on installing twit.</p>
<p>Next you need to register for a twitter account. I read one article this week where a guy suggests registering a separate twitter account just for twitter searches and experiments. That way you don’t get your personal account banned by accident. I didn’t do this.</p>
<p>Once you have an account, you need to then go <a href="https://dev.twitter.com/">https://dev.twitter.com</a> and sign in as a developer to register an application.</p>
<p>After logging in, go to the drop-down menu at the top-right (where your profile icon is) and go to ‘My Applications’.</p>
<p>Create a new application. This is where you get your consumer key and Consumer Secret. (make sure you save these for easy reference in a minute)</p>
<p>Now that you have those, you need to click the button at the bottom of the page and ‘Create My Access Token’. Here’s where you get the Access Token Key and Access Token Secret. (again, make sure you save these for easy reference in a minute)</p>
<p>I am going to assume you are logged into your terminal. Node and node_modules should be installed in your main directory. If so, you can change directories</p>
<p><code>cd node_modules/twit/examples</code> (honestly, you can put this anywhere, but I figured why not keep it with the other twit code?)</p>
<p>create a file mysearch.js (<code>vi mysearch.js</code> and paste the code below)</p>
<p><code><br/>
var Twit = require('twit')<br/>
var T = new Twit({<br/>
consumer_key: 'put yours here'<br/>
, consumer_secret: ‘put yours here’<br/>
, access_token: ‘put yours here '<br/>
, access_token_secret: 'put yours here '<br/>
})<br/>
</code><br/>
<code><br/>
// filter public stream<br/>
var fs = require('fs')<br/>
var myList = ['texas', ‘longhorns’]<br/>
var stream = T.stream('statuses/filter', { track: myList})</code><br/>
<code>stream.on('tweet', function (tweet) {<br/>
var jsonTweet = JSON.stringify(tweet)<br/>
</code><br/>
<code><br/>
// write to file<br/>
fs = require('fs');<br/>
fs.appendFile('myStream.json', jsonTweet + "\n", function (err) {<br/>
if (err) return console.log(err);<br/>
</code><br/>
<code><br/>
});<br/>
})<br/>
</code></p>
<p>Be sure to add your login key, token secrets…</p>
<p>That’s it. Now just run the file.</p>
<p><code>node mysearch</code></p>
<p>A nice file (myStream.json) will start to accumulate in the folder you set it to.</p>
<p>You can modify your search my just changing the items in myList. The twit documentation also gives solid advice on how to modify the searches by location, language, etc.</p>
<p>When you want to kill it, just hit ctrl-C, but this thing can run for days, as long as you leave it on.</p>
<p>What to do with that file is up to you. I will post next week on update R code to get you some usable data. Taylor Smith has some good starter code and we are working on tightening that up a bit. (There are some kinks in the date/time portion)</p>
<p>The eventual extension will be to set the searches up on a server and let them run continuously on their own. I am currently installing node.js on my server and will be able to run these as chron jobs.</p>
<p>Another extension is to evaluate the tweets in real-time and send some sort of data to a browser. Node.js was created to allow you to run JavaScript code on the backend very efficiently.</p>
