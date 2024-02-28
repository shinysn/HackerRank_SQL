# Basic Join
## 1. Population Census
Given the CITY and COUNTRY tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'.

> [!Note]
> CITY.CountryCode and COUNTRY.Code are matching key columns.

Input Format
The CITY and COUNTRY tables are described as follows: 

![1449769013-e54ce90480-Country](https://github.com/shinysn/HackerRank_SQL/assets/68563246/36dcf6fe-48d8-4306-8a98-15fa262a75a5)
![1449729804-f21d187d0f-CITY](https://github.com/shinysn/HackerRank_SQL/assets/68563246/d1ab2710-2c36-4fcf-bc96-df20db1ed46e)

### Solution:
```
SELECT SUM(a.Population) FROM City a, Country b
WHERE 
a.CountryCode = b.Code AND
b.Continent = 'Asia';
```

## 2. African Cities
Given the CITY and COUNTRY tables, query the names of all cities where the CONTINENT is 'Africa'.

> [!Note]
> CITY.CountryCode and COUNTRY.Code are matching key columns.

Input Format
The CITY and COUNTRY tables are described as follows:

![1449769013-e54ce90480-Country](https://github.com/shinysn/HackerRank_SQL/assets/68563246/c6c1500b-3416-4fb3-9583-1770ef7efb37)
![1449729804-f21d187d0f-CITY](https://github.com/shinysn/HackerRank_SQL/assets/68563246/52415ab9-902c-4e17-b4fb-1f89c4559fcb)

### Solution:
```
SELECT a.Name FROM City a, Country b
WHERE
a.CountryCode = b.Code AND
b.Continent = 'Africa';
```

## 3. Average Population of Each Continent
Given the CITY and COUNTRY tables, query the names of all the continents (COUNTRY.Continent) and their respective average city populations (CITY.Population) rounded down to the nearest integer.

> [!Note]
> CITY.CountryCode and COUNTRY.Code are matching key columns.

Input Format
The CITY and COUNTRY tables are described as follows:

![1449769013-e54ce90480-Country](https://github.com/shinysn/HackerRank_SQL/assets/68563246/578d96c8-f1d6-414a-b7e7-e768376dc578)
![1449729804-f21d187d0f-CITY](https://github.com/shinysn/HackerRank_SQL/assets/68563246/a0d7b7d0-ef40-41ee-abc9-5c7b736cee8e)

### Solution:
```
SELECT COUNTRY.Continent, FLOOR(AVG(CITY.Population)) FROM COUNTRY, CITY
WHERE CITY.CountryCode = COUNTRY.Code
GROUP BY COUNTRY.Continent;
```
> OR
```
SELECT COUNTRY.Continent, FLOOR(AVG(CITY.Population)) 
FROM CITY
JOIN COUNTRY
On CITY.CountryCode = COUNTRY.Code
GROUP BY COUNTRY.Continent;
```

## 4. The Report
You are given two tables: Students and Grades. Students contains three columns ID, Name and Marks.

![1443818166-a5c852caa0-1](https://github.com/shinysn/HackerRank_SQL/assets/68563246/6cd65331-e5d4-4b72-9a59-c3b9a272a43d)

Grades contains the following data:

![1443818137-69b76d805c-2](https://github.com/shinysn/HackerRank_SQL/assets/68563246/81805e01-6247-40f0-bbc0-fb9cc4d134f0)

Ketty gives Eve a task to generate a report containing three columns: Name, Grade and Mark. Ketty doesn't want the NAMES of those students who received a grade lower than 8. The report must be in descending order by grade -- i.e. higher grades are entered first. If there is more than one student with the same grade (8-10) assigned to them, order those particular students by their name alphabetically. Finally, if the grade is lower than 8, use "NULL" as their name and list them by their grades in descending order. If there is more than one student with the same grade (1-7) assigned to them, order those particular students by their marks in ascending order.

Write a query to help Eve.

### Solution:
```
SELECT 
CASE
    WHEN g.grade < 8 THEN 'NULL'
    ELSE s.name
    END,
g.Grade, s.Marks FROM Students s
LEFT JOIN Grades g
ON s.Marks >= g.Min_Mark AND s.Marks <= g.Max_Mark
ORDER BY Grade DESC, Name;
```
> OR
```
SELECT 
CASE
    WHEN g.grade < 8 THEN 'NULL'
    ELSE s.name
    END,
g.Grade, s.Marks FROM Students s, Grades g
WHERE s.Marks >= g.Min_Mark AND s.Marks <= g.Max_Mark
ORDER BY Grade DESC, Name;
```

## 5. Top Competitors
Julia just finished conducting a coding contest, and she needs your help assembling the leaderboard! Write a query to print the respective hacker_id and name of hackers who achieved full scores for more than one challenge. Order your output in descending order by the total number of challenges in which the hacker earned a full score. If more than one hacker received full scores in same number of challenges, then sort them by ascending hacker_id.

Input Format
The following tables contain contest data:
- Hackers: The hacker_id is the id of the hacker, and name is the name of the hacker. 

![1458526776-67667350b4-ScreenShot2016-03-21at7 45 59AM](https://github.com/shinysn/HackerRank_SQL/assets/68563246/db721c33-c124-47d2-ab19-88ca9c79ea5d)

- Difficulty: The difficult_level is the level of difficulty of the challenge, and score is the score of the challenge for the difficulty level. 

![1458526915-57eb75d9a2-ScreenShot2016-03-21at7 46 09AM](https://github.com/shinysn/HackerRank_SQL/assets/68563246/d9b65cab-8e23-4a69-a343-0eb596ab5d3e)

- Challenges: The challenge_id is the id of the challenge, the hacker_id is the id of the hacker who created the challenge, and difficulty_level is the level of difficulty of the challenge. 

![1458527032-f9ca650442-ScreenShot2016-03-21at7 46 17AM](https://github.com/shinysn/HackerRank_SQL/assets/68563246/bffa2e38-5d2a-46ff-b1d9-ec41f844b433)

- Submissions: The submission_id is the id of the submission, hacker_id is the id of the hacker who made the submission, challenge_id is the id of the challenge that the submission belongs to, and score is the score of the submission.

![1458527077-298f8e922a-ScreenShot2016-03-21at7 46 29AM](https://github.com/shinysn/HackerRank_SQL/assets/68563246/087f5294-8074-4314-92e5-7f2d30d981a7)

### Solution:
```
SELECT h.hacker_id, h.name 
FROM Submissions s 
JOIN Hackers h ON s.hacker_id = h.hacker_id
JOIN Challenges c ON s.challenge_id = c.challenge_id
JOIN Difficulty d ON c.Difficulty_level = d.Difficulty_level
WHERE s.score = d.score
GROUP BY h.hacker_id, h.name
HAVING COUNT(*)>1
ORDER BY COUNT(*) DESC, h.hacker_id ASC;
```

## 6. Ollivander's Inventory
Harry Potter and his friends are at Ollivander's with Ron, finally replacing Charlie's old broken wand.
Hermione decides the best way to choose is by determining the minimum number of gold galleons needed to buy each non-evil wand of high power and age. Write a query to print the id, age, coins_needed, and power of the wands that Ron's interested in, sorted in order of descending power. If more than one wand has same power, sort the result in order of descending age.

Input Format
The following tables contain data on the wands in Ollivander's inventory:
- Wands: The id is the id of the wand, code is the code of the wand, coins_needed is the total number of gold galleons needed to buy the wand, and power denotes the quality of the wand (the higher the power, the better the wand is).

![1458538092-b2a8163a74-ScreenShot2016-03-08at12 13 39AM](https://github.com/shinysn/HackerRank_SQL/assets/68563246/ae5d6ca5-5855-4dbd-84ac-1993ba857332)

- Wands_Property: The code is the code of the wand, age is the age of the wand, and is_evil denotes whether the wand is good for the dark arts. If the value of is_evil is 0, it means that the wand is not evil. The mapping between code and age is one-one, meaning that if there are two pairs, (code1, age1) and (code2, age2), then code1 != code2 and age1 != age2

![1458538221-18c4092b7d-ScreenShot2016-03-08at12 13 53AM](https://github.com/shinysn/HackerRank_SQL/assets/68563246/17830f42-62b3-4740-90c2-63a9ed04ccc1)

### Solution:
```
SELECT w.id, p.age, w.coins_needed, w.power FROM Wands w
JOIN Wands_Property p ON w.code = p.code
WHERE p.is_evil = 0 AND
w.coins_needed = 
(
    SELECT MIN(coins_needed) FROM Wands
    WHERE power = w.power AND code = w.code
)
ORDER BY w.power DESC, p.age DESC;
```

## 7. Challenges
Julia asked her students to create some coding challenges. Write a query to print the hacker_id, name, and the total number of challenges created by each student. Sort your results by the total number of challenges in descending order. If more than one student created the same number of challenges, then sort the result by hacker_id. If more than one student created the same number of challenges and the count is less than the maximum number of challenges created, then exclude those students from the result.

Input Format
The following tables contain challenge data:
- Hackers: The hacker_id is the id of the hacker, and name is the name of the hacker.

![1458521004-cb4c077dd3-ScreenShot2016-03-21at6 06 54AM](https://github.com/shinysn/HackerRank_SQL/assets/68563246/cbc62d8e-fe6f-405b-a413-de601f482975)

- Challenges: The challenge_id is the id of the challenge, and hacker_id is the id of the student who created the challenge.

![1458521079-549341d9ec-ScreenShot2016-03-21at6 07 03AM](https://github.com/shinysn/HackerRank_SQL/assets/68563246/c172262b-0307-400a-9076-c40e92c79bf8)

### Solution:
```
SELECT b.id, b.name, a.cnt_challenges
FROM (SELECT h.hacker_id, h.name, COUNT(c.challenge_id) AS cnt_challenges, RANK() OVER (ORDER BY COUNT(c.challenge_id) DESC) AS ranknum
      FROM Hackers h
      JOIN Challenges c ON h.hacker_id = c.hacker_id
      GROUP BY h.hacker_id, h.name
     ) a
JOIN (SELECT h.hacker_id AS id, h.name AS name, COUNT(c.challenge_id) AS cnt_challenges
      FROM Hackers h
      JOIN Challenges c ON h.hacker_id = c.hacker_id
      GROUP BY h.hacker_id, h.name
     ) b
ON a.cnt_challenges = b.cnt_challenges
GROUP BY a.cnt_challenges, b.id, b.name
HAVING count(ranknum) = 1 OR 
a.cnt_challenges = (SELECT MAX(cnt_challenges) 
                    FROM (SELECT COUNT(challenge_id) 
                          AS cnt_challenges 
                          FROM Challenges GROUP BY hacker_id
                         )
                   )
ORDER BY a.cnt_challenges DESC, b.id;
```
> OR
```
```
> OR
```
```
