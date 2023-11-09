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





