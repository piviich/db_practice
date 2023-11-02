  ## schema
![image](https://github.com/piviich/db_practice/assets/144881369/eae75c35-ca95-4390-bb69-1cdd05c5dfec)

```

CREATE TABLE checks (
	id INT PRIMARY KEY NOT NULL,
	sum_of_order float
	);
CREATE TABLE client (
	id INT PRIMARY KEY NOT NULL,
	first_name text,
	second_nmae text,
	birth_date date,
	number varchar(12),
	email varchar(64)
	);
CREATE TABLE ranged (
	id INT PRIMARY KEY NOT NULL,
	rang_title varchar(28)
	);
CREATE TABLE category(
		id INT PRIMARY KEY NOT NULL,
		category_title varchar(64)
	);
	
CREATE TABLE menu (
	id INT PRIMARY KEY NOT NULL,
	dish_title text,
	price float  ,
	description text,
	category_id INT,
	constraint fk_category_category_id FOREIGN KEY (category_id) references category(id)
	);
	
CREATE TABLE personnel
(
	id INT PRIMARY KEY NOT NULL,
	first_name text,
	second_nmae text,
	birth_date date,
	number varchar(12),
	email varchar(64),
	rang_id int,
	constraint fk_ranged_rang_id FOREIGN KEY (rang_id) references ranged(id)
	);
	
CREATE TABLE orders
(
    id INT PRIMARY KEY NOT NULL,
    waiter_id INT, 
    menu_id INT,
	check_id INT,
	client_id INT, 
	amount INT,
	constraint fk_personnel_waiter_id FOREIGN KEY (waiter_id) references personnel(id),
	constraint fk_menu_menu_id FOREIGN KEY (menu_id) references menu(id),
	constraint fk_checks_check_id FOREIGN KEY (check_id) references checks(id),
	constraint fk_client_client_id FOREIGN KEY (client_id) references client(id)
	);
	

```




