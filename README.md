# PostgreSQL

# Install PostgreSQL

![](https://github.com/zazi479/-PostgreSQL/blob/dfa19899c7918fd097825821d2b8478aa0a8218c/img/postgres.png)

# BBDD_outer_joins

![](https://github.com/zazi479/-PostgreSQL/blob/054b0cfa57bd9e839ee6c5712184f1b6634c9d8b/mapa%20bases%20postgre.png)


**1. Show the name of the towns and its country name. Sort the results sorted by country name and town name. Make four versions:
-Using an explicit inner join.
-Using an implicit inner join.
-Using a left outer join.
-Using a right outer join.**


**EXPLICIT INNER JOIN VERSION:**
```
SELECT towns.name AS TownName,countries AS CountryName
FROM Towns
INNER JOIN countries ON towns.country = countries.id
ORDER BY CountryName,TownName;
```
![](https://github.com/zazi479/-PostgreSQL/blob/9abf29a6da7f63ffb6a1baf33d4da73ed40cea07/img/1.1.png)

**IMPLICIT INNER JOIN VERSION:**
```
SELECT towns.name,countries.name
FROM towns,countries
WHERE towns.country = countries.id
ORDER BY countries.name,towns.name;
```
![](https://github.com/zazi479/-PostgreSQL/blob/9abf29a6da7f63ffb6a1baf33d4da73ed40cea07/img/1.2.png)

**LEFT OUTER JOIN VERSION:**
```
SELECT towns.name AS TownName, countries.name AS CountryName
FROM Towns
LEFT OUTER JOIN countries on towns.country = countries.id
ORDER BY CountryName,TownName;
```
![](https://github.com/zazi479/-PostgreSQL/blob/9abf29a6da7f63ffb6a1baf33d4da73ed40cea07/img/1.3.png)

**RIGHT OUTER JOIN VERSION:**
```
SELECT towns.name AS TownName,countries.name AS CountryName
FROM towns
RIGHT OUTER JOIN countries On towns.country = countries.id
ORDER BY CountryName,TownName;
```
![](https://github.com/zazi479/-PostgreSQL/blob/9abf29a6da7f63ffb6a1baf33d4da73ed40cea07/img/1.4.png)

**2. Show the name of the teams with the town name and country name. Sort the results sorted by name of town and name of team. Make five versions:
-Using an explicit inner join.
-Using an implicit inner join.
-Using a left outer join.
-Using a right outer join.
-Using a full outer join.**


**EXPLICIT INNER JOIN VERSION:**
```
SELECT teams.name as TeamName,towns.name AS Name,countries.name AS CountryName
FROM towns
INNER join teams on teams.town = towns.id 
join countries on towns.country = countries.id
Order  BY towns.name asc ,teams.name asc;
```
![](https://github.com/zazi479/-PostgreSQL/blob/9abf29a6da7f63ffb6a1baf33d4da73ed40cea07/img/2.1.png)

**IMPLICIT INNER JOIN VERSION:**
```
SELECT teams.name as TeamName,towns.name AS Name,countries.name AS CountryName
FROM countries,towns,teams
WHERE  towns.country = countries.id AND  teams.town = towns.id 
Order  BY towns.name asc ,teams.name asc;
```
![](https://github.com/zazi479/-PostgreSQL/blob/9abf29a6da7f63ffb6a1baf33d4da73ed40cea07/img/2.2.png)

**LEFT OUTER JOIN VERSION:**
```
SELECT teams.name as TeamName,towns.name AS Name,countries.name AS CountryName
FROM countries
LEFT JOIN towns on towns.country = countries.id
LEFT JOIN teams on teams.town = towns.id 
Order  BY towns.name asc ,teams.name asc;
```
![](https://github.com/zazi479/-PostgreSQL/blob/9abf29a6da7f63ffb6a1baf33d4da73ed40cea07/img/2.3.png)

**RIGHT OUTER JOIN VERSION:**
```
SELECT teams.name as TeamName,towns.name AS Name,countries.name AS CountryName
FROM countries
RIGHT JOIN towns on towns.country = countries.id
RIGHT JOIN teams on teams.town = towns.id 
Order  BY towns.name asc ,teams.name asc;
```
![](https://github.com/zazi479/-PostgreSQL/blob/9abf29a6da7f63ffb6a1baf33d4da73ed40cea07/img/2.4.png)

**FULL OUTER JOIN VERSION:**
```
SELECT teams.name as TeamName,towns.name AS Name,countries.name AS CountryName
FROM countries
FULL OUTER JOIN towns on towns.country = countries.id
FULL OUTER JOIN teams on teams.town = towns.id 
Order  BY towns.name asc ,teams.name asc;
```
![](https://github.com/zazi479/-PostgreSQL/blob/9abf29a6da7f63ffb6a1baf33d4da73ed40cea07/img/2.5.png)


**3. Select the name of the towns and the numbers of teams of the town. Sort the results by town name. Make two versions:
-Using an explicit inner join.
-Using a left outer join.**

**EXPLICIT INNER JOIN VERSION:**
```
SELECT towns.name AS Name,count(teams.id) AS Num_Teams
FROM towns
INNER JOIN teams ON teams.town = towns.id
GROUP BY towns.name
ORDER BY towns.name asc;
```
![](https://github.com/zazi479/-PostgreSQL/blob/9abf29a6da7f63ffb6a1baf33d4da73ed40cea07/img/3.1.png)

**LEFT OUTER JOIN VERSION:**
```
SELECT towns.name AS Name,count(teams.id) AS Num_Teams
FROM towns
LEFT OUTER join teams on teams.town = towns.id
GROUP BY towns.name 
ORDER BY towns.name asc;
```
![](https://github.com/zazi479/-PostgreSQL/blob/9abf29a6da7f63ffb6a1baf33d4da73ed40cea07/img/3.2.png)

**4. Show the name of the towns that don't have teams using a left outer join.**

```
SELECT towns.name
FROM towns
LEFT JOIN teams
ON towns.id = teams.town
WHERE teams.town IS NULL;
```
![](https://github.com/zazi479/-PostgreSQL/blob/b5f93d55a95b24c526fc3c3566ba3e98495860df/img/atenas.png)



