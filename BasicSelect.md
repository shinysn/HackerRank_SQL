# Basic Select


## 1. Revising the Select Query I
Query all columns for all American cities in the CITY table with populations larger than 100000. The CountryCode for America is USA. 
The CITY table is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/4e9eb269-9d44-4431-a75e-520553ce0803)

### Solution:
```
SELECT * FROM CITY
WHERE Population > 100000 AND CountryCode = 'USA';
```

## 2. Revising the Select Query II
Query the NAME field for all American cities in the CITY table with populations larger than 120000. The CountryCode for America is USA.
The CITY table is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/14ca844b-5513-4ba7-8022-fce5d7c2e851)

### Solution:
```
SELECT Name FROM City
WHERE Population > 120000 AND Countrycode = 'USA';
```

## 3. Select All
Query all columns (attributes) for every row in the CITY table.
The CITY table is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/1cc2d26b-391f-4e40-b32e-a5894897300f)

### Solution:
```
SELECT * FROM City;
```

## 4. Select By ID
Query all columns for a city in CITY with the ID 1661.
The CITY table is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/5f6e81da-58a9-445e-9d41-4ac21c5a7bc0)

### Solution:
```
SELECT * FROM City
WHERE ID=1661;
```

## 5. Japanese Cities' Attributes
Query all attributes of every Japanese city in the CITY table. The COUNTRYCODE for Japan is JPN.
The CITY table is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/b85d8da6-f195-4ddf-880a-ada758b808f9)

### Solution:
```
SELECT * FROM City
WHERE CountryCode = 'JPN';
```

## 6. =Japanese Cities' Names
Query the names of all the Japanese cities in the CITY table. The COUNTRYCODE for Japan is JPN.
The CITY table is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/c4c79b09-17c9-45aa-afb1-261322bfe71e)

### Solution:
```
SELECT Name FROM City
WHERE CountryCode = 'JPN';
```

## 7. Weather Observation Station 1
Query a list of CITY and STATE from the STATION table.
The STATION table is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/4ecfe307-1487-4558-a790-70b4a4be80e7)

### Solution:
```
SELECT City, State FROM Station;
```

## 8. Weather Observation Station 3
Query a list of CITY names from STATION for cities that have an even ID number. Print the results in any order, but exclude duplicates from the answer.
The STATION table is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/db95be73-0a0b-4844-87df-cdb6b9e3bd93)

### Solution:
```
SELECT DISTINCT City from Station
WHERE MOD(ID,2) = 0;
```

## 9. Weather Observation Station 4
Find the difference between the total number of CITY entries in the table and the number of distinct CITY entries in the table.
The STATION table is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/3b98db5c-76f1-4f79-a6fd-adeabcf0b457)

### Solution:
```
SELECT COUNT(City) - COUNT(DISTINCT City) FROM Station;
```

## 10. Weather Observation Station 5
Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.
The STATION table is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/d3bb39f1-bd05-4125-a996-063ba1e36edb)

### Solution:
```
SELECT city, LENGTH(city) FROM station
ORDER BY LENGTH(city), city
LIMIT 1;
SELECT city, LENGTH(city) FROM station
ORDER BY LENGTH(city) desc, city 
LIMIT 1;
```

## 11. Weather Observation Station 6
Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. Your result cannot contain duplicates.
Input Format
The STATION table is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/8a87632a-0e22-4f05-af4c-a2955185f4fc)

### Solution:
```
SELECT DISTINCT City FROM Station
WHERE LOWER(SUBSTR(City,1,1)) in ('a','e','i','o','u');  
```

## 12. Weather Observation Station 7
Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.
Input Format
The STATION table is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/54be3b07-e1b2-4f2d-b11a-3b06ac3efaf1)

### Solution:
```
SELECT DISTINCT City FROM Station
WHERE 
lower(City) LIKE '%a' OR 
lower(City) LIKE '%e' OR
lower(City) LIKE '%i' OR
lower(City) LIKE '%o' OR
lower(City) LIKE '%u';
```

## 13. Weather Observation Station 8
Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.
Input Format
The STATION table is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/e8d8a78c-6532-48f0-a3db-b21212728bea)

### Solution:
```
SELECT DISTINCT City FROM Station
WHERE 
LOWER(SUBSTR(City,1,1)) in ('a','e','i','o','u') and
(LOWER(City) LIKE '%a' OR
 LOWER(City) LIKE '%e' OR
 LOWER(City) LIKE '%i' OR
 LOWER(City) LIKE '%o' OR
 LOWER(City) LIKE '%u');
```

## 14. Weather Observation Station 9
Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.
Input Format
The STATION table is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/42d3ce99-64a0-43e4-9d48-d8228e77f70d)

### Solution:
```
SELECT DISTINCT City FROM Station
WHERE LOWER(SUBSTR(City,1,1)) NOT IN ('a','e','i','o','u');
```

## 15. Weather Observation Station 10
Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates.
Input Format
The STATION table is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/6ea4b102-70ba-494c-8b5e-053dec6f4fb9)

### Solution:
```
SELECT DISTINCT City FROM Station
WHERE LOWER(SUBSTR(City, LENGTH(City), 1)) NOT IN ('a','e','i','o','u'); 
```

## 16. Weather Observation Station 11
Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.
Input Format
The STATION table is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/a0ffa97d-f73c-48d6-a75d-7bb02fabf5d4)

### Solution:
```
SELECT DISTINCT City FROM Station
WHERE 
LOWER(SUBSTR(City, LENGTH(City), 1)) NOT IN ('a','e','i','o','u') OR
(LOWER(SUBSTR(City, 1, 1)) NOT IN ('a','e','i','o','u')); 
```

## 17. Weather Observation Station 12
Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.
Input Format
The STATION table is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/d70af3a4-6c3e-40c0-b6b2-66670dfe3f4a)

### Solution:
```
SELECT DISTINCT City FROM Station
WHERE
LOWER(SUBSTR(City, LENGTH(City), 1)) NOT IN ('a','e','i','o','u') AND
(LOWER(SUBSTR(City, 1, 1)) NOT IN ('a','e','i','o','u'));
```

## 18. Higher Than 75 Marks
Query the Name of any student in STUDENTS who scored higher than 75 Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.
Input Format
The STUDENTS table is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/28828f45-8872-4746-8734-4c1458f29b3d)

### Solution:
```
SELECT Name FROM Students
WHERE Marks > 75
ORDER BY SUBSTR(Name,LENGTH(Name)-2,LENGTH(Name)), ID ASC;
```

## 19. Employee Names
Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order.
Input Format
The Employee table containing employee data for a company is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/810c25f8-bc2f-4aa8-880a-c5dca0e83935)

### Solution:
```
SELECT name FROM Employee
ORDER BY Name;
```

## 20. Employee Salaries
Write a query that prints a list of employee names (i.e.:  the name attribute) for employees in Employee having a salary greater than $2000 per month who have been employees for less than 10 months. Sort your result by ascending employee_id.
Input Format
The Employee table containing employee data for a company is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/ac85b152-872b-4311-a141-fba2c6599b27)

### Solution:
```
SELECT Name FROM Employee
WHERE Salary > 2000 AND Months < 10
ORDER BY Employee_ID ASC;
```
