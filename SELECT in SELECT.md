### 1

* SELECT name FROM world 
 WHERE population > (SELECT population FROM world WHERE name='Russia')
----

### 2

* SELECT name from world
WHERE continent = 'Europe' AND gdp/population > (SELECT gdp/population from world WHERE name = 'United Kingdom')
----

### 3

* SELECT name, continent FROM world WHERE continent IN 
(SELECT continent from world WHERE continent = 'South America' OR continent = 'Oceania' ) ORDER BY name
----

### 4

* SELECT name, population from world where population > 
(SELECT population from world WHERE name = 'Canada') AND population < 
(SELECT population from world WHERE name = 'Poland')
----

### 5

* SELECT name, population/(SELECT population FROM world
WHERE name = 'Germany')*100 FROM world
WHERE continent = 'Europe'
----

### 6

* SELECT name FROM world WHERE gdp > ALL(SELECT gdp FROM world
WHERE continent = 'Europe' AND gdp>0)
----

### 7

* SELECT continent, name, area FROM world x
WHERE area >= ALL(SELECT area FROM world y WHERE x.continent = y.continent AND y.area>0)
----

### 8

* SELECT continent, name FROM world x WHERE name <= ALL(SELECT name from world y WHERE x.continent = y.continent) 
----
 
### 9 

 * SELECT name, continent, population FROM world WHERE continent IN (SELECT continent from world WHERE population <=25000000)
----

### 10

* SELECT name, continent
FROM world x
WHERE population > all (SELECT population*3
FROM world y
WHERE y.continent = x.continent AND y.name != x.name)
----



