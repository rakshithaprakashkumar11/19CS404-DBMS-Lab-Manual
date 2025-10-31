# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
Write a SQL query to find the customer with longest name?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER

```sql
SELECT name, LENGTH(name) AS length
FROM customer
ORDER BY LENGTH(name) DESC
LIMIT 1;

```

**Output:**

<img width="740" height="399" alt="image" src="https://github.com/user-attachments/assets/38d8955b-1d65-4cb3-9ef0-869ca9ff9d07" />


**Question 2**
---
Write a SQL query to count the number of customers. Return number of customers.

Sample table: customer

customer_id |   cust_name    |    city    | grade | salesman_id 

-------------+----------------+------------+-------+-------------

        3002 | Nick Rimando   | New York   |   100 |        5001

        3007 | Brad Davis     | New York   |   200 |        5001

        3005 | Graham Zusi    | California |   200 |        5002

```sql
SELECT COUNT(*) AS COUNT
FROM customer;

```

**Output:**

<img width="531" height="416" alt="image" src="https://github.com/user-attachments/assets/0de409b1-89c4-4c27-8568-dfd427195e5d" />


**Question 3**
---
Write a SQL query to calculate the average purchase amount of all orders. Return average purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

```sql
SELECT AVG(purch_amt) AS AVERAGE
FROM orders;

```

**Output:**

<img width="456" height="415" alt="image" src="https://github.com/user-attachments/assets/94ee4498-842b-4297-9e00-17a8b22abfe5" />


**Question 4**
---
What is the most common diagnosis among patients?

```sql
SELECT Diagnosis, COUNT(*) AS DiagnosisCount
FROM MedicalRecords
GROUP BY Diagnosis
ORDER BY DiagnosisCount DESC
LIMIT 1;

```

**Output:**

<img width="881" height="398" alt="image" src="https://github.com/user-attachments/assets/cafe989f-3781-4add-aa62-f863c041c84f" />


**Question 5**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the total work hours for each date, and excludes dates where the total work hour sum is not greater than 40.

```sql
SELECT jdate, SUM(workhour) AS "SUM(workhour)"
FROM employee1
GROUP BY jdate
HAVING SUM(workhour) > 40;

```

**Output:**

<img width="707" height="481" alt="image" src="https://github.com/user-attachments/assets/1d33c32d-c2d0-4ca4-8861-e7cf822c28ce" />


**Question 6**
---
Write the SQL query that accomplishes the selection of average price for each category from the "products" table and includes only those products where the average price falls between 10 and 15.

Sample table: products

```sql
SELECT category_id, AVG(Price) AS "AVG(Price)"
FROM products
GROUP BY category_id
HAVING AVG(Price) BETWEEN 10 AND 15;
```

**Output:**

<img width="628" height="424" alt="image" src="https://github.com/user-attachments/assets/a6c54387-c73b-4f57-bc23-cb8f7256e7a5" />


**Question 7**
---
SELECT category_id, SUM(price) AS Total_Cost
FROM products
GROUP BY category_id
HAVING SUM(price) > 50;

```sql
SELECT category_id, SUM(Price) AS Total_Cost
FROM products
GROUP BY category_id
HAVING SUM(Price) > 50;

```

**Output:**

<img width="621" height="422" alt="image" src="https://github.com/user-attachments/assets/cf109ac0-97dd-43d1-a52a-50f9da8968e1" />


**Question 8**
---
Write the SQL query that accomplishes the grouping of data by age, calculates the total income for each age group, and includes only those age groups where the total income sum is greater than 1,000,000.

```sql
SELECT age, SUM(income) AS "SUM(income)"
FROM employee
GROUP BY age
HAVING SUM(income) > 1000000;

```

**Output:**

<img width="674" height="500" alt="image" src="https://github.com/user-attachments/assets/37955e57-d3b7-41c0-8c42-bb4c209a7dbd" />


**Question 9**
---
What is the average age of doctors in each medical specialty?

```sql
SELECT Specialty,
       ROUND(AVG(TIMESTAMPDIFF(YEAR, DateOfBirth, CURDATE())),1) AS AvgAge
FROM Doctors
GROUP BY Specialty;
```

**Output:**

<img width="997" height="476" alt="image" src="https://github.com/user-attachments/assets/53be1407-65a6-48e0-9cc8-76b5c4463c95" />


**Question 10**
---
Write a SQL query to calculate the average purchase amount of all orders. Return average purchase amount.

```sql
SELECT AVG(purch_amt) AS AVERAGE
FROM orders;
```

**Output:**

<img width="457" height="408" alt="image" src="https://github.com/user-attachments/assets/a6475720-70cb-4145-9cec-ec8217c1570b" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
