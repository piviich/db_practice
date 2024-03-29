 ## Task 1. SQL statement which returns all possible combinations between person and pizzeria tables and please set ordering by person identifier and then by pizzeria identifier columns

 ```
SELECT * FROM person
CROSS JOIN pizzeria
ORDER BY person,pizzeria

```
![image](https://github.com/piviich/db_practice/assets/144881369/859bf16d-9b8f-488c-8c30-1d3a25e992c9)

 ## Task 2. change our SQL statement to return person names instead of person identifiers and change ordering by action_date in ascending mode and then by person_name in descending mode. 
```
SELECT name FROM person 
CROSS JOIN person_visits
ORDER BY visit_date,name DESC;

```
![image](https://github.com/piviich/db_practice/assets/144881369/6d31855b-621c-496c-92b5-832b854e0745)

 ## Task 3. Please write a SQL statement which returns the date of order from the person_order table and corresponding person name (name and age are formatted as in the data sample below) which made an order from the person table. Add a sort by both columns in ascending mode.
 ```
SELECT DISTINCT order_date, (name,age) AS person_information 
FROM person_order
CROSS JOIN person
ORDER BY order_date, person_information ASC;
```
![image](https://github.com/piviich/db_practice/assets/144881369/d7a145ab-44db-4630-ab7e-6c1f67971ebd)


 ## Task 4. 
 ```
SELECT order_date, (name,age) AS person_information 
FROM person_order
NATURAL JOIN person
ORDER BY order_date, person_information ASC;
```
![image](https://github.com/piviich/db_practice/assets/144881369/19b0b2f7-5160-49e6-b47e-26bcca716015)

 ## Task 5. write 2 SQL statements which return a list of pizzerias names which have not been visited by persons by using IN for 1st one and EXISTS for the 2nd one.

 ```
SELECT pizzeria.name FROM pizzeria
WHERE pizzeria.id NOT IN (SELECT pizzeria_id FROM person_visits)

```
![image](https://github.com/piviich/db_practice/assets/144881369/b4493079-27c3-4eea-9553-c0c7e85046a8)

 ## Task 6. Please write a SQL statement which returns a list of the person names which made an order for pizza in the corresponding pizzeria. The sample result (with named columns) is provided below and yes ... please make ordering by 3 columns (person_name, pizza_name, pizzeria_name) in ascending mode.
 ```
SELECT person.name,menu.pizza_name,pizzeria.name FROM person_order JOIN person ON person_order.person_id=person.id
LEFT JOIN  menu ON menu.id=person_order.menu_id
LEFT JOIN pizzeria ON pizzeria.id=menu.pizzeria_id


```
![image](https://github.com/piviich/db_practice/assets/144881369/e96a1cae-4dba-4dd2-988d-82b15fd6d07b)

