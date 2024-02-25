# Aggregation

## 1. Revising Aggregations - The Count Function
Query a count of the number of cities in CITY having a Population larger than 100,000.

Input Format
The CITY table is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/3f8cb3ce-170f-4333-b622-bfa286d45ee9)

### Solution:
```
SELECT COUNT(*) FROM City
WHERE Population > 100000;
```

## 2. Revising Aggregations - The Sum Function
Query the total population of all cities in CITY where District is California.

Input Format
The CITY table is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/751e7f05-0cf3-4962-841f-98fa522bea5d)

### Solution:
```
SELECT SUM(Population) FROM City
WHERE District = 'California';
```

## 3. Revising Aggregations - Averages
Query the average population of all cities in CITY where District is California.

Input Format
The CITY table is described as follows:

![1449729804-f21d187d0f-CITY](https://github.com/shinysn/HackerRank_SQL/assets/68563246/8d27e337-2156-459a-8ac2-ff0348658151)

### Solution:
```
SELECT AVG(Population) FROM City
WHERE District = 'California';
```

## 4. Average Population
Query the average population for all cities in CITY, rounded down to the nearest integer.

Input Format
The CITY table is described as follows:

![1449729804-f21d187d0f-CITY](https://github.com/shinysn/HackerRank_SQL/assets/68563246/30a5d4f3-d53c-4816-af43-1600c3f02736)

### Solution:
```
SELECT ABS(AVG(Population)) FROM City;
```

## 5. Japan Population
Query the sum of the populations for all Japanese cities in CITY. The COUNTRYCODE for Japan is JPN.

Input Format
The CITY table is described as follows:

![1449729804-f21d187d0f-CITY](https://github.com/shinysn/HackerRank_SQL/assets/68563246/dca03fc4-cf90-4dd6-90eb-06b31b63d5b3)

### Solution:
```
SELECT SUM(Population) FROM City
WHERE Countrycode = 'JPN';
```

## 6. Population Density Difference
Query the difference between the maximum and minimum populations in CITY.

Input Format
The CITY table is described as follows:

![1449729804-f21d187d0f-CITY](https://github.com/shinysn/HackerRank_SQL/assets/68563246/90d6526d-ec9f-496a-9492-69bfd6078be2)

### Solution:
```
SELECT MAX(Population) - MIN(Population) FROM City;
```

## 7. The Blunder
Samantha was tasked with calculating the average monthly salaries for all employees in the EMPLOYEES table, but did not realize her keyboard's 0 key was broken until after completing the calculation. She wants your help finding the difference between her miscalculation (using salaries with any zeros removed), and the actual average salary.
Write a query calculating the amount of error (i.e.:actual -miscalculated  average monthly salaries), and round it up to the next integer.

Input Format
The EMPLOYEES table is described as follows:

![1443817108-adc2235c81-1](https://github.com/shinysn/HackerRank_SQL/assets/68563246/8571a992-f6fb-422c-9d3d-f8adbb96b68d)

> [!Note]
> Salary is per month.
> Constraints
> 1000 < Salary < 10^5

### Solution:
```
SELECT (CEIL(AVG(Salary) - AVG(REPLACE(Salary,0)))) FROM Employees;
```

## 8. Top Earners
We define an employee's total earnings to be their monthly salary * months worked, and the maximum total earnings to be the maximum total earnings for any employee in the Employee table. Write a query to find the maximum total earnings for all employees as well as the total number of employees who have maximum total earnings. Then print these values as  space-separated integers.

Input Format
The Employee table containing employee data for a company is described as follows:

![1458557872-4396838885-ScreenShot2016-03-21at4 27 13PM](https://github.com/shinysn/HackerRank_SQL/assets/68563246/fcd32aea-e7ca-4645-8dcd-ffcf4970ac28)

### Solution:
```
SELECT MAX(months*salary), COUNT(*) FROM Employee
WHERE months*salary = (SELECT MAX(months*salary) FROM Employee);
```

## 9. Weather Observation Station 2
Query the following two values from the STATION table:
The sum of all values in LAT_N rounded to a scale of 2 decimal places.
The sum of all values in LONG_W rounded to a scale of 2 decimal places.

Input Format
The STATION table is described as follows:

![1449345840-5f0a551030-Station](https://github.com/shinysn/HackerRank_SQL/assets/68563246/aa827825-4de3-464b-9077-54093eaa8ddb)

### Solution:
```
SELECT ROUND(SUM(LAT_N),2), ROUND(SUM(LONG_W),2) FROM Station;
```

## 10. Weather Observation Station 14
Query the greatest value of the Northern Latitudes (LAT_N) from STATION that is less than 137.2345. Truncate your answer to 4 decimal places.

Input Format
The STATION table is described as follows

![1449345840-5f0a551030-Station](https://github.com/shinysn/HackerRank_SQL/assets/68563246/747933f4-9f55-4e29-8cad-c97f49b3c695)

### Solution:
```
SELECT TRUNC(MAX(Lat_N),4) FROM Station
WHERE Lat_N < 137.2345;
```

## 11. Weather Observation Station 15
Query the Western Longitude (LONG_W) for the largest Northern Latitude (LAT_N) in STATION that is less than 137.2345. Round your answer to 4 decimal places.

Input Format
The STATION table is described as follows

### Solution:
```
SELECT ROUND(Long_W,4) FROM Station
WHERE 
Lat_N = (SELECT MAX(Lat_N) FROM Station WHERE Lat_N < 137.2345);
```

## 12. Weather Observation Station 16
Query the smallest Northern Latitude (LAT_N) from STATION that is greater than 38.7780. Round your answer to 4 decimal places.

Input Format
The STATION table is described as follows:

![1449345840-5f0a551030-Station](https://github.com/shinysn/HackerRank_SQL/assets/68563246/fb938e95-b662-45f6-ad15-d91f436eff69)

### Solution:
```
SELECT ROUND(MIN(Lat_N),4) FROM Station
WHERE Lat_N > 38.7780;
```

## 13. Weather Observation Station 17
Query the Western Longitude (LONG_W)where the smallest Northern Latitude (LAT_N) in STATION is greater than 38.7780. Round your answer to 4 decimal places.

Input Format
The STATION table is described as follows:

![1449345840-5f0a551030-Station](https://github.com/shinysn/HackerRank_SQL/assets/68563246/348b958f-b677-4e3f-9a83-d4a3885c93cb)

### Solution:
```
SELECT ROUND(Long_W,4) FROM Station
WHERE 
Lat_N = (SELECT MIN(Lat_N) FROM Station WHERE Lat_N > 38.7780);
```

## 14. Weather Observation Station 18
Consider P1(a,b) and P2(c,d) to be two points on a 2D plane.
 happens to equal the minimum value in Northern Latitude (LAT_N in STATION).
 happens to equal the minimum value in Western Longitude (LONG_W in STATION).
 happens to equal the maximum value in Northern Latitude (LAT_N in STATION).
 happens to equal the maximum value in Western Longitude (LONG_W in STATION).
Query the Manhattan Distance between points  and  and round it to a scale of  decimal places.

Input Format
The STATION table is described as follows:

![1449345840-5f0a551030-Station](https://github.com/shinysn/HackerRank_SQL/assets/68563246/12f39d53-76a9-48ca-893c-33ff9976ac50)

### Solution:
```
/*
a=MIN(Lat_N)
b=MIN(Long_W)
c=MAX(Lat_N)
d=MAX(Long_W)
Manhattan distance = |a - c| + |b - d|
*/

SELECT ROUND(ABS(MIN(Lat_N)-MAX(Lat_N)) + ABS(MIN(Long_W)-MAX(Long_W)), 4) FROM Station;
```

## 15. Weather Observation Station 19
Consider P1(a,c) and P2(b,d) to be two points on a 2D plane where (a,b) are the respective minimum and maximum values of Northern Latitude (LAT_N) and (c,d) are the respective minimum and maximum values of Western Longitude (LONG_W) in STATION.
Query the Euclidean Distance between points  and  and format your answer to display  decimal digits.

Input Format
The STATION table is described as follows:

![1449345840-5f0a551030-Station](https://github.com/shinysn/HackerRank_SQL/assets/68563246/42910ed5-64cc-46d4-aadc-0843adbebe00)

### Solution:
```
/*
a=MIN(Lat_N)
b=MAX(Lat_N)
c=MIN(Long_W)
d=MAX(Long_W)
Euclidean Distance = SQRT((a-b)^2 + (c-d)^2)
*/

SELECT
ROUND(SQRT(POWER(MIN(Lat_N)-MAX(Lat_N),2) + POWER(MIN(Long_W)-MAX(Long_W),2)) , 4)
FROM Station;
```

## 16. Weather Observation Station 20
A median is defined as a number separating the higher half of a data set from the lower half. Query the median of the Northern Latitudes (LAT_N) from STATION and round your answer to 4 decimal places.

Input Format
The STATION table is described as follows:

![1449345840-5f0a551030-Station](https://github.com/shinysn/HackerRank_SQL/assets/68563246/18ff301f-3cd0-4048-9e9c-ea0ff315e222)

### Solution:
```
SELECT LAT_N FROM
(
    SELECT ROW_NUMBER() OVER(ORDER BY Lat_N) sno, ROUND(Lat_N, 4) Lat_N FROM Station
)
WHERE sno = (SELECT ROUND(COUNT(*)/2) FROM Station);
```

## 17. Weather Observation Station 13
Query the sum of Northern Latitudes (LAT_N) from STATION having values greater than 38.7880 and less than 137.2345. Truncate your answer to 4 decimal places.

Input Format
The STATION table is described as follows:

![1449345840-5f0a551030-Station](https://github.com/shinysn/HackerRank_SQL/assets/68563246/81e2f745-9b97-440e-9816-f0917521c32e)

### Solution:
```
SELECT TRUNC(SUM(Lat_N),4) FROM Station
WHERE LAT_N > 38.7880 AND Lat_N < 137.2345;
```
