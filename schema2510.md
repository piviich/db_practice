  ## schema
![image](https://github.com/piviich/db_practice/assets/144881369/eae75c35-ca95-4390-bb69-1cdd05c5dfec)

```
CREATE TABLE orders
(
    id INT PRIMARY KEY NOT NULL,
    waiter INT constraint fk_FOREIGN KEY,
    menu_id INT FOREIGN KEY,
	check_id INT FOREIGN KEY,
	cliend_id INT FOREIGN KEY,
	amount INT
	);
CREATE TABLE personnel
(
	id INT PRIMARY KEY,
	first_name text,
	second_nmae text,
	birth_date date,
	number varchar(12),
	email varchar(64),
	rang_id int FOREIGN KEY
	);
CREATE TABLE menu (
	id INT PRIMARY KEY AUTO_INCREMENT,
	dish_title text,
	price DOUBLE ,
	description text,
	category_id INT FOREIGN KEY,
	);
CREATE TABLE check (
	id INT PRIMARY KEY AUTO_INCREMENT,
	sum_of_order DOUBLE
	);
CREATE TABLE client (
	id INT PRIMARY KEY AUTO_INCREMENT,
	first_name text,
	second_nmae text,
	birth_date date,
	number varchar(12),
	email varchar(64)
	);
CREATE TABLE ranged (
	id INT PRIMARY KEY AUTO_INCREMENT,
	rang_title varchar(28)
	);
CREATE TABLE category(
		id INT PRIMARY KEY AUTO_INCREMENT,
		category_title varchar(64)
	);
	
```




