 ## Task IV Let’s expand our data model to involve a new business feature. Every person wants to see a personal discount and every business wants to be closer for clients.
 ```
CREATE TABLE person_discounts (
id BIGINT PRIMARY KEY,
person_id bigint,
pizzeria_id bigint,
value FLOAT not null,
	constraint fk_person_discounts_person_id FOREIGN KEY (person_id) references person(id),
	constraint fk_person_discounts_pizzeria_id FOREIGN KEY (pizzeria_id) references pizzeria(id)
	);
```
 ## Task V So, there is a table person_order that stores the history of a person's orders. Please write a DML statement (INSERT INTO ... SELECT ...) that makes inserts new records into person_discounts table based on the next rules.

 ```
INSERT INTO person_discounts (person_id, pizzeria_id, value)
SELECT person_id, pizzeria_id,
	case
		WHEN amount_of_orders = 1 THEN 10.5
		WHEN amount_of_orders = 2 THEN 22
		ELSE 30
	END AS discount
FROM (
	SELECT person_id, pizzeria_id, COUNT(*) AS amount_of_orders
	FROM person_discounts
	GROUP BY person_id, pizzeria_id
) AS order_counts;
```

  ## Task VI Please write a SQL statement that returns orders with actual price and price with applied discount for each person in the corresponding pizzeria restaurant and sort by person name, and pizza name. Please take a look at the sample of data below.

  ```

```

  ## Task VIII

  ```
	ALTER TABLE person_discounts ADD CONSTRAINT ch_nn_person_id check (person_id IS NOT NULL)
	ALTER TABLE person_discounts ADD CONSTRAINT ch_nn_value check ( value IS NOT NULL)
	INSERT INTO person_discounts VALUES (1,2,3);
```
