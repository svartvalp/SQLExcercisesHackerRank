Samantha interviews many candidates from different colleges using coding challenges and contests. Write a query to print the contest_id, hacker_id, name, and the sums of total_submissions, total_accepted_submissions, total_views, and total_unique_views for each contest sorted by contest_id. Exclude the contest from the result if all four sums are 0.

Note: A specific contest can be used to screen candidates at more than one college, but each college only holds 1 screening contest.

(https://www.hackerrank.com/challenges/interviews/problem)
---

My solution(MySQL)

```sql
select Contests.contest_id, hacker_id, name, sum(total_submissions),
sum(total_accepted_submissions), sum(total_views), sum(total_unique_views)
from Contests 
join Colleges on Contests.contest_id = Colleges.contest_id
join Challenges on Challenges.college_id = Colleges.college_id
left join (select challenge_id, sum(total_views) as total_views, sum(total_unique_views) as total_unique_views from View_Stats 
           group by 1) as stats_sum
on stats_sum.challenge_id = Challenges.challenge_id 
left join (select challenge_id, sum(total_submissions) as total_submissions, sum(total_accepted_submissions) as total_accepted_submissions from Submission_Stats group by 1) as subs_sum on subs_sum.challenge_id = Challenges.challenge_id
group by contest_id, hacker_id, name
having (sum(total_submissions) + sum(total_accepted_submissions) + sum(total_views) + sum(total_unique_views)) > 0
order by contest_id;
```