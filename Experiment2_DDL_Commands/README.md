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
Create a table named Members with the following columns:

MemberID as INTEGER
MemberName as TEXT
JoinDate as DATE

```sql
CREATE TABLE Members (
MemberID INTEGER,
MemberName TEXT,
JoinDate DATE
);
```

**Output:**

<img width="1236" height="469" alt="image" src="https://github.com/user-attachments/assets/77e53f30-c9f9-4bc0-b46a-51f1ef75655d" />



**Question 2**
---
Write a SQL query to Add a new column mobilenumber as number in the Student_details table.
```sql
ALTER TABLE Student_details
ADD mobilenumber number;
```

**Output:**

<img width="1239" height="445" alt="image" src="https://github.com/user-attachments/assets/7c451215-b52f-40d9-9943-8af7466335ec" />



**Question 3**
---
Create a new table named products with the following specifications:
product_id as INTEGER and primary key.
product_name as TEXT and not NULL.
list_price as DECIMAL (10, 2) and not NULL.
discount as DECIMAL (10, 2) with a default value of 0 and not NULL.
A CHECK constraint at the table level to ensure:
list_price is greater than or equal to discount
discount is greater than or equal to 0
list_price is greater than or equal to 0
 

```sql
CREATE TABLE products (
product_id INTEGER PRIMARY KEY,
product_name TEXT NOT NULL,
list_price DECIMAL(10,2) NOT NULL,
discount DECIMAL(10,2) DEFAULT 0 NOT NULL,
CHECK (
list_price >= discount
AND discount >= 0
AND list_price >= 0
)
);
```

**Output:**

<img width="1234" height="372" alt="image" src="https://github.com/user-attachments/assets/bbcfbb10-b08e-48db-9d01-51377f55cb01" />



**Question 4**
---
Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```sql

```CREATE TABLE Orders (
OrderID INTEGER PRIMARY KEY,
OrderDate DATE NOT NULL,
CustomerID INTEGER,
FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);

**Output:**

<img width="1227" height="377" alt="image" src="https://github.com/user-attachments/assets/d96374c7-b13b-4054-b6ac-26307f9b885b" />



**Question 5**
---
Create a table named Locations with the following columns:

LocationID as INTEGER
LocationName as TEXT
Address as TEXT

```sql
CREATE TABLE Locations (
LocationID INTEGER,
LocationName TEXT,
Address TEXT
);
```

**Output:**

<img width="1224" height="463" alt="image" src="https://github.com/user-attachments/assets/9b3d9c77-7ecc-4e42-9ca9-d59f5e7ab74d" />



**Question 6**
---
Create a table named Customers with the following columns:

CustomerID as INTEGER
Name as TEXT
Email as TEXT
JoinDate as DATETIME

```sql
CREATE TABLE Customers (
CustomerID INTEGER,
Name TEXT,
Email TEXT,
JoinDate DATETIME
);

```

**Output:**

<img width="1235" height="487" alt="image" src="https://github.com/user-attachments/assets/082795a5-1f3d-43c1-a059-e9cbe1b34d4d" />


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
In the Books table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

```sql
INSERT INTO Books (ISBN, Title, Author, Publisher, Year) VALUES ('978-1234567890', 'Introduction to AI', 'John Doe', NULL, NULL);
INSERT INTO Books (ISBN, Title, Author, Publisher, Year) VALUES ('978-9876543210', 'Deep Learning', 'Jane Doe', 'TechPress', 2022);
INSERT INTO Books (ISBN, Title, Author, Publisher, Year) VALUES ('978-1122334455', 'Cybersecurity Essentials', 'Alice Smith',NULL,2021);
```

**Output:**

<img width="1234" height="377" alt="image" src="https://github.com/user-attachments/assets/60fcefa6-c418-4e12-830c-cc5db83c466a" />



**Question 9**
---
Insert the below data into the Books table, allowing the Publisher and Year columns to take their default values.

```sql
INSERT INTO Books (ISBN, Title, Author) VALUES ('978-6655443321', 'Big Data Analytics', 'Karen Adams');

```

**Output:**

<img width="1227" height="407" alt="image" src="https://github.com/user-attachments/assets/010bdcc8-3ad1-4ca7-91e6-47f7ad2b03d5" />



**Question 10**
---
In the Products table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.


```sql
INSERT INTO Products (ProductID, Name, Category, Price, Stock) VALUES (106, 'Fitness Tracker', 'Wearables', NULL, NULL);
INSERT INTO Products (ProductID, Name, Category, Price, Stock) VALUES (107, 'Laptop', 'Electronics', 999.99, 50);
INSERT INTO Products (ProductID, Name, Category, Price, Stock) VALUES (108, 'Wireless Earbuds', 'Accessories', NULL, 100);


```

**Output:**

<img width="1228" height="380" alt="image" src="https://github.com/user-attachments/assets/48c41391-1337-43bb-8277-c03d0dad50fe" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
