Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.(https://www.hackerrank.com/challenges/weather-observation-station-5/problem)

Sample Input

Let's say that CITY only has four entries: DEF, ABC, PQRS and WXY

Sample Output

ABC 3
PQRS 4

---

My solution (for Oracle SQL):

```sql
select * from (select CITY, length(CITY) from STATION
where length(CITY) = (select min(length(CITY)) from STATION) order by CITY) where rownum = 1
union
select * from (
select CITY, length(CITY) from STATION
where length(CITY) = (select max(length(CITY)) from STATION) order by CITY) where rownum = 1
order by 2;
```