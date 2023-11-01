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

Our model is based on the structure of a football club. The main entity in the model, teams, is representative of the different football teams that are all within the club. Teams are identified with an ID and include a team name.

Each team is comprised of multiple players, held within the Players entity. Each player has a unique ID, first and last name, age, date of birth, and position that they play. It is also possible for a player to be a part of more than one team, thus creating a many to many relationship between players and teams, creating a roster entity. This entity contains both the player ID as well as the team ID.

There are two more branches that come from the Players table. The first is a one to many relationship with the Scounting Reports entity, which contains a report ID, date, note, and the respective player ID. A player can have many scouting reports. The last relationship with the Players entity consists of both a one to many and a one to one relationship with the Injuries entity. The injury ID, date, status, type, and player are all included. As a player can have many injuries, but a specific injury can only be tied to one player, we include a one to many relationship. We also include a one to one relationship [???]

The Injuries entity also has a many to many relationship with the Teams entity, creating the Contracts entity. This contains the Contract ID, start and end dates, and [MATCHES?]. [???]

Teams also have multiple coaches, represented by a one to many relationship with the Coaches entity. This contains the coach ID, name, and task. Teams also participate in many practices, establishing a one to many relationship with the Practice entity, which contains a unique ID and the date and time of the practice. The Practice entity also has a one to many relationship with the Coaches entity, as multiple coaches can attend one practice.

Teams play in matches, and each match is played with multiple teams, creating a one to many relationship. The Matches entity includes a match ID, as well as the match date and time. [location???]

Finally, teams have multiple Sponsors, Medical Staff, Social Media Accounts, and Jerseys. All four of these entities have a one to many relationship with the Teams table. The Sponsors entity details the sponsor ID, name, and sponsor amount (in dollars). The Medical Staff entity is comprised of a staff ID, name, and role of the staff member. The Jerseys entity includes the jersey ID, home and away colors, and number. Finally, the Social Media Accounts entity is comprised of the account ID, platform, followers, and username.
