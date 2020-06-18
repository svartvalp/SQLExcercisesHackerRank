You did such a great job helping Julia with her last coding contest challenge that she wants you to work on this one, too!

The total score of a hacker is the sum of their maximum scores for all of the challenges. Write a query to print the hacker_id, name, and total score of the hackers ordered by the descending score. If more than one hacker achieved the same total score, then sort the result by ascending hacker_id. Exclude all hackers with a total score of 0 from your result.

(https://www.hackerrank.com/challenges/contest-leaderboard/problem)

---

My solution(MySQL)

```sql
select Hackers.hacker_id, name, sum(score) as total_score from Hackers 
join (select hacker_id, challenge_id, max(score) as score from Submissions group by hacker_id, challenge_id) as Max_scores on Hackers.hacker_id = Max_scores.hacker_id
group by Hackers.hacker_id, name
having total_score > 0
order by total_score desc, hacker_id;
```