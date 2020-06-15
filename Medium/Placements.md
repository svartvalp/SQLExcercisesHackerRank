You are given three tables: Students, Friends and Packages. Students contains two columns: ID and Name. Friends contains two columns: ID and Friend_ID (ID of the ONLY best friend). Packages contains two columns: ID and Salary (offered salary in $ thousands per month).
Write a query to output the names of those students whose best friends got offered a higher salary than them. Names must be ordered by the salary amount offered to the best friends. It is guaranteed that no two students got same salary offer.

(https://www.hackerrank.com/challenges/placements/problem)

---

My Solution(MySQL):


```sql
select Students.Name from Students
inner join Packages as p1 on Students.ID = p1.ID
inner join Friends on Students.ID = Friends.ID
inner join Packages as p2 on Friends.Friend_ID = p2.ID
where p1.salary < p2.salary order by p2.Salary
```