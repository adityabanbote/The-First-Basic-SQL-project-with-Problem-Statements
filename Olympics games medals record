Hey Data enthusiasts! Welcome to my profile. 

If you are new to data analytics field and want to explore some EASY yet helpful SQL scenarios then you are at the right place.

This is a small SQL project where I got a small dataset and asked some questions to the dataset as a data analyst(intern). Haha!

Tools used : EXCEL
             MySQL WORKBENCH

DATASET : OLYMPIC GAMES MEDAL RECORDS
          The dataset is taken from kaggle.com
          Its about performance of different countries in Olympics. You can assume any random year. 
          
Simply import the csv file into MySQL workbence (if you don't know how, its ok, Google it) and get started.

Disclaimer : This will be helpful for those who have just started with SQL and want to experiment on a small dataset. For those who are on the advance stage of SQL learning, please give me some days, I will soon be at your pace. Wish me good luck!

Lets start.................... 

You can copy and paste from the very next line and run the commands. You won't get any error.

-- First create a database. To create database ---- 
CREATE database project;

-- TO USE THAT DATABASE FOR ALL FURTHER QUERIES -------- 
USE project;

-- TO GET THE ENTIRE TABLE --------
SELECT * FROM olympics_medals_country_wise;

-- Since we need to use the table name and column names everytime, its very imp for it to be simple to type. Hence I changed it. You can change it as per your wish.
-- You can do this easily on MySQL and EXCEL as well, but I used query for it.

-- CHANGE THE NAME OF THE TABLE -----------------------------
ALTER table olympics_medals_country_wise
RENAME Olympic;

-- TO RENAME THE COLUMN NAME --- (WE NEED TO DO IT INDIVIDUALLY) -------
ALTER table Olympic
RENAME column summer_participations TO summer_participants

ALTER table Olympic
RENAME column winter_participations TO winter_participants

ALTER table Olympic
RENAME column total_participation TO total_participants;


-- TO SELECT THE ENTIRE RECORD FOR A PARTICULAR VALUE FROM THE COLUMN ----------
SELECT * FROM olympic
WHERE ioc_code='(IND)';

-- TO SELECT COUNTRIES HAVING EVEN NUMBER OF MEDALS----------------
SELECT countries, total_medals FROM olympic
WHERE total_medals %2=0
ORDER BY total_medals DESC;

-- TO SELECT COUNTRIES HAVING ODD NUMBER OF MEDALS----------------
SELECT countries, total_medals FROM olympic
WHERE total_medals %2=1
ORDER BY total_medals DESC;

-- COUNTRIES WITH LESS THAN 5 MEDALS IN TOTAL --------------------
SELECT countries, total_medals FROM olympic
WHERE total_medals < 5;

-- TO CHECK FOR THE DUPLICATE RECORDS ---------- (IF THE COUNT IS MORE THAN 1 THEN IT HAS DUPLICATE VALUES)
SELECT countries, count(countries) FROM olympic
GROUP BY countries;

-- GOLD MEDALS BY EACH COUNTRY ------------------------- 
SELECT countries, total_gold FROM olympic
ORDER BY total_gold desc;

-- COUNTRY WITH HIGHEST NUMBER OF GOLD MEDALS -----------

SELECT countries, total_gold FROM olympic
ORDER BY total_gold desc
LIMIT 1;

-- COUNTRY WITH MAX PARTICIPANTS --- '

SELECT countries, total_participants FROM olympic
ORDER BY total_participants desc
LIMIT 1;

-- COUNTRIES WITH MORE THAN 100 TOTAL MEDALS AND MORE THAN 15 TOTAL PARTICIPANTS ------

SELECT countries, total_participants, total_medals FROM olympic
WHERE total_participants >15 AND total_medals >100;

-- COUNTRIES WITH MORE THAN 200 TOTAL MEDALS or MORE THAN 30 TOTAL PARTICIPANTS ------

SELECT countries, total_participants, total_medals FROM olympic
WHERE total_participants >30 OR total_medals >200;

-- TOP COUNTRY IN SUMMER AND WINTER ---

SELECT countries, summer_total, winter_total FROM olympic
order by winter_total desc
limit 1;

SELECT countries, summer_total, winter_total FROM olympic
order by summer_total desc
limit 1;

-- TO SELECT MULTIPLE ROWS  ------- 

SELECT * FROM olympic
WHERE countries IN ('India', 'Pakistan', 'China');

-- COUNTRIES HOT MEDAL BETWEEN 200 AND 400 ------------

SELECT countries, total_medals FROM olympic
WHERE total_medals BETWEEN 200 AND 400;

-- COUNTRIES WITH ZERO MEDAL ------------------

SELECT countries, total_medals FROM olympic
WHERE total_medals=0;

-- COUNTRIES WHO GOT MORE MEDALS IN SUMMER THAN IN WINTER ----------- 

select countries, summer_total, winter_total FROM olympic
WHERE summer_total > winter_total
order by countries;

-- COUNTRIES HAVING NAMES WITH EXACT 5 ALPHABETS --------------

SELECT countries FROM olympic
WHERE countries LIKE '_____';  -- (5 underscore) 

-- TOTAL NUMBER OF ROWS IN THE TABLE -------------
SELECT count(*) FROM olympic;   --- 

-- TO FIND THE MAX VALUE FROM THE COLUMN  --------- 

SELECT max(total_medals) FROM olympic;

-- HOW MANY TOTAL MEDALS WHERE DISTRIBUTED --------------

SELECT sum(total_medals) FROM olympic;

-- HOW MANY COUNTRIES PARTICIPATED   -------
SELECT count(countries) FROM olympic;   -- (THIS GAVE THE NUMBER OF ROWS IN TABLE, THIS CAN BE USED ONLY WHEN THERE ARE NO DUPLICATES IN THE COLUMNS)

-- GIVE STATUS TO THE COUNTRIES ACCORDING TO THE NUMBER OF MEDALS WON -----------
SELECT countries, total_medals,
CASE
WHEN total_medals>= 300 THEN 'Powerful'
WHEN total_medals between 100 AND 299 THEN 'Developed'
ELSE 'Developing'
END AS STATUS
FROM olympic;

-- USING Subqueries (group countries by STATUS )   ------------------------

SELECT STATUS, count(STATUS) FROM 
(SELECT countries, total_medals,
CASE
WHEN total_medals>= 300 then 'Powerful'
when total_medals between 100 and 299 then 'Developed'
Else 'Developing'
END as STATUS
FROM olympic) as temptable
group by STATUS;

-- GIVING RANK TO CONTRIES ON THE BASIS OF NUMBER OF MEDALS (Row_number() , RANK() , DENSE_RANK() )------------

SELECT countries, total_medals,
ROW_NUMBER() OVER (ORDER BY total_medals DESC) AS Position
FROM olympic;

SELECT countries, total_medals,
RANK() OVER (ORDER BY total_medals desc) AS Position
FROM olympic;

SELECT countries, total_medals,
DENSE_RANK() OVER (ORDER BY total_medals desc) AS Position
FROM olympic;

-- 5TH TEAM IN THE POINTS TABLE WITH HIGHEST MEDALS (USING SUBqueries) -------- 

SELECT * FROM (
SELECT countries, total_medals,
RANK() OVER (ORDER BY total_medals desc) AS Position
FROM olympic) AS temptable
WHERE Position=5;


-- THANK YOU ----------------- 








