We define an employee's total earnings to be their monthly  worked, and the maximum total earnings to be the maximum total earnings for any employee in the Employee table. Write a query to find the maximum total earnings for all employees as well as the total number of employees who have maximum total earnings. Then print these values as 2 space-separated integers.

(https://www.hackerrank.com/challenges/earnings-of-employees/problem)
---

My solution(MySQL)

```sql
select (salary * months), count(*) from Employee group by 1 order by 1 desc limit 1;
```