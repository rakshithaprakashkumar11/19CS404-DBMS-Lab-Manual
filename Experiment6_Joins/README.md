# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.  

```sql
SELECT
  c.cust_name      AS "Customer Name",
  c.city           AS "city",
  s.name           AS "Salesman",
  s.city           AS "city",
  s.commission
FROM customer c
JOIN salesman s
  ON c.salesman_id = s.salesman_id
WHERE c.city <> s.city
  AND s.commission > 0.12;
```

**Output:**

<img width="1233" height="721" alt="image" src="https://github.com/user-attachments/assets/b5d76814-915f-4e4e-a64f-32011d710c44" />


**Question 2**
---
Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "customer_id" column and a condition filtering for orders with an order date between '2012-07-01' and '2012-07-30'.

```sql
SELECT c.*
FROM customer AS c
LEFT JOIN orders AS o ON c.customer_id = o.customer_id
WHERE o.ord_date BETWEEN '2012-07-01' AND '2012-07-30';
```

**Output:**

<img width="1231" height="500" alt="image" src="https://github.com/user-attachments/assets/1bcea37f-370a-4e98-9d2b-6f83f1d260aa" />


**Question 3**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column and a condition filtering for test results with the test name 'Blood Pressure'.

```sql
SELECT 
    p.first_name AS patient_name,
    t.*
FROM patients AS p
INNER JOIN test_results AS t ON p.patient_id = t.patient_id
WHERE t.test_name = 'Blood Pressure';
```

**Output:**

<img width="1236" height="505" alt="image" src="https://github.com/user-attachments/assets/32e1ffb6-3c39-4adc-991e-58088e43917e" />


**Question 4**
---
Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "customer_id" column and a condition filtering for orders with an order date between '2012-08-01' and '2012-08-30'.

```sql
SELECT c.*
FROM customer AS c
LEFT JOIN orders AS o ON c.customer_id = o.customer_id
WHERE o.ord_date BETWEEN '2012-08-01' AND '2012-08-30';
```

**Output:**

<img width="1236" height="581" alt="image" src="https://github.com/user-attachments/assets/fd5c70f1-9f27-4ab5-8496-6339d21ef801" />


**Question 5**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name"), with an inner join on the "patient_id" column and a condition filtering for test results with the test name 'Blood Pressure'.

```sql
SELECT patient_name.first_name AS patient_name
FROM patients AS patient_name
INNER JOIN test_results AS t ON patient_name.patient_id = t.patient_id
WHERE t.test_name = 'Blood Pressure';
```

**Output:**

<img width="830" height="486" alt="image" src="https://github.com/user-attachments/assets/9d25ebb0-fc42-45d3-af0f-7a92ee7af0db" />


**Question 6**
---
Write the SQL query that accomplishes the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a non-null discharge date.

```sql
SELECT 
    p.first_name AS patient_name,
    d.first_name AS doctor_name
FROM patients AS p
INNER JOIN doctors AS d ON p.doctor_id = d.doctor_id
WHERE p.discharge_date IS NOT NULL;
```

**Output:**

<img width="1153" height="490" alt="image" src="https://github.com/user-attachments/assets/22a9fb93-d3f8-47bc-bf69-9bc9156c3189" />


**Question 7**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for salesman_id values that have more than one associated customer.

```sql
SELECT s.name, c.cust_name, c.city, c.grade, c.salesman_id
FROM salesman AS s
LEFT JOIN customer AS c ON s.salesman_id = c.salesman_id
WHERE s.salesman_id IN (
    SELECT salesman_id
    FROM customer
    GROUP BY salesman_id
    HAVING COUNT(*) > 1
);
```

**Output:**

<img width="1232" height="718" alt="image" src="https://github.com/user-attachments/assets/00b718ae-7bdd-4b7c-9402-a091a93b67f5" />


**Question 8**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a date of birth after '1990-01-01'.

```sql
SELECT 
    p.first_name AS patient_name,
    d.first_name AS doctor_name
FROM patients AS p
INNER JOIN doctors AS d ON p.doctor_id = d.doctor_id
WHERE p.date_of_birth > '1990-01-01';
```

**Output:**

<img width="796" height="473" alt="image" src="https://github.com/user-attachments/assets/77774ec6-a4b9-41b1-9eef-e79bdf2a8b16" />


**Question 9**
---
Write the SQL query that achieves the selection of all columns from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers with the name 'Fabian Johns'.

```sql
SELECT s.*
FROM salesman AS s
LEFT JOIN customer AS c ON s.salesman_id = c.salesman_id
WHERE c.cust_name = 'Fabian Johns';
```

**Output:**

<img width="1234" height="506" alt="image" src="https://github.com/user-attachments/assets/c04eff1a-a2a0-4ab2-9999-973763d69684" />


**Question 10**
---
Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column and a condition filtering for orders with a purchase amount greater than 1000.

```sql
SELECT c.cust_name, o.ord_no, o.ord_date, o.purch_amt
FROM customer AS c
LEFT JOIN orders AS o
ON c.customer_id = o.customer_id
WHERE o.purch_amt > 1000;
```

**Output:**

<img width="1239" height="799" alt="image" src="https://github.com/user-attachments/assets/136c70ca-dab3-41fc-9784-2731f4216707" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
