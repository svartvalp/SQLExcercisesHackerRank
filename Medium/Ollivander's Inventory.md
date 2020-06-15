Harry Potter and his friends are at Ollivander's with Ron, finally replacing Charlie's old broken wand.

Hermione decides the best way to choose is by determining the minimum number of gold galleons needed to buy each non-evil wand of high power and age. Write a query to print the id, age, coins_needed, and power of the wands that Ron's interested in, sorted in order of descending power. If more than one wand has same power, sort the result in order of descending age.

Input Format

The following tables contain data on the wands in Ollivander's inventory:

Wands: The id is the id of the wand, code is the code of the wand, coins_needed is the total number of gold galleons needed to buy the wand, and power denotes the quality of the wand (the higher the power, the better the wand is).

Wands_Property: The code is the code of the wand, age is the age of the wand, and is_evil denotes whether the wand is good for the dark arts. If the value of is_evil is 0, it means that the wand is not evil. The mapping between code and age is one-one.
(https://www.hackerrank.com/challenges/harry-potter-and-wands/problem)
---

My Solution(MySQL) 

```sql
select w.id, Wands_Property.age, w.coins_needed, w.power from Wands as w join Wands_Property on w.code = Wands_Property.code
join (select min(coins_needed) as coins_needed, age, power from Wands 
      join Wands_property on Wands.code = Wands_Property.code group by age, power) as tmp 
on Wands_Property.age = tmp.age and w.power = tmp.power
where Wands_Property.is_evil = 0 and w.coins_needed = tmp.coins_needed
order by power desc, age desc;
```