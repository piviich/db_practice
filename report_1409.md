![image](https://github.com/piviich/db_practice/assets/144881369/29ec8faa-5d43-4b42-83fe-2a4f2980f13c) ## Task 1. 
```

SELECT pizzeria_id, pizza_name FROM menu
UNION
SELECT id, name FROM person ORDER BY pizzeria_id, pizza_name

```
![image](https://github.com/piviich/db_practice/assets/144881369/a9cea209-ecdc-4767-8ad9-bf331f8ae215)

## Task 2.

```
SELECT id,name,'person' AS source FROM person
UNION
SELECT pizzeria_id, pizza_name, 'menu' AS source FROM menu ORDER BY source,name
```
![image](https://github.com/piviich/db_practice/assets/144881369/bc2ab110-49be-44b0-9a06-a015519e12b6)

