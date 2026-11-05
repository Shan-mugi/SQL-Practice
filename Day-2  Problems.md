/*
=========================================
DAY 2 - SQL 50 PROGRESS
=========================================
*/

-- ---------------------------------------------------------
-- Problem 1: 584. Find Customer Referee
-- ---------------------------------------------------------
-- QUESTION: 
-- Find the names of customers who are either:
-- 1. Referred by any customer with id != 2.
-- 2. Not referred by any customer.
-- 
-- LOGIC/WHY: 
-- I used "referee_id != 2" to find people referred by someone other than ID 2. 
-- But since some people have no referrer (which is NULL), I must use "IS NULL" 
-- because in SQL, you cannot use "!= 2" to find empty/NULL values. 
-- Finally, I used "OR" because the question asks for EITHER condition.
--
-- CODE:
SELECT name 
FROM Customer 
WHERE referee_id != 2 OR referee_id IS NULL;


-- ---------------------------------------------------------
-- Problem 2: 595. Big Countries
-- ---------------------------------------------------------
-- QUESTION: 
-- Find the name, population, and area of countries that have 
-- an area of at least 3,000,000 OR a population of at least 25,000,000.
--
-- LOGIC/WHY:
-- I used "OR" instead of "AND" because a country only needs to meet 
-- ONE of those conditions to be considered "Big". I also used ">=" 
-- because the question says "at least" (meaning the number is included).
--
-- CODE:
SELECT name, population, area 
FROM World 
WHERE population >= 25000000 OR area >= 3000000;


-- ---------------------------------------------------------
-- Problem 3: 1148. Article Views I
-- ---------------------------------------------------------
-- QUESTION: 
-- Find all the authors that viewed at least one of their own articles. 
-- Return the result sorted by id in ascending order.
--
-- LOGIC/WHY:
-- I used "author_id = viewer_id" to find when the author and the viewer 
-- are the same person. I used "DISTINCT" because an author might view 
-- their article multiple times, but we only want their ID to show up once. 
-- I used "AS id" to rename the column, and "ORDER BY id ASC" to sort it.
--
-- CODE:
SELECT DISTINCT author_id AS id 
FROM Views 
WHERE author_id = viewer_id 
ORDER BY id ASC;
