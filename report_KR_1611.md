  ## 01.ex00
  ```
WITH last_currency AS (
SELECT name,rate_to_usd, id,row_number() over(partition by name ORDER BY updated DESC) FROM currency
),
last_rate_to_usd AS (
SELECT * FROM last_currency WHERE row_number= 1
)
SELECT COALESCE(u.name, 'not defined'), 
	COALESCE(u.lastname,'not defined'),
	b.type,SUM(b.money) AS volume,
	COALESCE(c.name, 'not defined') AS currency_name,
	COALESCE(c.rate_to_usd, 1) AS last_rate_to_usd,
	SUM(b.money * COALESCE(c.rate_to_usd, 1)) AS total_volume_in_usd

FROM "user" u
	FULL JOIN balance b ON u.id = b.user_id
	LEFT JOIN last_rate_to_usd c ON c.id = b.currency_id
GROUP BY u.id, b.type, c.name, c.rate_to_usd
ORDER BY u.name ASC, u.lastname, b.type;

```
