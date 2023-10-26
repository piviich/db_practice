 ## Task 1Let’s make a simple aggregation, please write a SQL statement that returns person identifiers and corresponding number of visits in any pizzerias and sorting by count of visits in descending mode and sorting in person_id in ascending mode. Please take a look at the sample of data below.
```sql
SELECT p.id, (SELECT COUNT(pv.id) FROM person_visits pv 
 WHERE pv.person_id = p.id) AS "count_of_visits" FROM person p
ORDER BY count_of_visits DESC, p.id ASC
```
![image](https://github.com/piviich/db_practice/assets/144881369/ea4a23a5-fbf9-4271-a0a5-73ae051b958d)
