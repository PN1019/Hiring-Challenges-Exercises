#### -- /TASK 1. Write a query to list count of unique accounts by group_name/

#### Query:
```sql:
SELECT COUNT(DISTINCT account_number) AS Count,group_name
FROM accounts 
WHERE account_number is not null 
GROUP BY group_name
```

#### -- /TASK 2. accounts table has the amount to be paid to unlock every
#### -- account (unlock_price). And payments table has the amount -- paid by the accounts in every installment.

#### Write a query to
#### -- get percentage of total amount paid out of the -- total unlock_price amount for every type of -- product(product_name). There is a one to many relationship -- between accounts and payments /

#### Query:
```sql:

SELECT a.account_number, a.product_name, SUM(CASE WHEN amount_total IS NOT NULL THEN amount_total ELSE 0 END) AS amount_total, SUM(unlock_price) AS unlock_price, 
CAST(COALESCE(SUM(amount_total / unlock_price * 100),0) AS DECIMAL(5,2)) AS covered_percentage
FROM 
( SELECT account_number, group_name, product_name, CAST(unlock_price AS DECIMAL) AS unlock_price 
FROM accounts ) 
AS a LEFT JOIN 
( SELECT account_number, group_name, CAST(SUM(amount) AS DECIMAL) AS amount_total 
FROM payments
GROUP BY account_number, group_name ) AS p 
ON p.account_number = a.account_number AND p.group_name = a.group_name
GROUP BY a.product_name, a.account_number, a.group_name
ORDER BY covered_percentage DESC

```
#### Query Using IsNull:
```sql:

SELECT a.account_number, a.product_name, isNull(SUM(amount_total),0) AS amount_total, 
SUM(unlock_price) AS unlock_price, 
CAST(IsNull(SUM(amount_total / unlock_price * 100),0) AS DECIMAL(5,2)) AS covered_percentage
FROM
( 
SELECT account_number, group_name, product_name, CAST(unlock_price AS DECIMAL) AS unlock_price FROM accounts )
AS a LEFT JOIN ( 
SELECT account_number,group_name, CAST(SUM(amount) AS DECIMAL) AS amount_total 
FROM payments 
GROUP BY account_number,group_name) 
AS p ON p.account_number = a.account_number AND p.group_name = a.group_name 
GROUP BY a.product_name, a.account_number, a.group_name
ORDER BY covered_percentage DESC

```
#### Query Using Coalesce:
```sql:

SELECT a.account_number, a.product_name, COALESCE(SUM(amount_total),0) AS amount_total, SUM(unlock_price) AS unlock_price,
CAST(COALESCE(SUM(amount_total / unlock_price * 100),0) AS DECIMAL(5,2)) AS covered_percentage
FROM 
( SELECT account_number, group_name, product_name, CAST(unlock_price AS DECIMAL) AS unlock_price 
FROM accounts ) 
AS a LEFT JOIN 
( SELECT account_number, group_name, CAST(SUM(amount) AS DECIMAL) AS amount_total 
FROM payments 
GROUP BY account_number, group_name )
AS p ON p.account_number = a.account_number AND p.group_name = a.group_name 
GROUP BY a.product_name, a.account_number, a.group_name 
ORDER BY covered_percentage DESC

```
#### Things To ponder upon here for using Coalesce or isnull:

- ISNULL Accepts 2 Arguments. COALESCE Accepts a List of Arguments ISNULL(NULL, 1) returned 1 because the first argument is NULL. COALESCE(NULL, 1) returned 1 because 1 is the first non-null value in the list.
replacing nulls using coalesce for it’s more compatible. it can also be used inside window function over to achieve e.g. nulls_last.
- isnull determines the output datatype based on the first argument. Coalesce return data type will change depending on what arguments you provide.in case of CAST
- isnull will carry 'not null' metadata as long as the second argument is a literal/not null. coalesce result is null-able regardless of the arguments - this changes how "into #table" creates tables, for example.
coalesce is a case statement with the memory and cpu usage that entails, ifnull / isnull is for the engines I use, a more optimised statement.
#### -- /TASK 3. Write a query to calculate the cumulative amount paid with every payment by the accounts along with the %age of the total amount paid i.e (cumulative amount/unlock_price) by the accounts till date /
#### Query:
```sql:

SELECT Convert(date,transaction_date,120) As Transaction_Date,a.account_number, a.product_name, 
SUM(Coalesce(amount_total,0)) AS amount_total, SUM(unlock_price) AS unlock_price, 
CAST(Coalesce(SUM(SUM(p.amount_total / a.unlock_price * 100))over(partition by a.account_number order by Transaction_Date),0) AS DECIMAL(5,2))AS covered_percentage 
FROM ( 
SELECT account_number,group_name,product_name, CAST(unlock_price AS DECIMAL) AS unlock_price 
FROM accounts ) 
AS a LEFT JOIN ( 
SELECT account_number, group_name,Convert(date,transaction_date,120) As Transaction_Date, CAST(SUM(amount) AS DECIMAL) AS amount_total 
FROM payments 
GROUP BY account_number, group_name,Transaction_Date ) 
AS p ON p.account_number = a.account_number AND p.group_name = a.group_name 
GROUP BY a.product_name, a.account_number, a.group_name,p.Transaction_Date
ORDER BY Transaction_Date DESC,covered_percentage

```
#### ImprovisedQuery:
```sql:

SELECT CASE WHEN transaction_date IS NULL THEN '' ELSE Convert(date,transaction_date,120) END As Transaction_Date
,a.account_number, a.product_name, 
SUM(Coalesce(amount_total,0)) AS amount_total, SUM(unlock_price) AS unlock_price, 
CAST(Coalesce(SUM(SUM(p.amount_total / a.unlock_price * 100))over(partition by a.account_number order by Transaction_Date),0) AS DECIMAL(5,2)) AS covered_percentage 
FROM ( SELECT account_number, group_name, product_name,
CAST(unlock_price AS DECIMAL) AS unlock_price FROM accounts )
AS a LEFT JOIN
( SELECT account_number, group_name,
Convert(date,transaction_date,120) As Transaction_Date, 
CAST(SUM(amount) AS DECIMAL) AS amount_total 
FROM payments 
GROUP BY account_number, group_name,Transaction_Date ) AS p 
ON p.account_number = a.account_number AND p.group_name = a.group_name 
GROUP BY a.product_name, a.account_number, a.group_name,p.Transaction_Date 
ORDER BY Transaction_Date DESC,covered_percentage

```
#### Things To Remember here:
#### - SUM = aggregate function
#### - SUM OVER != aggregate function
#### - you need to aggregate inside the window function as well so for example SUM(SUM(MyColumn)) OVER (…)
#### - The inner sum is aggregate, the outer sum is window function
