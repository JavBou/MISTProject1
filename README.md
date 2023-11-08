
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
## Chat GPT

To get a framework for our data model, we utilized chat GPT to generate initial concepts for tables, attributes, and relationships, surrounding a hypothetical football club. While we did utilize many of ChatGPT's entities and attributes in our final model, we made some edits with regards to the types of tables used (ie: we did not include the travel itineraries entity) and recommended relationships (ie: rather than having a many to many with medical staff and players, we created a one to many with between medical staff and teams).

### The input prompt is as follows:

Pretend you are the owner/operator of a football club needing to build a relational database. You hired some students from the MIST 4610 class at the University of Georgia to create the database for you. They need to know more about your organization to identify which entities, attributes, and relationships are important for you. Start by describing your business as a real client. Use 12 -15 entities

### ChatGPT then gave the following response:

Certainly! As the owner/operator of a football club, here's an overview of my business to help the MIST 4610 class students in building a relational database.

Players:
- Attributes: Player ID, Name, Position, Date of Birth, Nationality
- Relationships: Many-to-One with Contracts, Many-to-Many with Teams

Teams:
- Attributes: Team ID, Team Name, Coach ID, Formation
- Relationships: One-to-Many with Players, One-to-Many with Matches

Coaches:
- Attributes: Coach ID, Name, Specialization, Nationality
- Relationships: One-to-Many with Teams, One-to-Many with Training Sessions

Matches:
- Attributes: Match ID, Date, Time, Location, Opponent Team ID, Result
- Relationships: Many-to-Many with Teams

Stadiums:
- Attributes: Stadium ID, Stadium Name, Location, Capacity
- Relationships: One-to-Many with Matches

Contracts:
- Attributes: Contract ID, Player ID, Team ID, Start Date, End Date, Salary
- Relationships: Many-to-One with Players, Many-to-One with Teams

Sponsors:
- Attributes: Sponsor ID, Sponsor Name, Sponsorship Amount, Duration
- Relationships: Many-to-Many with Teams

Injuries:
- Attributes: Injury ID, Player ID, Date, Type, Status
- Relationships: Many-to-One with Players

Training Sessions:
- Attributes: Session ID, Coach ID, Team ID, Date, Time
- Relationships: Many-to-One with Coaches, Many-to-One with Teams

Scouting Reports:
- Attributes: Report ID, Scout ID, Player ID, Date, Notes
- Relationships: Many-to-One with Players

Fan Clubs:
- Attributes: Fan Club ID, Club Name, President, Number of Members
- Relationships: Many-to-Many with Matches

Jersey Kits:
- Attributes: Kit ID, Team ID, Home Color, Away Color, Sponsor Logo
- Relationships: One-to-Many with Teams

Social Media Accounts:
- Attributes: Account ID, Team ID, Platform, Username, Followers
- Relationships: One-to-Many with Teams

Medical Staff:
- Attributes: Staff ID, Name, Position, Contact Information
- Relationships: Many-to-Many with Players

Travel Itineraries:
- Attributes: Itinerary ID, Team ID, Departure Date, Return Date, Destination
- Relationships: One-to-Many with Teams

These entities and their relationships should provide a solid foundation for the MIST 4610 class to design a relational database that meets the requirements of my football club.

### Our Response
Specify the many to many relationships and what to call them.

### ChatGPT's Response

Players - Teams (Many-to-Many) - "Belongs To" relationship:
- Attributes: Player ID, Team ID
- This relationship represents the fact that a player can belong to multiple teams over time, and a team can have multiple players.
Matches - Teams (Many-to-Many) - "Participates In" relationship:
- Attributes: Match ID, Team ID
- This relationship signifies that a match involves multiple teams, and a team can participate in various matches.
Contracts - Players (Many-to-Many) - "Includes" relationship:
- Attributes: Contract ID, Player ID
- This relationship indicates that a player can have multiple contracts over their career, and a contract can include multiple players.
Sponsors - Teams (Many-to-Many) - "Sponsors" relationship:
- Attributes: Sponsor ID, Team ID
- This relationship signifies that a sponsor can support multiple teams, and a team can have support from multiple sponsors.
Training Sessions - Coaches (Many-to-Many) - "Conducts" relationship:
- Attributes: Session ID, Coach ID
- This relationship indicates that a coach can conduct multiple training sessions, and a training session can be conducted by multiple coaches.
Fan Clubs - Matches (Many-to-Many) - "Supports" relationship:
- Attributes: Fan Club ID, Match ID
- This relationship represents the fact that a fan club can support multiple matches, and a match can have support from multiple fan clubs.
Medical Staff - Players (Many-to-Many) - "Provides Medical Care To" relationship:
- Attributes: Staff ID, Player ID
- This relationship signifies that medical staff can provide care to multiple players, and a player can receive care from multiple members of the medical staff.

These names give clarity to the nature of the relationships and make it easier for the MIST 4610 class to understand the connections between different entities in the relational database.
## Data Model

Our model is based around the structure of a football club. The main entity in the model, teams, is representative of the different football teams that are all within the club. Teams are identified with an ID and include a team name.

Each team is comprised of multiple players, held within the Players entity. Each player has a unique ID, first and last name, age, date of birth, and position that they play. It is also possible for a player to be a part of more than one team, thus creating a many to many relationship between players and teams and an associative contracts entity. This entity contains both the player ID and team ID, as well as the contract salary and start and end dates as its attributes.

There are two more branches that come from the Players table. The first is a one to many relationship with the Scouting Reports entity, which contains a report ID, date, note, and the respective player ID. A player can have many scouting reports. The last relationship with the Players entity consists of a one to many relationship with the Injuries entity. The injury ID, date, status, type, and player are all included. As a player can have many injuries, but a specific injury can only be tied to one player, we include a one to many relationship.

Teams also have multiple coaches, represented by a one to many relationship with the Coaches entity. This contains the coach ID, name, and task. Teams also participate in many practices, establishing a one to many relationship with the Practice entity, which contains a unique ID and the date and time of the practice. The Practice entity also has a one to many relationship with the Coaches entity, as multiple coaches can attend one practice.

Teams play in matches, and each match is played with multiple teams, creating a many to many relationship with Schedule as the associative entity. The Schedule entity details the match that is being played and the teams that are playing in that match. The Matches entity includes a match ID, as well as the match date and time. As matches can take place in many different places, we included a one to many relationship between Stadiums and Matches.

Finally, teams have multiple Sponsors, Medical Staff, Social Media Accounts, and Jerseys. All four of these entities have a one to many relationship with the Teams table. The Sponsors entity details the sponsor ID, name, and sponsor amount (in dollars). The Medical Staff entity is comprised of a staff ID, name, and role of the staff member. The Jerseys entity includes the jersey ID, home and away colors, and number. Finally, the Social Media Accounts entity is comprised of the account ID, platform, followers, and username.

![Model](https://i.imgur.com/eE1RbNR.png)

## Data Dictionary

### Player Table

![Table 1](https://i.imgur.com/tWV94u9.png)

### Scouting Reports Table

![Table 2](https://i.imgur.com/jJwlYbs.png)

### Injuries Table

![Table 3](https://i.imgur.com/Rdd1Hsi.png)

### Contracts Table

![Table 4](https://i.imgur.com/sFfdWMb.png)

### Teams Table

![Table 5](https://i.imgur.com/biY41C3.png)

### Schedule Table

![Table 6](https://i.imgur.com/xEn5GC0.png)

### Stadiums Table

![Table 7](https://i.imgur.com/CtH0276.png)

### Matches Table

![Table 8](https://i.imgur.com/rVdeZPC.png)

### Sponsors Table

![Table 9](https://i.imgur.com/PBZXXrp.png)

### Medical Staff Table

![Table 10](https://i.imgur.com/PPRIJlS.png)

### Coaches Table

![Table 11](https://i.imgur.com/AsXIyYt.png)

### Practice Table

![Table 12](https://i.imgur.com/lPBltIo.png)

### Social Media Accounts Table

![Table 13](https://i.imgur.com/wcC9mcx.png)

### Jerseys Table

![Table 14](https://i.imgur.com/Kuucgs1.png)
## Queries

![Query Table](https://i.imgur.com/erJTkxR.png)

### Query 1

![Query 1](https://i.imgur.com/cmhEcKn.png)

Query 1 lists the players full names (in the form of last, first) their respectives positions, as well as their salaries. Only players who's salaries are higher than the total average salary are displayed. The salaries are then organized from highest to lowest.

This query allows for coaches and other team administrators to know which players are being paid more than others and by how much. This can be useful to see if any players are being overpaid, or to detect and standout players that are deserving of their higher salaries. Listing the results from highest to lowest salary make it easier to view these detials. Grouping the results by position can also be useful to see if a particular position is being paid more than others regardless of performance.

### Query 2

![Query 2]()

Query 2 lists all of the players who play in the Quarterback position that have suffered a knee injury. Their current injury status is also displayed.

This query is extreemly useful in finding commonalities between player's positions and the injuries that they sustain during their games. Moreover, it's useful because, as coaches, viewing the quarterbacks with knee injuries is critical in determining who will play in specific games.

### Query 3

![Query 3](https://i.imgur.com/aRdDCpn.png)

Query 3 lists all the teams that have an Instagram account with a follwer count greater than the average amungst all teams.

This query can be used to track different Instagram trends across the different teams in the league. Coaches and team administrators can track which teams have a higher social media presence than others, which can be used to establish a possible relationship between team/player performance and social media following. It can also be used to indentify coorelations between winrates, salary, and other key metrics.

### Query 4

![Query 4](https://i.imgur.com/OngUAAp.png)

This query lists all the teams in the league along with their combined social media folllowers and the amount of medical staff that they have.

This query is useful in learning how many medical personnel there are in each team. The information from this query can be used in determining coorelations between the amount of medical staff that a team has along with factors such as injuries, win rate, and overall player performance. Moreover, the information found in this query can tie the amount of social media followers a team has to the amount of medical staff they have. Using this, you can find a possible coorelation between social media presence and medical staff.

### Query 5

![Query 5](https://i.imgur.com/3PXcKTE.png)

Query 5 identifies the average player age of teams that have a home jersey color of red.

This query can be used when team coaches are determining jersey color. They'd be able to identify what jersey colors are associated with teams of varying ages and thus could select a color reflective of that team's specific age. This data could also be used to identify trends related to how teams with specific jersey colors perform in games relative to their age.

### Query 6

![Query 6](https://i.imgur.com/YtkqKya.png)

Query 6 lists all the distinct sponsor names and their respective donation amounts for teams that have less than three sponsors.

This query is useful in detemining which teams not only have a low amount of sponsors, but if those respective sponsors tend to give higher or lower amounts depending on the total amount of sponsors that a team has. This query can also be used in determing possible relationships between number of sponsors and player performance or salary.

### Query 7

![Query 7](https://i.imgur.com/jVaE6wy.png)

Query 7 lists the teams in the league that do not have a Facebook account along with their average sponsor amounts. This is shown through a new "AverageSponsorAmount" column.

This query can mainly be used to understand the relationship between the amount that a team recieves from sponsors on average and the social media accounts they have, specifically Facebook. This could lead to possible claims that having an increased social media presence through more accounts can lead to higher sponsor amounts.

### Query 8

![Query 8](https://i.imgur.com/R6bfJYE.png)

Query 8 shows the amount of teams that held a practice on September 2nd, 2023.

This is a more simplified query showing us the teams that held a practice on a specific date, in this case September 2nd, 2023. This query can easily be altered to different dates to see which teams have held practices on specific dates. This information can also be used to establish trends based on teams that prefer to hold practice on specific dates.

### Query 9

![Query 9](https://i.imgur.com/EmS1lez.png)

Query 9 locates and lists the Head Coach for the Falcons team.

This query can be used mainly to identify the leader for the Falcons team. This query can also be altered depending on what team you're looking to find the head coach for. Mostly this would be use for getting in contact with specific team leaders.

### Query 10

![Query 10](https://i.imgur.com/nk1rE24.png)

Query 10 lists all of the different teams that Subway has sponsored. The results are listed under a newly created "TeamsSponsored" column.

This query can be mainly used for Subway, a popular sponsor for the teams, to identify the number of teams that they've sponsored so far in the league. This data can be used when determining if the sponsor should be collaborating with more or less teams in the league.
## Databse Information

#### Database Name: cs_g5p1

#### Query Procedures:
Each query listed above is saved in the database using stored procedures which can be called using the following command (x being the question name):

`CALL TP_Q(x);`
