# SQL

## Topics

### Where
```sql
-- nb: you can also use and/or within the where clause
SELECT
	id,
  	first_name
FROM
  	employees
WHERE
  	first_name != 'John';
```

#### Where In
```sql
-- nb: this is how you would get player_id for minimum event_date
SELECT
 	player_id,
 	device_id
FROM
 	activity
WHERE (player_id, event_date) IN 
	(
 	SELECT
		player_id,
		MIN(event_date)
  	FROM
		activity
  	GROUP BY
		player_id
	);
```

### Select Distinct
```sql
SELECT DISTINCT
  	last_name
FROM
  	employees;
```

### Union
- `UNION` does **not** include duplicates, `UNION ALL` **does**

```sql
SELECT
  	id
FROM
  	employees
UNION ALL
SELECT
  	id
FROM
  	departments;
```

### Join
```sql
SELECT
  e.id, e.salary, d.name
FROM
  employees e
JOIN
  departments d
ON
  e.department_id = d.id;
```

#### Multiple Joins
```sql
SELECT
  	e.id, e.salary, d.name, pr.title project
FROM
  	employees e
JOIN
  	departments d
ON
  	e.department_id = d.id
JOIN
  	employees_projects ep
ON
  	e.id = ep.employee_id
JOIN
  	projects pr
ON
  	ep.project_id = pr.id;
```

### Group By
```sql
SELECT
  	COUNT(e.id), ROUND(AVG(e.salary), 2), d.name
FROM
  	employees e
JOIN
  	departments d
ON
  	e.department_id = d.id
GROUP BY
  	d.name;
```

### Order By
```sql
SELECT
  	COUNT(e.id) n_employees,
  	ROUND(AVG(e.salary), 2) avg_salary,
  	d.name dep_name
FROM
  	employees e
JOIN
  	departments d
ON
  	e.department_id = d.id
GROUP BY
  	d.name
ORDER BY
  	avg_salary ASC;
```

### Having
```sql
-- nb: having clause cannot use column psuedonyms (avg_salary, etc.)

SELECT
  COUNT(e.id) n_employees,
  ROUND(AVG(e.salary), 2) avg_salary,
  d.name dep_name
FROM
  employees e
JOIN
  departments d
ON
  e.department_id = d.id
GROUP BY
  d.name
HAVING
  ROUND(AVG(e.salary), 2) > 40000
ORDER BY
  avg_salary ASC;
```

### Nulls
- By default, a column can hold `null` values (changed when using `CREATE TABLE`).
- You **cannot** join on null values
	- Use `isnull(null_val, replacement_val)` instead
	- It is more efficient to do the following seen below (as you are not replacing values needlessly);

```sql
SELECT
    a.UserId,
    at.YearOpened,
    at.AccountType,
    at.Description
FROM
    dbo.Account a
    INNER JOIN dbo.AccountType at
        ON a.YearOpened = at.YearOpened
        AND (a.AccountType = at.AccountType OR (a.AccountType IS NULL AND at.AccountType IS NULL))
```

### With
```sql
WITH Avg_Time (User_ID, User_Delay, Order_Count) AS (
	SELECT
		User_ID,
		AVG(Time_stamp - Prev_stamp) AS User_Delay,
		COUNT(*) AS Order_Count
	FROM
		(SELECT
			s.User_ID,
			b.Time_stamp,
			lag(Time_stamp) OVER
				(PARTITION BY s.User_ID ORDER BY b.Time_stamp)
				AS Prev_stamp
		FROM
			Sales s
		INNER JOIN
			Baskets b
		ON
			s.Basket_ID = b.Basket_ID
		)
	GROUP BY
		User_ID
	HAVING
		COUNT(*) > 1 
	)

SELECT AVG(User_Delay) FROM Avg_Time;
```

### Case When
- `CASE WHEN` could also be use to manually create a bucket

### Other Useful Functions

#### Concat

#### Cast

#### Row Number

#### Rank and Dense Rank
```sql

```

#### Lag and Lead
- Useful in combination with `date_trunc`

```sql
 SELECT
 	date_trunc('month', Time_stamp) AS Date,
	SUM(Sales_value) AS Total_Monthly_Sales,
	100 * (SUM(Sales_value) - lag(SUM(Sales_value), 1) OVER (ORDER BY Time_stamp)) / lag(SUM(Sales_value), 1) OVER (ORDER BY Time\_stamp) || '%' AS 'Monthly\_%Change'
FROM Sales
WHERE YEAR(Time_stamp) = '2020'
GROUP BY 1
ORDER BY 1;
```

### Date Manipulation

#### Date Add

#### Date Trunc
Truncate lets you define the precision of a datetime value

```sql
date_trunc('year', '2017-01-31 21:43:52:00') = 2017-01-01 00:00:00+00
```

#### Date Part
Date part lets you select only the relevant date interval that is required
```sql
SELECT DATEPART(year, '2017/08/25') AS DatePartInt; = 2017
```

#### Interval
Lets you define an interval to add or take from a date
```sql
SELECT '2020-01-01' + INTERVAL 1 DAY;
```

```sql
SELECT
	*
FROM
	table
WHERE
	datetime < DATE(NOW() - INTERVAL 14 DAY);
```

### Window Functions
Window functions do calculations that are comparable to aggregate functions. Unlike regular aggregate functions, use of a window function does not cause rows to become grouped into a single output row - ==the rows retain their separate identities==.

#### Partition By
You would use `PARTITION BY` instead of a `GROUP BY` if you wanted to aggregate but still wanted individual rows (instead of one row per aggregation)

```sql
-- nb: you can use and ORDER BY immediately after the PARTITION BY
SELECT
  	d.name,
  	AVG(e.salary) OVER(PARTITION BY d.name) AS avg_dep_salary
FROM
  	employees e
JOIN
  	departments d
ON
  	e.department_id = d.id;
```

### Histogram Bucket Creation

#### Width Bucket
```sql
SELECT
	width_bucket(e.salary, 10000, 150000, 5) bucket,
	count(*) cnt
FROM
	employees e
GROUP BY
	bucket
ORDER BY
	bucket;
```

### Cumulative Distribution
```sql
-- nb: not tested
SELECT
	COUNT(Txn_Qty) AS ‘Quantity’,
	CUME_DIST() OVER (ORDER BY COUNT(Account_id) DESC) AS ‘Distribution’
FROM
	CUSTOMER_TXNS
GROUP BY
	COUNT(Txn_Qty);
```

## Past Examples
`these examples are not tested on a dataset so may not be entirely correct!`

### Yieldify Examples
```sql
 SELECT date\_trunc('month', Time\_stamp) as 'Date',

 SUM(Sales\_value) AS 'Total\_Monthly\_Sales',

 100 \* (SUM(Sales\_value) - lag(SUM(Sales\_value), 1) OVER (ORDER BY Time\_stamp)) / lag(SUM(Sales\_value), 1) OVER (ORDER BY Time\_stamp) || '%' AS 'Monthly\_%Change'

FROM Sales

WHERE YEAR(Time\_stamp) = '2020'

GROUP BY 1

ORDER BY 1;
```

### EA Examples
```sql
SELECT
	cust.Txn_timestamp AS Date,
	COUNT(mstr.Account_id) AS ‘# Customers’, 
	SUM(
		CASE WHEN(mstr.Country= 'US'
		THEN cust.Txn_Amt
		ELSE 0 END)) AS ‘Revenue US’,
	SUM(CASE WHEN(mstr.Country= 'UK'
		THEN cust.Txn_Amt
		ELSE 0 END)) AS ‘Revenue UK’,
	SUM(CASE WHEN(mstr.Country NOT IN ('US', ‘UK’, ‘DE’)
		THEN cust.Txn_Amt
		ELSE 0 END)) AS ‘Revenue Other’,
	SUM(cust.Txn_Amt) AS ‘Revenue All’
FROM
	CUSTOMER_TXNS cust
INNER JOIN
	CUSTOMER_MSTR mstr
ON
	cust.Account_id = mstr.Account_id
WHERE
	Date BETWEEN ‘2017-02-01’ AND ‘2017-02-28’
GROUP BY
	cust.Txn_timestamp
ORDER BY
	cust.Txn_timestamp ASC;
```

```sql
SELECT
	DATALENGTH(Address) AS ‘Bytes’,
	LEN(Address) AS ‘Characters
FROM
	CUSTOMER_MSTR
ORDER BY
	DATALENGTH(Address);
```

### Deliveroo Test
1. Count the number of different cities where at least 1 order has been placed on 1st June 2020
```sql
SELECT
	COUNT(DISTINCT o.city_id)
FROM
	orders o
WHERE
	o.date_created = '2020-06-01';
```

2. Count the number of customers, that placed at least 1 order, whose last_name is “Scott”
```sql
SELECT
	COUNT(DISTINCT us.user_id)
FROM
	users us
JOIN
	orders o
ON
	us.user_id = o.user_id
WHERE
	us.last_name = 'Scott';
```

3. Find the weekly order count for the city of Madrid for the 6 full weeks leading up to, but not including, Monday 31st August 2020. Please also include the cumulative total.

```sql
-- Desired output: [week_start, order_count, cuml_order_count]

SELECT
  date_trunc('week', o.date_created) AS week_start,
  COUNT(o.order_id) AS order_count,
  SUM(COUNT(o.order_id) OVER (ORDER BY date_trunc('week', o.date_created))
  	AS cuml_order_count
FROM
  orders o
JOIN
  city ci
ON
  o.city_id = ci.city_id
WHERE
  ci.city_name = 'Madrid'
AND
  o.date_created
  	BETWEEN DATE('2020-08-31') - INTERVAL '6 WEEK'
  	AND  DATE('2020-08-31')
GROUP BY
  date_trunc('week', o.date_created);
```