 ## Task 1. 
```
SELECT DISTINCT pizzeria.name, rating FROM pizzeria
CROSS JOIN menu
WHERE pizzeria.id NOT IN (SELECT pizzeria_id FROM person_visits)
```
![image](https://github.com/piviich/db_practice/assets/144881369/b97b0347-634f-4c32-9a15-a19e61943d89)


 ## Task 2. 

 ```
SELECT  missing_date::date FROM generate_series ('2022-01-01','2022-01-10', INTERVAL '1 DAY') AS missing_date 
FULL JOIN (
SELECT * FROM person_visits WHERE person_id = 1 OR person_id = 2 AND visit_date BETWEEN '2022-01-01' AND '2022-01-10')  as tab
ON missing_date = visit_date WHERE tab.person_id IS NULL
ORDER BY missing_date
```
![image](https://github.com/piviich/db_practice/assets/144881369/bef24e9a-28dd-4490-afe8-0cf1be4a4efd)

