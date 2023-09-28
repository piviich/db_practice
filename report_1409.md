 ## Task 1. 
```

SELECT pizzeria_id, pizza_name FROM menu
UNION
SELECT id, name FROM person ORDER BY pizzeria_id, pizza_name

```
![image](https://github.com/piviich/db_practice/assets/144881369/a9cea209-ecdc-4767-8ad9-bf331f8ae215)

## Task 2.

```
SELECT name,'person' AS source FROM person
UNION ALL
SELECT pizza_name, 'menu' AS source FROM menu ORDER BY source,name
```
![image](https://github.com/piviich/db_practice/assets/144881369/21ce41b0-00e0-4009-b10b-5a60f003478b)
![image](https://github.com/piviich/db_practice/assets/144881369/31b5fa5a-b91a-4f86-ab1f-f55a26bd156a)


 ## Task 3. 
 ```
SELECT po.order_date, po.person_id, v.visit_date
FROM person_order po
JOIN person_visits v ON po.person_id = v.person_id
AND po.order_date = v.visit_date
ORDER BY visit_date ASC, person_id DESC;
```
![image](https://github.com/piviich/db_practice/assets/144881369/75bca649-7bd5-48e2-a93c-b3432f111553)

