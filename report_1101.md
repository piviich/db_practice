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
