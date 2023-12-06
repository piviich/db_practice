  ## schema
![image](https://github.com/piviich/db_practice/assets/144881369/eae75c35-ca95-4390-bb69-1cdd05c5dfec)

----------------------------------------------------------------------------------------------------


CREATE TABLE checks (
    id INT PRIMARY KEY NOT NULL,
    sum_of_order FLOAT
);

INSERT INTO checks VALUES (1, 1500);
INSERT INTO checks VALUES (2, 1700);
INSERT INTO checks VALUES (3, 500);
INSERT INTO checks VALUES (4, 6100);
INSERT INTO checks VALUES (5, 4200);


CREATE TABLE client (
    id INT PRIMARY KEY NOT NULL,
    first_name TEXT,
    second_name TEXT,
    birth_date DATE,
    number VARCHAR(12),
    email VARCHAR(64)
);

INSERT INTO client VALUES (1, 'Alexey', 'Vladimirovich', '2003-03-18', '163634634', 'random@mail.ru');
INSERT INTO client VALUES (2, 'John', 'Smith', '1990-01-01', '123456789', 'johnsmith@gmail.com');
INSERT INTO client VALUES (3, 'Maria', 'Gonzalez', '1985-06-10', '987654321', 'mariagonzalez@yahoo.com');
INSERT INTO client VALUES (4, 'Anna', 'Kowalski', '1998-12-15', '246813579', 'annakowalski@gmail.com');
INSERT INTO client VALUES (5, 'Mohammed', 'Ali', '1977-09-25', '555555555', 'mohammed.ali@gmail.com');


CREATE TABLE ranged (
    id INT PRIMARY KEY NOT NULL,
    rang_title VARCHAR(28)
);

INSERT INTO ranged VALUES (1, 'Junior staff');
INSERT INTO ranged VALUES (2, 'Senior staff');
INSERT INTO ranged VALUES (3, 'Manager');


CREATE TABLE category (
    id INT PRIMARY KEY NOT NULL,
    category_title VARCHAR(64)
);

INSERT INTO category VALUES (1, 'Appetizers');
INSERT INTO category VALUES (2, 'Main course');
INSERT INTO category VALUES (3, 'Desserts');
INSERT INTO category VALUES (4, 'Beverages');


CREATE TABLE menu (
    id INT PRIMARY KEY NOT NULL,
    dish_title TEXT,
    price FLOAT,
    description TEXT,
    category_id INT,
    CONSTRAINT fk_category_category_id FOREIGN KEY (category_id) REFERENCES category (id)
);

INSERT INTO menu VALUES (1, 'Caesar Salad', 5.99, 'Classic Caesar salad with fresh romaine lettuce, croutons, Parmesan cheese, and Caesar dressing', 1);
INSERT INTO menu VALUES (2, 'Margherita Pizza', 8.99, 'Traditional Italian pizza with tomato sauce, mozzarella cheese, and fresh basil', 2);
INSERT INTO menu VALUES (3, 'Chocolate Brownie', 4.99, 'Warm chocolate brownie with vanilla ice cream and chocolate sauce', 3);
INSERT INTO menu VALUES (4, 'Iced Tea', 2.99, 'Refreshing iced tea with lemon and mint', 4);
-- Fix incorrect values in the following INSERT statements
INSERT INTO menu VALUES (5, 'Pasta carbonara', 250, 'Pasta with bacon, parmesan and cream', 2);
INSERT INTO menu VALUES (6, 'Beef Steak', 500, 'Juicy steak with garnish and sauce', 2);
INSERT INTO menu VALUES (7, 'Chicken Caesar', 200, 'Salad with chicken, croutons and Caesar sauce', 1);
INSERT INTO menu VALUES (8, 'Lasagna', 300, 'Meat lasagna with tomato sauce and cheese', 2);
INSERT INTO menu VALUES (9, 'Sushi Set', 400, 'Assorted Sushi', 1);
INSERT INTO menu VALUES (10, 'Tiramisu', 150, 'Italian dessert with mascarpone', 3);

CREATE VIEW ExpensiveDishes AS
SELECT
  id,
  dish_title,
  price,
  description,
  category_id
FROM
  menu
WHERE
  price > 10.0;

CREATE TABLE personnel (
    id INT PRIMARY KEY NOT NULL,
    first_name TEXT,
    second_name TEXT,
    birth_date DATE,
    number VARCHAR(12),
    email VARCHAR(64),
    rang_id INT,
    CONSTRAINT fk_ranged_rang_id FOREIGN KEY (rang_id) REFERENCES ranged (id)
);

INSERT INTO personnel VALUES (1, 'Ivan', 'Ivanov', '1995-05-20', '123456789', 'ivanivanov@gmail.com', 1);
INSERT INTO personnel VALUES (2, 'Petr', 'Petrov', '1988-11-10', '987654321', 'petrpetrov@yahoo.com', 2);
INSERT INTO personnel VALUES (3, 'Svetlana', 'Sidorova', '1992-07-25', '555555555', 'svetlanasidorova@gmail.com', 2);
INSERT INTO personnel VALUES (4, 'Elena', 'Kuznetsova', '1999-03-15', '246813579', 'elenakuznetsova@gmail.com', 3);


CREATE TABLE orders (
    id INT PRIMARY KEY NOT NULL,
    waiter_id INT,
    menu_id INT,
    check_id INT,
    client_id INT,
    amount INT,
    CONSTRAINT fk_personnel_waiter_id FOREIGN KEY (waiter_id) REFERENCES personnel (id),
    CONSTRAINT fk_menu_menu_id FOREIGN KEY (menu_id) REFERENCES menu (id),
    CONSTRAINT fk_checks_check_id FOREIGN KEY (check_id) REFERENCES checks (id),
    CONSTRAINT fk_client_client_id FOREIGN KEY (client_id) REFERENCES client (id)
);

INSERT INTO orders VALUES (1, 1, 1, 1, 1, 2);
INSERT INTO orders VALUES (2, 2, 2, 2, 2, 1);
INSERT INTO orders VALUES (3, 3, 3, 3, 3, 3);
INSERT INTO orders VALUES (4, 4, 4, 4, 4, 4);
INSERT INTO orders VALUES (5, 1, 5, 5, 5, 2);


```
  ## TRIGGER.

```


CREATE OR REPLACE FUNCTION fnc_orders_after_edit() RETURNS TRIGGER AS $trg_orders_after_edit$
	BEGIN
		INSERT INTO orders (id, waiter_id, menu_id, check_id, client_id, amount)
		VALUES (NEW.sum_of_order,NEW.id);
		RETURN NULL;
	END;
$trg_orders_after_edit$ LANGUAGE plpgsql;

CREATE TRIGGER trg_orders_after_edit AFTER INSERT ON checks
	FOR EACH ROW EXECUTE FUNCTION fnc_orders_after_edit();
```

```
CREATE OR REPLACE FUNCTION remove_order_from_check()
RETURNS TRIGGER AS $$
BEGIN
    UPDATE checks
    SET sum_of_order = sum_of_order - (OLD.amount * menu.price)
    FROM menu
    WHERE checks.id = OLD.check_id AND menu.id = OLD.menu_id;
    RETURN OLD;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER remove_order_from_check_trigger
AFTER DELETE ON orders
FOR EACH ROW EXECUTE FUNCTION remove_order_from_check();
```

```
CREATE OR REPLACE FUNCTION update_check_sum_of_order()
RETURNS TRIGGER AS $$
BEGIN
    UPDATE checks
    SET sum_of_order = sum_of_order + (NEW.amount * menu.price)
    FROM menu
    WHERE checks.id = NEW.check_id AND menu.id = NEW.menu_id;
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER update_check_sum_of_order_trigger
AFTER INSERT ON orders
FOR EACH ROW EXECUTE FUNCTION update_check_sum_of_order();
```
```
CREATE OR REPLACE FUNCTION update_sum_of_order_function()
RETURNS TRIGGER AS $$
BEGIN
    UPDATE checks
    SET sum_of_order = NEW.sum_of_order
    WHERE id = NEW.id;
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER update_sum_of_order
AFTER INSERT ON orders
FOR EACH ROW EXECUTE FUNCTION update_sum_of_order_function();
```
--------------------------------------------------------------------------------

  ##ОТЧЕТ



  

