Query the Western Longitude (LONG_W) for the largest Northern Latitude (LAT_N) in STATION that is less than 137.2345. Round your answer to 4 decimal places.

(https://www.hackerrank.com/challenges/weather-observation-station-15/problem)
---

My solution(MySQL)
```sql
select round(LONG_W, 4) from STATION
where LAT_N = (select max(LAT_N) from STATION where LAT_N < 137.2345);
```