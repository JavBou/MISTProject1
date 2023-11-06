# MIST Group Project 1


## Team Name

cs_g5p1


## Team Members

1. Javi Bou [@JavBou](https://github.com/Javbou)
2. Sebastian Taborda [@SebastianTaborda1](https://github.com/SebastianTaborda1)
3. Coleman Leathers [@cleatherss](https://github.com/cleatherss)
4. Matt Pietri [@MattPietri](https://github.com/MattPietri)
## Problem Description

Our task was to construct a relational database for a football club. Our central entity, teams, represents the numerous teams that are formed within the football club. These teams are comprised of players, coaches, and sponsors, all of whom participate in numerous matches. We're also modeling other aspects surrounding the teams, such as social media, injuries, etc. Our goal is to accurately model these various relationships, generating sample data sets, and populating our table and attributes with the same data to showcase the performance and effectiveness of the model. We're also aiming to perform various queries on this data model to highlight key metrics and insights surrounding the operations and functionality of the football club.
## Data Model

Our model is based around the structure of a football club. The main entity in the model, teams, is representative of the different football teams that are all within the club. Teams are identified with an ID and include a team name.

Each team is comprised of multiple players, held within the Players entity. Each player has a unique ID, first and last name, age, date of birth, and position that they play. It is also possible for a player to be a part of more than one team, thus creating a many to many relationship between players and teams and an associative contracts entity. This entity contains both the player ID and team ID, as well as the contract salary and start and end dates as its attributes.

There are two more branches that come from the Players table. The first is a one to many relationship with the Scouting Reports entity, which contains a report ID, date, note, and the respective player ID. A player can have many scouting reports. The last relationship with the Players entity consists of a one to many relationship with the Injuries entity. The injury ID, date, status, type, and player are all included. As a player can have many injuries, but a specific injury can only be tied to one player, we include a one to many relationship.

Teams also have multiple coaches, represented by a one to many relationship with the Coaches entity. This contains the coach ID, name, and task. Teams also participate in many practices, establishing a one to many relationship with the Practice entity, which contains a unique ID and the date and time of the practice. The Practice entity also has a one to many relationship with the Coaches entity, as multiple coaches can attend one practice.

Teams play in matches, and each match is played with multiple teams, creating a many to many relationship with Schedule as the associative entity. The Schedule entity details the match that is being played and the teams that are playing in that match. The Matches entity includes a match ID, as well as the match date and time. As matches can take place in many different places, we included a one to many relationship between Stadiums and Matches.

Finally, teams have multiple Sponsors, Medical Staff, Social Media Accounts, and Jerseys. All four of these entities have a one to many relationship with the Teams table. The Sponsors entity details the sponsor ID, name, and sponsor amount (in dollars). The Medical Staff entity is comprised of a staff ID, name, and role of the staff member. The Jerseys entity includes the jersey ID, home and away colors, and number. Finally, the Social Media Accounts entity is comprised of the account ID, platform, followers, and username.


![Logo](https://imgur.com/1YI3d8g.png)


## Data Dictionary

### Player Table

![Table 1](https://i.imgur.com/A0nimuP.png)

### Scouting Reports Table

![Table 2](https://i.imgur.com/DVqdK3G.png)

### Injuries Table

![Table 3](https://i.imgur.com/T0bDQWv.png)

### Contracts Table

![Table 4](https://i.imgur.com/xVCifn1.png)

### Teams Table

![Table 5](https://i.imgur.com/6odtQlF.png)

### Schedule Table

![Table 6](https://i.imgur.com/YsGZv0M.png)

### Stadiums Table

![Table 7](https://i.imgur.com/qg3T2GD.png)

### Matches Table

![Table 8](https://i.imgur.com/qdshPTe.png)

### Sponsors Table

![Table 9](https://i.imgur.com/m8y5c4F.png)

### Medical Staff Table

![Table 10](https://i.imgur.com/ld3FwJs.png)

### Coaches Table

![Table 11](https://i.imgur.com/sT05qlp.png)

### Practice Table

![Table 12](https://i.imgur.com/1GyRy7k.png)

### Social Media Accounts Table

![Table 13](https://i.imgur.com/hrN0sSZ.png)

### Jerseys Table

![Table 14](https://i.imgur.com/a8PBinO.png)
## Queries

![Query Table]()

### Query 1

![Query 1]()

Query 1 lists the players full names, their respectives positions, as well as their salaries. Only players who's salaries are higher than the total average salary are displayed. The salaries are then organized from highest to lowest and grouped based on position.

This query allows for coaches and other team administrators to know which players are being paid more than others and by how much. This can be useful to see if any players are being overpaid, or to detect and standout players that are deserving of their higher salaries. Listing the results from highest to lowest salary make it easier to view these detials. Grouping the results by position can also be useful to see if a particular position is being paid more than others regardless of performance. This query can also be easily edited to show players who earn less than the average to see the same detailed information on the other end of the spectrum.

### Query 2

![Query 2]()

Query 2 lists all of the players who play in the Quarterback position that have suffered a knee injury.

This query is extreemly useful in finding commonalities between player's positions and the injuries that they sustain during their games. Moreover, it's useful because as coaches, viewing the quarterbacks with knee injuries is critical in determining who will play in specific games. This query can also be altered by changing the respective postions or injuries to get more comprehensive data on different positions and what injuries are most common in each position.

### Query 3

![Query 3]()

Query 3 lists all the teams that have a social media account with more than 500,000 followers.

This query can be used to track different social media trends across the different teams in the league. Coaches and team administrators can track which teams have a higher social media presence than others, which can be used to establish a possible relationship between team/player performance and social media following. It can also be used to indentify coorelations between winrates, salary, and other key metrics.

### Query 4

![Query 4]()

Query 4 lists the two teams that played one another on November 1st in Atlanta.

While this query is specific to an individual match, it can be altered to detect the teams involved in any match in any locaton during any date. This is useful in determining the specific teams that played in matches, as well as identifying different trends or patterns as it related to players and the locations they play at.

### Query 5

![Query 5]()

This query lists all the teams in the league along with the amount of medical staff that they have.

This query is useful in learning how many medical personnel there are in each team. The information from this query can be used in determining coorelations between the amount of medical staff that a team has along with factors such as injuries, win rate, and overall player performance.

### Query 6

![Query 6]()

Query 6 identifies the team that has the most social media followers amongst the teams that wear red home jerseys. The query also lists the amount of followers that the team has.

This query is moreso a fun exercise measuring the amount of social media followers that the highest-followed team with red home jerseys has. While not directly measuring a statistic, this query could be used to establish possible coorelations between the team's social media following and their jersey color.

### Query 7

![Query 7]()

Query 7 lists all the sponsor names and their respective donation amounts for teams that have less than three sponsors.

This query is useful in detemining which teams not only have a low amount of sponsors, but if those respective sponsors tend to give higher or lower amounts depending on the total amount of sponsors that a team has. This query can also be used in determing possible relationships between number of sponsors and player performance or salary.

### Query 8

![Query 8]()

Query 8 lists all of the teams in the league that do not have a Facebook account

This query can mainly be used to quickly gather the teams that do not have a Facebook account associated with their team. This information can then be used to idenfity possible coorelations between a team having a Facebook account and things like their audience engagement, performance, as well as how active they are on their other social media platforms.

### Query 9

![Query 9]()

Query 9 shows the amount of teams that held a practice on November 5th, 2023.

This is a more simplified query showing us the teams that held a practice on a specific date, in this case November 5th, 2023. This query can easily be altered to different dates to see which teams have held practices on specific dates. This information can also be used to establish trends based on teams that prefer to hold practice on specific dates.

### Query 10

![Query 10]()

Query 10 lists all of the offensive coaches that play on the Falcons team.

This query can be used mainly to identify all of the offensive coaches on the Falcons team. This can be useful to identify specific coaches on the team that stand out or some that are performing at a lower level than needed. This query can also be changed to target other coaching types (like defensive or special teams) as well as different teams.
