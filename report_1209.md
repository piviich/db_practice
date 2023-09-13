## Task 1. Inserting values to th table
```
INSERT INTO pizzeria (id,name,rating)
VALUES 
(7,'NYP',3.8),
(8,'mshkfrdd',5),
(9,'mamaitalia',4.5),
(10,'DINOCO',4.8),
(11,'Pizzajat',3.3),
(12,'Bratzhan',4.4),
(13,'cheeseplace',4.9),
(14,'walmart',2.4),
(15,'tesco',4.2);
```
![image](https://github.com/piviich/db_practice/assets/144881369/046a4e20-33d9-4b51-b65d-e76c294eae23)

```
INSERT INTO person_visits (id,person_id,pizzeria_id,visit_date)
VALUES (20,5,6,'2022-02-12'),
(21,5,3,'2022-02-14'),
(22,16,1,'2022-03-21'),
(23,12,2,'2022-03-12'),
(24,6,2,'2022-05-26'),
(25,17,1,'2022-07-29'),
(26,19,4,'2022-12-05'),
(27,15,5,'2022-12-07'),
(28,19,6,'2022-02-11'),
(29,4,3,'2022-08-13');
 
```
![image](https://github.com/piviich/db_practice/assets/144881369/89106db0-6f87-437a-a196-1a8b94938799)

```
INSERT INTO menu (id, pizzeria_id, pizza_name, price)

VALUES (20, 5, 'pineapplex', 900 ),
	(21, 6, 'italiano', 1100 ),
	(22, 3, 'extrameat', 2000 ),
	(23, 1, 'cheeseborta', 800 ),
	(24, 2, 'XXHOT', 1210 ),
	(25, 5, 'mexicanhola', 950 ),
	(26, 3, 'candyparty', 2100 ),
	(27, 2, 'doublefloor', 970 ),
	(28, 1, 'AllInOne', 1500 );
```
![image](https://github.com/piviich/db_practice/assets/144881369/ee8cfa5c-6034-4615-99f1-49c1da6bec79)


```
INSERT INTO person (id,name,age,gender,address)

VALUES (10, 'alexey', 43,'male','kazan'),
(11, 'nadezhda', 63,'female','kazan'),
(12, 'oleg', 21,'male','kazan'),
(13, 'olga', 23,'female','kazan'),
(14, 'alex', 34,'male','Saint-Petersburg'),
(15, 'zahar', 53,'female','Moscow'),
(16, 'Alina', 24,'male','Moscow'),
(17, 'Ann', 32,'female','Moscow'),
(18, 'maksim', 38,'male','Samara'),
(19, 'sasha', 18,'female','Samara');
```

![image](https://github.com/piviich/db_practice/assets/144881369/8003cfc2-0a48-459f-9617-6e6910c864b7)



```
INSERT INTO person_order (id,person_id,menu_id,order_date)
VALUES (21,10,5,'2023-02-05'),
(22,10,15,'2022-04-04'),
(23,17,23,'2022-05-02'),
(24,17,21,'2022-08-06'),
(25,19,2,'2022-09-05'),
(26,10,8,'2022-04-04'),
(27,12,17,'2022-05-04'),
(28,19,19,'2022-06-03'),
(29,18,27,'2022-02-02'),
(30,15,13,'2022-05-01');
```
![image](https://github.com/piviich/db_practice/assets/144881369/d21cd84f-dad0-4fec-bd2c-4aef4ab4dec1)
