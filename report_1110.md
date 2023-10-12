 ## Task1. Please create 2 Database Views (with similar attributes like the original table) based on simple filtering of gender of persons. Set the corresponding names for the database views: v_persons_female and v_persons_male.
 ```
CREATE VIEW view1 AS
SELECT name,gender FROM person
WHERE gender = 'male'
-------------------------------------
CREATE VIEW view1 AS
SELECT name,gender FROM person
WHERE gender = 'female'
```

![image](https://github.com/piviich/db_practice/assets/144881369/7a1d0ebf-8796-4bc7-abac-b8543210f55d)
![image](https://github.com/piviich/db_practice/assets/144881369/bb22fc12-bff1-4c88-b7c2-a84912c2178d)

 ## Task 2 Please use 2 Database Views from Exercise #00 and write SQL to get female and male person names in one list. Please set the order by person name. The sample of data is presented below.
 ```
SELECT DISTINCT v1.name FROM view1 v1
UNION
SELECT v2.name FROM view2 v2
ORDER BY name

```
![image](https://github.com/piviich/db_practice/assets/144881369/888c8023-4f81-470d-811b-26ad6bae76d5)

 ## Task 3 Please create a Database View (with name v_generated_dates) which should be “store” generated dates from 1st to 31th of January 2022 in DATE type. Don’t forget about order for the generated_date column.

 ```
CREATE view v_generated_dates AS
SELECT date::date FROM generate_series ('2022-01-01', '2022-01-31', interval '1 day') AS date
```
 ## Task 4. Please write a SQL statement which returns missing days for persons’ visits in January of 2022. Use v_generated_dates view for that task and sort the result by missing_date column. The sample of data is presented below.
 ```
SELECT * FROM v_generated_dates
WHERE date NOT IN (SELECT visit_date FROM person_visits)
ORDER BY date
```

![image](https://github.com/piviich/db_practice/assets/144881369/d51c0f68-f884-4f75-a93e-36219e5b77d2)
