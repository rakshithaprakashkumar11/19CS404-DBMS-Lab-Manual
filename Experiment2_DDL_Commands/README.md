# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
Write a SQL query to Delete customers with 'GRADE' 3 or 'AGENT_CODE' 'A008' whose 'OUTSTANDING_AMT' is less than 5000

```sql
DELETE FROM Customer
WHERE (GRADE = 3 OR AGENT_CODE = 'A008')
  AND OUTSTANDING_AMT < 5000;
```

**Output:**

<img width="1185" height="466" alt="image" src="https://github.com/user-attachments/assets/434ab9b9-c26b-4f25-b7cc-31bf86e3f030" />


**Question 2**
---
Write a SQL query to categorize decimal as 'High', 'Medium', or 'Low' based on whether it is greater than 100, between 50 and 100, or less than 50 in the Calculations table


```sql
SELECT 
    id,
    decimal,
    CASE
        WHEN decimal > 100 THEN 'High'
        WHEN decimal BETWEEN 50 AND 100 THEN 'Medium'
        ELSE 'Low'
    END AS category
FROM Calculations;
```

**Output:**

<img width="917" height="561" alt="image" src="https://github.com/user-attachments/assets/c61fc570-2fec-43a2-ac66-5f71655fc93a" />


**Question 3**
---
Decrease the reorder level by 30 percent where the product name contains 'cream' and quantity in stock is higher than reorder level in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT
 

```sql
UPDATE products
SET reorder_lvl = CAST(reorder_lvl * 0.7 AS INT)
WHERE product_name LIKE '%cream%'
  AND quantity > reorder_lvl;
```

**Output:**

<img width="1223" height="525" alt="image" src="https://github.com/user-attachments/assets/40493993-db0f-454a-b66e-f62dfa3cbb18" />


**Question 4**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is odd.


```sql
DELETE FROM Customer
WHERE GRADE % 2 = 1;
```

**Output:**

<img width="1222" height="512" alt="image" src="https://github.com/user-attachments/assets/864bc4e5-4723-401e-90e3-ff34f9fee082" />


**Question 5**
---
Write a SQL statement to Change the supplier name to 'A1 Suppliers' where the supplier ID is 8 in the suppliers table.

```sql
UPDATE suppliers
SET supplier_name = 'A1 Suppliers'
WHERE supplier_id = 8;

```

**Output:**

<img width="1232" height="476" alt="image" src="https://github.com/user-attachments/assets/366811b3-5f3b-485e-a27a-6667aece3c62" />


**Question 6**
---
Write a SQL query to delete a doctor from Doctors table whos specialization is 'Cardiology'

```sql
DELETE FROM Doctors
WHERE specialization = 'Cardiology';
```

**Output:**

<img width="1227" height="475" alt="image" src="https://github.com/user-attachments/assets/3e0757db-db6a-4093-a1db-a866fa4ce822" />

**Question 7**
---
Write a SQL statement to display name and commission of first 5 salesmen.

table info

salesman(name,commission) 


```sql
SELECT name, commission
FROM salesman
LIMIT 5;
```

**Output:**

<img width="567" height="445" alt="image" src="https://github.com/user-attachments/assets/dfa731de-f0a8-47ae-bc71-c50ff2641ea0" />


**Question 8**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_COUNTRY' is neither 'India' nor 'USA'.

```sql
DELETE FROM Customer
WHERE CUST_COUNTRY NOT IN ('India', 'USA');
```

**Output:**

<img width="1202" height="506" alt="image" src="https://github.com/user-attachments/assets/0e4dc10f-91fd-4d6f-900c-6e5323da420a" />


**Question 9**
---
Write a query to display the unique employee ID from EmployeePosition table who joined in 2024 and have a salary greater than 50000.

```sql
SELECT DISTINCT EmpID
FROM EmployeePosition
WHERE strftime('%Y', DateOfJoining) = '2024'
  AND Salary > 50000;

```

**Output:**

<img width="402" height="260" alt="image" src="https://github.com/user-attachments/assets/1c7f0d1f-3d27-416c-8ed9-1574d75b2a04" />


**Question 10**
---
Write a SQL statement to change the email column of employees table with 'Unavailable' for all employees in employees table.


```sql
UPDATE employees
SET email = 'Unavailable';

```

**Output:**

<img width="1227" height="453" alt="image" src="https://github.com/user-attachments/assets/bf9807c9-f902-470d-ba6c-3d507220a1a4" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
