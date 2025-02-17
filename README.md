# World-of-Warcraft-Data-Analysis Using SQL (Coming soon)
![Στιγμιότυπο οθόνης 2025-02-06 004828](https://github.com/user-attachments/assets/43b6c76e-01f1-4503-86b3-d17b815e2efa)

Since I’m a huge fan of Blizzard Entertainment, I wanted to bring my passion for World of Warcraft into data analysis by working with actual WoW data.

What is World of Warcraft? WoW is the top 1 online MMORPG game for the last 21 years. 

This project is based on the "WoW Avatar History" dataset from Kaggle.
To make this project as immersive and authentic as possible, I structured it like a real Blizzard support ticket, similar to the ones I’ve received over the years.
Banner Logo is a fan made creation since there are copyrights.

![Hazagoza's Re(quest)](https://github.com/user-attachments/assets/6782d092-9325-4895-8163-007a96f055d5)

# Project Overview
The dataset consists of player records, including race, class, level, location, and timestamps.

The goal is to identify trends in player behavior by analyzing:
1 - Most popular leveling zones.
2 - Most common class/race combinations.
3 - Max-level player locations.
4 - Dead zones (least active areas).
5 - Faction-based trends (Horde focus in this dataset)

This project demonstrates SQL techniques, including:
✔ JOINs (INNER, LEFT, RIGHT, FULL).
✔ Aggregations (COUNT, AVG, SUM).
✔ Filtering with WHERE, HAVING, and ORDER BY.
✔ Case-When statements.

# Dataset Description
We use four tables in the database(wow):

a. wowah_data - Core player data (character ID, level, race, class, zone, guild, timestamp).
b. zones - Zone details (name, continent, control faction, min/max level).
c. locations - Game version & location details (map ID, type, name).
d. location_coords - Coordinates for major game locations.

# An Overview of some of our Data

![Data overview](https://github.com/user-attachments/assets/4746a0c2-5e9e-4566-a15e-af2f20cf9822)

RENAME TABLE wowah_data TO wow_players;

>Table wowah_data converted to wow_players to be more relevant to the data we have, and "char" column to "chara" (since char is used by SQL as a specific key).

ALTER TABLE wow_players 
RENAME COLUMN `char` TO chara;

>"Chara" Column is the one that includes every unique player to our Data set and by using ->

SELECT COUNT(DISTINCT chara) AS unique_players
FROM wow_players;

>We find the total unique players #5418

SELECT COUNT(*) FROM wow_players AS even_dublicates;

>Since someone might have multiple characters in the game, the total number of ALL players are #412946

# Question 1.	How many players are at each level? / What is the most common level?

![1-Players Distribution](https://github.com/user-attachments/assets/f86bbf00-4a0f-4c68-a527-685d1191fad7)

Key insights: 
-
The majority of players fall within 61-70 level range, making it the most populated category.
On the other hand, players that fall within 1-20 is the least poplated category.
A possible explanation for our results might be that many players enjoy leveling until the Max level.
>By using case when statement we are trying to form our data result to be less overwhelming.

# Question 2. What is the most popular/visited leveling zones?

![Most popular leveling zones](https://github.com/user-attachments/assets/d8469b51-9743-4867-9606-7d0abdd02bae)

Key insights:
-
As we can see in the screenshot above, we notice that Shattrath City is the most visited area. Shattrath City is one of the capital cities so as Orgrimmar. Arathi Basin is a PvP area which people's characters fight against each other. By that saying, our results lead to the fourth option which is Terokkar Forest.
Those 2 cities are the most common visited since either people "park" their character until the next login or they just want to meet with their friends. Arathi Basin its a "mode" that you can simply join so you can fight. Terrokar Forest is the actual and most common area for leveling, plenty of activities(Dungeons, Questing, farming materials)
