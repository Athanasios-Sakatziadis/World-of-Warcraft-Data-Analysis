# World-of-Warcraft-Data-Analysis Using SQL
![Στιγμιότυπο οθόνης 2025-02-06 004828](https://github.com/user-attachments/assets/43b6c76e-01f1-4503-86b3-d17b815e2efa)

Since I’m a huge fan of __Blizzard Entertainment__, I wanted to bring my passion for __World of Warcraft__ into data analysis by working with actual WoW data.

What is World of Warcraft? WoW is the top 1 online MMORPG game for the last 21 years. 

This project is based on the __"WoW Avatar History"__ dataset from Kaggle.
To make this project as immersive and authentic as possible, I structured it like a real Blizzard support ticket, similar to the ones I’ve received over the years.
Banner Logo is a fan made creation since there are copyrights.

![Hazagoza's Re(quest)](https://github.com/user-attachments/assets/bdd72537-b5ee-4787-be64-94cecfe7e13d)


# Project Overview
The dataset consists of player records, including race, class, level, location, and timestamps.

The goal is to identify trends in player behavior by analyzing:


1 - __How many players are at each level / What is the most common level.__


2 - __Most popular/visited leveling zones.__


3 - __Max-level player locations.__


4 - __Faction & class breakdown.__


5 - __PvP - PvE or something else?__



This project demonstrates SQL techniques, including:


✔ __JOINs (LEFT).__


✔ __Aggregations (COUNT, AVG, SUM, MAX).__


✔ __Filtering with WHERE, and ORDER BY, GROUP BY.__


✔ __Case-When statement.__

# Dataset Description
We use four tables in the database(wow):

a. __wowah_data__ - Core player data (character ID, level, race, class, zone, guild, timestamp, etc).
b. __zones__ - Zone details (name, continent, control faction, min/max level).
c. __locations__ - Game version & location details (map ID, type, name).
d. __location_coords__ - Coordinates for major game locations.

>We will use some of them for our data analysis.

# Data Overview

![Data overview](https://github.com/user-attachments/assets/4746a0c2-5e9e-4566-a15e-af2f20cf9822)

__RENAME TABLE__ wowah_data __TO__ wow_players_cleaned;

__RENAME TABLE__ zones __TO__ wow_zones_cleaned;

>Table wowah_data converted to wow_players_cleaned to be more relevant to the data we have, and "char" column to "chara" (since char is used by SQL as a specific key).

*The Data has been cleaned*

__ALTER TABLE__ wow_players_cleaned 
__RENAME COLUMN__ `char` __TO__ chara;

>"Chara" Column is the one that includes every unique player to our Data set and by using :

__SELECT COUNT(DISTINCT__ chara) __AS__ unique_players
__FROM__ wow_players_cleaned;

>We find the total unique players #5418

__SELECT COUNT__(*) __FROM__ wow_players __AS__ even_dublicates;

>Since someone might have multiple characters in the game, the total number of ALL players are #412.946

# Question 1.	How many players are at each level? / What is the most common level?

![How many players are at each level- What is the most common level](https://github.com/user-attachments/assets/5ea9f038-58e1-4ea8-87fc-7c5fc8f51cdf)


Key insights: 
-
The majority of players fall within 61-70 level range, making it the most populated category.
On the other hand, players that fall within 1-20 is the least poplated category.
A possible explanation for our results might be that many players enjoy leveling until the Max level.
>By using case when statement we are trying to form our data result to be less overwhelming.

# Question 2. What is the most popular/visited leveling zones?

![most popular-visited leveling zones](https://github.com/user-attachments/assets/8dff320a-6f2d-4b92-be56-76eeffea362b)

Key insights:
-
As we can see in the screenshot above, we notice that Orgrimmar is the most visited area(unique IDs). Orgrimmar is one of the capital cities so as Shattrath City. By that saying, our results lead to the Third option which is Terokkar Forest.
Those 2 cities are the most common visited since either people "park" their character until the next login or they just want to meet with their friends. Terrokar Forest is the actual and most common area for leveling, plenty of activities(Dungeons, Questing, farming materials). Also the avarage level of players in the most common area is 60.56

# Question 3. Where do max-level players spend their time?

![Where do max-level players spend their time](https://github.com/user-attachments/assets/a7a6ff14-edf8-43ab-b74e-797fe7f524d5)


Key insights:
-
Due to our results, people prefering to spend the most of their time in the capital city(manipulate auction house prices, selling and buying, chatting) instead raiding(Tempest Keep) or PvP (Warsong Gulch).

# Question 4. How many hordes are there? / what are the most popular class/race combination?

![class-race combination](https://github.com/user-attachments/assets/1215572f-342d-4f00-a023-ab3c2592cb34)


Key insights:
-
To begin with, our Data has been elaborate based on one side of players, from the horde's. The majority of players are creating the combination Blood elf Paladin because back then it was the most popular race/class combination. Instead of Orc Warlock which might be less enjoyable, time consuming and demanding. The total number of ALL players are #412.946 as we mentioned above.

# Question 5. PvP / PVE or something else?

![pvp - pve or something else](https://github.com/user-attachments/assets/842ba2a4-99ba-4d24-961d-0a09a9e3312f)


Key insights:
-
There are many way to enjoy the game. Due to our results it seems that people prefer to play the game casually instead of doing PvP or PvE.



![How many players are at each level- What is the most common level visualization](https://github.com/user-attachments/assets/e260f68c-0d9f-46e3-8f58-b9e98edb093d)


![most popular-visited leveling zones visualization](https://github.com/user-attachments/assets/fcc7b29c-46b2-4086-8796-e92bce28d731)


![Where do max-level players spend their time visualization](https://github.com/user-attachments/assets/59408808-9aaa-4182-ac21-b911ae527fd1)


![class-race combination visualization](https://github.com/user-attachments/assets/5badccb3-3b79-437a-9701-de2d0d416d8f)


![pvp - pve or something else visualization](https://github.com/user-attachments/assets/58ab1c22-e864-4031-919a-439627197a35)
