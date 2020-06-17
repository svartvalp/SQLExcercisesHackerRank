A median is defined as a number separating the higher half of a data set from the lower half. Query the median of the Northern Latitudes (LAT_N) from STATION and round your answer to 4 decimal places.

(https://www.hackerrank.com/challenges/weather-observation-station-20/problem)
---

My solution(MySQL)
```sql
select round(station.LAT_N,4) from Station station
where (select count(LAT_N) from Station s1 where station.LAT_N > s1.LAT_N) = (select count(LAT_N) from Station s2 where station.LAT_N < s2.LAT_N);
```