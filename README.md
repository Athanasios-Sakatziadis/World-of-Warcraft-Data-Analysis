# World-of-Warcraft-Data-Analysis Using SQL (Coming soon)
![Στιγμιότυπο οθόνης 2025-02-06 004828](https://github.com/user-attachments/assets/43b6c76e-01f1-4503-86b3-d17b815e2efa)

Since I’m a huge fan of Blizzard Entertainment, I wanted to bring my passion for World of Warcraft into data analysis by working with actual WoW data.

What is World of Warcraft? WoW is the top 1 online MMORPG game for the last 21 years. 

This project is based on the "WoW Avatar History" dataset from Kaggle.
To make this project as immersive and authentic as possible, I structured it like a real Blizzard support ticket, similar to the ones I’ve received over the years.

![Hazagoza's Re(quest)](https://github.com/user-attachments/assets/6782d092-9325-4895-8163-007a96f055d5)

# Project Overview
The dataset consists of player records, including race, class, level, location, and timestamps.

The goal is to identify trends in player behavior by analyzing:
1 - Most popular leveling zones
2 - Most common class/race combinations
3 - Max-level player locations
4 - Dead zones (least active areas)
5 - Faction-based trends (Horde focus in this dataset)

This project demonstrates SQL techniques, including:
✔ JOINs (INNER, LEFT, RIGHT, FULL)
✔ Aggregations (COUNT, AVG, SUM)
✔ Filtering with WHERE, HAVING, and ORDER BY
✔ Data cleaning & interpretation

# Dataset Description
We use four tables in the database(wow):

a. wowah_data - Core player data (character ID, level, race, class, zone, guild, timestamp)
b. zones - Zone details (name, continent, control faction, min/max level)
c. locations - Game version & location details (map ID, type, name)
d. location_coords - Coordinates for major game locations

# An Overview of some of our Data

![Data overview](https://github.com/user-attachments/assets/4746a0c2-5e9e-4566-a15e-af2f20cf9822)


Table wowah_data converted to wow_players to be more relevant to the data we have, and "char" column to "chara" (since char is used by SQL as a specific key).

RENAME TABLE wowah_data TO wow_players;

--

ALTER TABLE wow_players 
RENAME COLUMN `char` TO chara;


"Chara" Column is the one that includes every unique player to our Data set and by using ->

SELECT COUNT(*) AS total_players FROM wow_players;

We find the total players #412946



