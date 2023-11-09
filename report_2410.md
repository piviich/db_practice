 ## task 00
 ```
SELECT person_id, COUNT(person_id) FROM person_visits
GROUP BY person_id
ORDER BY count DESC, person_id ASC
```
![image](https://github.com/piviich/db_practice/assets/144881369/0251b746-8378-4fd1-a2b2-06ae146a19f0)

 ## Task 01 

 ```
SELECT p.name, COUNT(person_id) FROM person_visits
	JOIN person p ON p.id = person_visits.person_id
GROUP BY name
ORDER BY count DESC, name ASC
```
![image](https://github.com/piviich/db_practice/assets/144881369/54d9ae8d-535c-4c4e-b6df-2888142a3a62)

 ## Task 02
 ```
SELECT pi.name, COUNT(menu_id), 'order' AS action_type FROM person_order po
	JOIN menu m ON m.id = po.menu_id
	JOIN pizzeria pi ON pi.id = m.pizzeria_id
GROUP BY pi.name
ORDER BY count DESC
LIMIT 3
```

![image](https://github.com/piviich/db_practice/assets/144881369/51ead2d3-0cb8-49b9-b8d3-deaa17630c3f)

  ## Task 03

  ```
(SELECT pi.name, COUNT(pizzeria_id), 'order' AS action_type FROM person_visits pv
	JOIN pizzeria pi ON pi.id = pv.pizzeria_id
GROUP BY pi.name
ORDER BY count DESC
LIMIT 3)
	union
(SELECT pi.name, COUNT(menu_id), 'order' AS action_type FROM person_order po
	JOIN menu m ON m.id = po.menu_id
	JOIN pizzeria pi ON pi.id = m.pizzeria_id
GROUP BY pi.name
ORDER BY count DESC
	LIMIT 3)
ORDER BY action_type
```
![image](https://github.com/piviich/db_practice/assets/144881369/d5db9756-a57b-40a3-b597-401f52b36a5d)


  ## Task 04

  ```
SELECT p.name, count(pv.id) AS visits_count FROM person p
	JOIN person_visits pv ON pv.person_id = p.id
group by 1
```
![image](https://github.com/piviich/db_practice/assets/144881369/90472d01-db92-4e41-a11e-361b15d40597)

 ## Task 05
 ```
SELECT DISTINCT p.name FROM person p
	JOIN person_order pv ON pv.person_id = p.id
ORDER BY name
```
![image](https://github.com/piviich/db_practice/assets/144881369/c50fd28d-e605-45a3-bd48-d0cb7b27b6c9)

 ## Task 06
 ```
SELECT COUNT(po.order_date) AS Count_of_orders FROM person_order po
	JOIN menu m ON m.id = po.id;

SELECT AVG(m.price) as average_price,
	MAX(m.price) as max_price,
	MIN(m.price) as min_price
	FROM menu m
GROUP BY m.pizzeria_id;


```
![image](https://github.com/piviich/db_practice/assets/144881369/84bdb446-40fa-4e33-98cf-232fe36b3a1d)



