# Advanced Select

## 1. The PADS
Generate the following two result sets:

Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).
Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format:
> There are a total of [occupation_count] [occupation]s.

where [occupation_count] is the number of occurrences of an occupation in OCCUPATIONS and [occupation] is the lowercase occupation name. If more than one Occupation has the same [occupation_count], they should be ordered alphabetically.

> [!NOTE]
> There will be at least two entries in the table for each type of occupation.

Input Format
The OCCUPATIONS table is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/5e67630c-52a3-4964-b140-f118c078345d)

### Solution:
```
/*QUERY 1*/
SELECT Name || '(' || SUBSTR(Occupation, 1, 1) || ')'
FROM Occupations
ORDER BY Name;

/*QUERY 2*/
SELECT 'There are a total of ' || COUNT(*) || ' ' || LOWER(Occupation) || 's.'
FROM Occupations
GROUP BY Occupation
ORDER BY COUNT(*) ASC, Occupation;
```

## 2. Occupations
Pivot the Occupation column in OCCUPATIONS so that each Name is sorted alphabetically and displayed underneath its corresponding Occupation. The output column headers should be Doctor, Professor, Singer, and Actor, respectively.

> [!NOTE]
> Print NULL when there are no more names corresponding to an occupation.

Input Format
The OCCUPATIONS table is described as follows:

![image](https://github.com/shinysn/HackerRank_SQL/assets/68563246/c312e244-ca0f-4503-9e4b-0c065cdb21bf)

###Solution:
