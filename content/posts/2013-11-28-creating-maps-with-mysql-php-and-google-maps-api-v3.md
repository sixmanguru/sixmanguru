---
title: "Creating Maps with MySQL, PHP and Google Maps API v3"
date: 2013-11-28T05:55:46+00:00
slug: "creating-maps-with-mysql-php-and-google-maps-api-v3"
author: "granger"
draft: false
tags:
  - "Google Maps"
  - "Google Maps API v3"
  - "PHP"
  - "six-man football"
  - "MySQL"
---

<p>It has been awhile since I started this and never really followed up. I created this blog to be a space where I can share data, news and concepts I am working with.</p>
<p>I have been feverishly working on a project that will be hosted here that just doesn’t seem to want to end. In the meantime, I decided I needed to catch up with a few projects that I have actually completed.</p>
<p>Over the past week, Google has been sending out reminders that their support for Google Maps API v2 was ending. They were going to provide a wrapper to try and support the old API. With the six-man football season in the middle of the playoffs, I was trying to put this off for at least a few more weeks. Unfortunately that all changed when my maps went blank a few days ago.</p>
<p>As usual, I hit the place where I tried to find a blog or post where combining MySQL, PHP and GM v3 all went together. I also just starred at the screen for what seemed to be an eternity.</p>
<p>I am here to tell you, Google Maps v3 is great. Converting the data points to XML, then plotting them is really quite simple.</p>
<p>The example I am going to post might seem a bit long, but it is a modified version of the <a href="http://developers.google.com/maps/articles/phpsqlajax_v3" title="google maps">explanation on the google developer site</a>, retold in terms humans without too, too much experience can decipher.</p>
<p>First off, you need to create the XML file.</p>
<p>The example I am using is taken from my own website, sixmanfootball.com. This file is used to populate two maps, including the one on the <a href="http://sixmanfotball.com/">index page</a> and the <a href="http://sixmanfootball.com/weekly_maps.php">weekly maps page</a>. It is WAY more complex than many uses, but I thought it would be good to show the details.</p>
<p>Let’s call this file, makeXML.php</p>
<pre lang="php">include('your_db_connection_file.inc');
// I like to use weird names like .inc files for hidden files
// this is something I was taught by someone somewhere
//who was wiser than me

header("Content-type: text/xml");

//function to help parse everything to XML
function parseToXML($htmlStr)
{
$xmlStr=str_replace('&lt;','&lt;',$htmlStr); $xmlStr=str_replace('&gt;','&gt;',$xmlStr);
$xmlStr=str_replace('"','"',$xmlStr);
$xmlStr=str_replace("'",''',$xmlStr);
$xmlStr=str_replace("&amp;",'&amp;',$xmlStr);
return $xmlStr;
}

//your actual db connection
$dblink = mysql_connect('localhost', $dbuser, $dbpass);
$dblinked = mysql_select_db($dbname, $dblink);

$key=13;

// Start XML file, echo parent node
echo '';

//my SQL command to get the game info
$q2 = "SELECT team_a, team_b, game_location, game_date, game_time FROM games WHERE game_time&gt;0 AND game_week=$key ORDER BY game_location, game_time DESC";
$r2 = mysql_query($q2);

while($a2 = mysql_fetch_array($r2))
{
$team_a = $a2[team_a];
$team_b = $a2[team_b];
$game_site = $a2[game_location];
$game_date = $a2[game_date];
$game_time = $a2[game_time];
$game_date=date('D',$game_date);
$game_time=$game_time = date('g:i A', $game_time);

$site_search = mysql_real_escape_string($game_site);
If ($site_search==$last_site)
{$previous=$game_name."
";} else
{$previous="";}

//sub SQL command to get the longitude and latitude
$q3 = "SELECT * FROM teams WHERE team_name='$site_search' AND team_lat&lt;&gt;0";
$r3 = mysql_query($q3);
while($a3 = mysql_fetch_array($r3))
{
$game_lat = $a3[team_lat];
$game_long = $a3[team_long];
$game_name = $previous.$team_a." vs ".$team_b." in ".$game_site." (".$game_date.", ".$game_time.")";

echo '&lt;marker ';
echo 'name="' . parseToXML($game_name) . '" ';
echo 'lat="' . $game_lat . '" ';
echo 'lng="' . $game_long . '" ';
echo 'type="stadium"';
echo '/&gt;';
}
//this is used to see if there is more than one game at a particular site
//that way the second node for that site is a combo node including both games
$last_site=$game_site;
}
// End XML file
echo '';</pre>
<p>OK, now that we have XML, you can check it by calling the page via a browser and make sure it is all working.</p>

<p>The next step is creating the page where you make the actual map. Honestly, I was scared. I hate trying to figure out what I really did 2-3 years ago. I will share some generic code that ties in with the weekly_maps page.</p>
<p>In a later post, I will share how to pass a variable to the XML page for a specific query that is not predetermined.</p>
<p>This is all javascript, but I wrap it within a PHP template page.</p>
<pre lang="javascript"></pre>
<p>So the end result looks something like this.<br/>
<a href="http://www.sixmanguru.com/wp-content/uploads/2013/11/scrnshot.png"><img alt="scrnshot" class="alignnone size-medium wp-image-21" height="229" src="http://www.sixmanguru.com/wp-content/uploads/2013/11/scrnshot-300x229.png" width="300"/></a><br/>
Here’s a photo when someone clicks a map bubble.</p>
<p><a href="http://www.sixmanguru.com/wp-content/uploads/2013/11/scrnshot2.png"><img alt="scrnshot2" class="alignnone size-medium wp-image-23" height="237" src="http://www.sixmanguru.com/wp-content/uploads/2013/11/scrnshot2-300x237.png" width="300"/></a></p>
