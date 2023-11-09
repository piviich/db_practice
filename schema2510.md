  ## schema
![image](https://github.com/piviich/db_practice/assets/144881369/eae75c35-ca95-4390-bb69-1cdd05c5dfec)

```

CREATE TABLE checks (
	id INT PRIMARY KEY NOT NULL,
	sum_of_order float
	);
insert into checks values (1,1500);
insert into checks values (2,1700);
insert into checks values (3,500);
insert into checks values (4,6100);
insert into checks values (5,4200);


CREATE TABLE client (
	id INT PRIMARY KEY NOT NULL,
	first_name text,
	second_name text,
	birth_date date,
	number varchar(12),
	email varchar(64)
	);
	
insert into client values (1,'Alexey','Vladimirovich','2003-03-18',163634634,'random@mail.ru');
insert into client values (2,'John','Smith','1990-01-01',123456789,'johnsmith@gmail.com');
insert into client values (3,'Maria','Gonzalez','1985-06-10',987654321,'mariagonzalez@yahoo.com');
insert into client values (4,'Anna','Kowalski','1998-12-15',246813579,'annakowalski@gmail.com');
insert into client values (5,'Mohammed','Ali','1977-09-25',555555555,'mohammed.ali@gmail.com');


CREATE TABLE ranged (
	id INT PRIMARY KEY NOT NULL,
	rang_title varchar(28)
	);
	
insert into ranged values (1,'Junior staff');
insert into ranged values (2,'Senior staff');
insert into ranged values (3,'Manager');


CREATE TABLE category(
		id INT PRIMARY KEY NOT NULL,
		category_title varchar(64)
	);


insert into category values (1,'Appetizers');
insert into category values (2,'Main course');
insert into category values (3,'Desserts');
insert into category values (4,'Beverages');


CREATE TABLE menu (
	id INT PRIMARY KEY NOT NULL,
	dish_title text,
	price float  ,
	description text,
	category_id INT,
	constraint fk_category_category_id FOREIGN KEY (category_id) references category(id)
	);
	
insert into menu values (1,'Caesar Salad', 5.99, 'Classic Caesar salad with fresh romaine lettuce, croutons, Parmesan cheese, and Caesar dressing', 1);
insert into menu values (2,'Margherita Pizza', 8.99, 'Traditional Italian pizza with tomato sauce, mozzarella cheese, and fresh basil', 2);
insert into menu values (3,'Chocolate Brownie', 4.99, 'Warm chocolate brownie with vanilla ice cream and chocolate sauce', 3);
insert into menu values (4,'Iced Tea', 2.99, 'Refreshing iced tea with lemon and mint', 4);


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
	
insert into personnel values (1,'Ivan','Ivanov','1995-05-20',123456789,'ivanivanov@gmail.com',1);
insert into personnel values (2,'Petr','Petrov','1988-11-10',987654321,'petrpetrov@yahoo.com',2);
insert into personnel values (3,'Svetlana','Sidorova','1992-07-25',555555555,'svetlanasidorova@gmail.com',2);
insert into personnel values (4,'Elena','Kuznetsova','1999-03-15',246813579,'elenakuznetsova@gmail.com',3);


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
	
insert into orders values (1,1,1,1,1,2);
insert into orders values (2,2,2,2,2,1);
insert into orders values (3,3,3,3,3,3);
insert into orders values (4,4,4,4,4,4);
insert into orders values (5,1,4,5,5,2);


```



