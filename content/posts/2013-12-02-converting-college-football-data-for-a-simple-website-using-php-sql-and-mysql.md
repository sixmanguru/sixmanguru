---
title: "Converting College Football Data for a Simple Website, using PHP, SQL and MySQL"
date: 2013-12-02T22:40:07+00:00
slug: "converting-college-football-data-for-a-simple-website-using-php-sql-and-mysql"
author: "granger"
draft: false
tags:
  - "Oracle"
  - "College Football"
  - "PHP"
  - "SQL"
  - "MySQL"
---

<p>The pages discussed here can be found at: <a href="http://www.sixmanguru.com/ncaa13.php">http://www.sixmanguru.com/ncaa13.php</a></p>
<p>The idea of this project came from a thought that there does not exist a single place where you can see NCAA college football teams’ records and schedules easily, without having to make a bunch of clicks on very ‘graphically full’ websites.</p>
<p>The first step was to see if the data could be found easily. This was done easily, as Peter Wolfe keeps this information updated daily. (<a href="http://prwolfe.bol.ucla.edu/cfootball/scores.htm">http://prwolfe.bol.ucla.edu/cfootball/scores.htm</a>). Wolfe is a member of the official BCS rankings and also includes a comprehensive listing of conferences as well.</p>
<p>I initially broke the data we collected into four tables, listed on the top of the tables list (<a href="http://sixmanguru.com/stuff/p2-tables-2.pdf">p2-tables-2.pdf</a>). These tables are essentially the data in its raw form with some ‘cleaning’ taking place.</p>
<p>Next was to build the website. Based on this blog, a template was created to host the site. The entry page is <a href="http://www.sixmanguru.com/ncaa13.php">http://www.sixmanguru.com/ncaa13.php</a>.</p>
<p>The thought was to have a way to separate the various divisions of college football (NCAA I, NCAA I FBS, NCAA II, NCAA III and so on). This was accomplished by having a link for each at the top of the page that will pass a variable back to the site if clicked.</p>
<p>Once a division variable is passed (NCAA I BCS is assumed if there is a direct click to the site), there is a drop-down menu to filter the teams by conferences. ($q = “SELECT Conf_ID,conference_names FROM Conferences WHERE Div_ID='”.$division_id.”‘ ORDER BY conference_names”;)</p>
<p>Once a selection is made, the website show the conference standings, including conference wins, conference losses, wins and losses. This query only access the ‘cached’ table, big_team_records, we created, but more on this later. ($q = “SELECT * FROM big_team_records JOIN Conferences ON big_team_records.conference=Conferences.conference_names WHERE Conferences.Conf_ID='”.$conf_id.”‘ ORDER BY conf_wins DESC, wins DESC”;)</p>
<p>All teams shown in the results are ‘clickable’. If clicked, they link to another page (<a href="http://sixmanguru.com/team.php?t=1420">teams.php</a>), passing the team ID. The team page then shows the data from the game file, including date, team, W/L and result. ($q = “SELECT * FROM big_game_table WHERE team_a='”.$team_name.”‘ OR team_b='”.$team_name.”‘ ORDER BY game_date ASC”;)</p>
<p>The first big problem was to create SQL code that would take what we have and create team records, including conference records. Since you have to create separate joins for the two sides of the scores when calculating wins/losses for a team, this can put a strain on the server, especially one that is online. When we got into also trying to calculate the conference wins/losses as well, it really made no sense with the MySQL server we were running.</p>
<p>The solution was to create ‘leftside’ and ‘rightside’ views, then combine them in another view, whole_game. This was all done on the Oracle SQL server. The view for the team_record was also done on the Oracle SQL server. Both of the finish product views were then imported to tables. These tables were then exported to Excel files and imported to the MySQL server.</p>
<p>This may be a little more work than initially anticipated, but the end result creates a much faster and flexible solution. The large game table that was created can be used to create much more interactivity with website visitors in the future, since all games are coded with each team’s individual and conference ID.</p>

<p>One other issue we had was that the date the initial data included worked fine for Oracle SQL, but not MySQL. This is shown below, but we took care of this by added some formatting for the initial view, so this would be invisible.</p>
<p>TO_CHAR(game_date, ‘YYYY-MM-DD’) AS game_date<br/>
This little bit of code had to be added since the date format used by the website is was scraped form uses a format compatible in our Oracle SQL db, BUT NOT in our MySQL db.</p>
<p>After the main four tables are created, we create master tables to essentially be used as cache in the MySQL database for the website. Their implementation is good, but allows for expansion of searches.</p>
<p><strong>THIS MAKES THE ENTIRE VISITOR SIDE WORK</strong></p>
<p><span style="line-height: 1.5;">CREATE VIEW leftside AS SELECT ncaascores2013.game_ID, TO_CHAR(game_date, ‘YYYY-MM-DD’) AS game_date, fbteams_2013.team_ID AS VID, FBConferences.Conf_ID AS V_CID, ncaascores2013.team_a, ncaascores2013.score_a</span></p>
<p>FROM ncaascores2013<br/>
INNER JOIN fbteams_2013<br/>
ON ncaascores2013.team_a = fbteams_2013.team_name<br/>
INNER JOIN FBConferences<br/>
ON FBConferences.conference_names = fbteams_2013.conference</p>
<p><strong>THIS MAKES THE ENTIRE HOME SIDE WORK</strong></p>
<p>CREATE VIEW rightside AS SELECT ncaascores2013.game_ID, fbteams_2013.team_ID AS HID, FBConferences.Conf_ID AS H_CID, ncaascores2013.team_b, ncaascores2013.score_b, ncaascores2013.site<br/>
FROM ncaascores2013<br/>
INNER JOIN fbteams_2013<br/>
ON ncaascores2013.team_b = fbteams_2013.team_name<br/>
INNER JOIN FBConferences<br/>
ON FBConferences.conference_names = fbteams_2013.conference</p>
<p><strong>COMBINE THEM</strong></p>
<p>CREATE VIEW whole_game AS SELECT leftside.game_ID, leftside.game_date, leftside.VID, leftside.V_CID, leftside.team_a, leftside.score_a,<br/>
rightside.HID, rightside.H_CID, rightside.team_b, rightside.score_b, rightside.site<br/>
FROM leftside<br/>
JOIN rightside<br/>
ON leftside.game_ID=rightside.game_ID</p>
<p><strong>MAKE A TABLE TO THEM PUT THE VIEW DATA IN</strong></p>
<p>create the new table from the view<br/>
CREATE TABLE tblWholeGame AS SELECT *<br/>
FROM whole_game;</p>
<p><strong>IMPORT THE DATA TO THE TABLE</strong></p>
<p><strong>INSERT INTO tblwholegame</strong><br/>
<strong> SELECT *</strong><br/>
<strong> FROM whole_game;</strong></p>
<p><strong>THIS DATA IS THEN EXPORTED TO USE IN THE OTHER ONLINE MYSQL DATABASE</strong></p>
<p><strong>THIS CREATES THE INITIAL TEAM_RECORD VIEW</strong></p>
<p>CREATE view team_record AS SELECT<br/>
team_name,<br/>
SUM(CASE WHEN (team_ID=VID AND score_a&gt;score_b) OR<br/>
(team_ID=HID AND score_b&gt;score_a) THEN 1 ELSE 0 END) AS wins,<br/>
SUM(CASE WHEN (team_ID=VID AND score_a&lt;score_b) OR<br/>
(team_ID=HID AND score_b&lt;score_a) THEN 1 ELSE 0 END) AS losses, SUM(CASE WHEN (team_ID=VID AND score_a&gt;score_b AND whole_game.V_CID=whole_game.H_CID) OR<br/>
(team_ID=HID AND score_b&gt;score_a AND whole_game.H_CID=whole_game.V_CID) THEN 1 ELSE 0 END) AS conf_wins,<br/>
SUM(CASE WHEN (team_ID=VID AND score_a&lt;score_b AND whole_game.V_CID=whole_game.H_CID) OR<br/>
(team_ID=HID AND score_b&lt;score_a AND whole_game.V_CID=whole_game.H_CID) THEN 1 ELSE 0 END) AS conf_losses<br/>
FROM fbteams_2013,whole_game<br/>
GROUP BY team_name<br/>
ORDER BY team_name</p>
<p><strong>WE THEN ADD SOME ADDITONAL DATA TO THIS</strong></p>
<p>CREATE VIEW big_team_record AS SELECT fbteams_2013.team_id, fbteams_2013.division,fbteams_2013.conference,team_record.*<br/>
FROM fbteams_2013, team_record<br/>
WHERE fbteams_2013.team_name=team_record.team_name;</p>
<p><strong>CREATING THE TABLE</strong></p>
<p>CREATE TABLE tblBigTeamRecord AS SELECT *<br/>
FROM big_team_record;</p>
<p><strong>IMPORTING THE DATA TO THE TABLE</strong></p>
<p>INSERT INTO tblbigteamrecord<br/>
SELECT *<br/>
FROM big_team_record;</p>
<p>AGAIN, THIS DATA MUST BE EXPORTED TO THE ONLINE MYSQL DATABASE</p>
