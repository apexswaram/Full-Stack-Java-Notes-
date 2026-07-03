# COMPLETE MYSQL MASTER NOTES

## Industry-Oriented MySQL Notes with Real-Time Examples

### Prepared for Students Learning SQL & Database Management

---

# TABLE OF CONTENTS

1. Introduction to Databases
2. Introduction to MySQL
3. SQL Basics
4. Database Creation
5. Table Creation
6. Data Types
7. DDL Commands
8. DML Commands
9. DQL Commands
10. Operators in SQL
11. WHERE Clause
12. DISTINCT Keyword
13. Aggregate Functions
14. GROUP BY Clause
15. HAVING Clause
16. ORDER BY Clause
17. LIMIT Clause
18. Constraints
19. Joins
20. Single Row Functions
21. Character Functions
22. Number Functions
23. Date Functions
24. General Functions
25. TCL Commands
26. DCL Commands
27. Real-Time Flipkart Examples
28. Real-Time Instagram Examples
29. Real-Time Swiggy Examples
30. Interview Questions
31. Important Notes
32. Practice Queries

---

# 1. INTRODUCTION TO DATABASES

## What is a Database?

A Database is a collection of related data stored in an organized manner.

A database helps us:

* Store data
* Manage data
* Retrieve data quickly
* Update data easily
* Delete unwanted data

### Real-Time Examples

| Application    | Data Stored                               |
| -------------- | ----------------------------------------- |
| Instagram      | Users, Posts, Likes, Followers            |
| Flipkart       | Products, Customers, Orders               |
| Swiggy         | Restaurants, Food Items, Delivery Details |
| WhatsApp       | Chats, Contacts, Media Files              |
| Banking System | Customer Accounts, Transactions           |

---

# 2. INTRODUCTION TO MYSQL

## What is MySQL?

MySQL is an open-source Relational Database Management System (RDBMS).

It is used to:

* Create databases
* Create tables
* Insert records
* Update records
* Delete records
* Retrieve records

## Features of MySQL

* Fast
* Secure
* Easy to use
* Supports large databases
* Used by major companies

## Companies Using MySQL

* Facebook
* Instagram
* Twitter
* YouTube
* Netflix
* Uber

---

# 3. SQL BASICS

## What is SQL?

SQL stands for Structured Query Language.

It is used to communicate with databases.

Using SQL we can:

* Create databases
* Create tables
* Insert data
* Update data
* Delete data
* Fetch data

---

# TYPES OF SQL COMMANDS

| Category | Full Form                    | Purpose                    |
| -------- | ---------------------------- | -------------------------- |
| DDL      | Data Definition Language     | Defines database structure |
| DML      | Data Manipulation Language   | Manipulates data           |
| DQL      | Data Query Language          | Retrieves data             |
| TCL      | Transaction Control Language | Controls transactions      |
| DCL      | Data Control Language        | Controls permissions       |

---

# 4. DATABASE CREATION

## Definition

A database is a container that stores tables.

## Syntax

```sql
CREATE DATABASE database_name;
```

## Example

```sql
CREATE DATABASE LEARNING2;
```

## Using Database

```sql
USE LEARNING2;
```

### Explanation

* CREATE DATABASE creates a new database.
* USE selects the database for operations.

---

# 5. TABLE CREATION

## What is a Table?

A table stores data in rows and columns.

### Real-Time Example

Instagram User Table:

| user_id | username | followers |
| ------- | -------- | --------- |
| 1       | mahesh   | 1200      |
| 2       | vishnu   | 800       |

---

## Syntax

```sql
CREATE TABLE table_name(
column1 datatype,
column2 datatype
);
```

## Example

```sql
create table students(
std_id INT,
std_name varchar(200)
);
```

## Explanation

| Column   | Meaning             |
| -------- | ------------------- |
| std_id   | Stores student ID   |
| std_name | Stores student name |

---

# 6. DATA TYPES

## What are Data Types?

Data types define what kind of data can be stored in a column.

---

# COMMON MYSQL DATA TYPES

| Data Type | Description            |
| --------- | ---------------------- |
| INT       | Stores integers        |
| VARCHAR() | Stores strings         |
| CHAR()    | Fixed-length strings   |
| DECIMAL() | Decimal values         |
| FLOAT     | Floating-point numbers |
| DATE      | Stores dates           |
| TIME      | Stores time            |
| DATETIME  | Stores date and time   |
| TIMESTAMP | Stores timestamp       |
| BOOLEAN   | True or False          |

---

## Examples

```sql
age INT
name VARCHAR(100)
price DECIMAL(10,2)
```

---

# 7. DDL COMMANDS

# DDL - Data Definition Language

DDL commands define database structure.

## DDL Commands

* CREATE
* ALTER
* DROP
* TRUNCATE
* RENAME

---

# CREATE COMMAND

## Definition

Used to create:

* Database
* Tables

## Syntax

```sql
CREATE TABLE table_name(
column_name datatype
);
```

## Example

```sql
CREATE TABLE STUDENTS1(
id int,
name varchar(50),
age int,
marks int,
city varchar(50)
);
```

---

# ALTER COMMAND

## Definition

Used to modify table structure.

## Operations

* Add column
* Modify column
* Drop column

## Syntax

```sql
ALTER TABLE table_name
ADD column_name datatype;
```

## Example

```sql
ALTER TABLE STUDENTS1
ADD phone_number VARCHAR(20);
```

---

# DROP COMMAND

## Definition

Deletes entire table permanently.

## Syntax

```sql
DROP TABLE table_name;
```

## Example

```sql
DROP TABLE students;
```

---

# TRUNCATE COMMAND

## Definition

Deletes all rows from table.

## Syntax

```sql
TRUNCATE TABLE table_name;
```

## Example

```sql
TRUNCATE TABLE students;
```

### Important Point

* Structure remains.
* Data gets deleted.

---

# RENAME COMMAND

## Definition

Used to rename a table.

## Syntax

```sql
RENAME TABLE old_name TO new_name;
```

## Example

```sql
RENAME TABLE students TO college_students;
```

---

# 8. DML COMMANDS

# DML - Data Manipulation Language

Used to manipulate table data.

## DML Commands

* INSERT
* UPDATE
* DELETE

---

# INSERT COMMAND

## Definition

Used to insert data into table.

## Syntax

```sql
INSERT INTO table_name VALUES(value1, value2);
```

## Example

```sql
insert into students values (1, 'vishnu');
```

## Multiple Insertions

```sql
insert into students values (3, 'aparna');
insert into students values (3, 'uday');
insert into students values (4, 'vishnu');
insert into students values (5, 'maheswaram');
insert into students values (6, 'vishnu');
insert into students values (6, 'aparna');
insert into students values (1, 'vishnu');
insert into students values (5, 'uday');
```

---

# UPDATE COMMAND

## Definition

Used to modify existing data.

## Syntax

```sql
UPDATE table_name
SET column_name = value
WHERE condition;
```

## Example

```sql
UPDATE EMPLOYEES
SET EMP_DEPT = 'IT'
WHERE EMP_ID = 11;
```

## Explanation

* UPDATE modifies data.
* SET changes values.
* WHERE specifies which row to update.

---

# DELETE COMMAND

## Definition

Deletes records from table.

## Syntax

```sql
DELETE FROM table_name
WHERE condition;
```

## Example

```sql
DELETE FROM EMPLOYEES
WHERE EMP_SAL < 45000;
```

---

# 9. DQL COMMANDS

# DQL - Data Query Language

Used to retrieve data.

## Main Command

* SELECT

---

# SELECT COMMAND

## Definition

Used to retrieve data from tables.

## Syntax

```sql
SELECT column_name FROM table_name;
```

---

## Select All Columns

```sql
select * from students;
```

### Explanation

* * means all columns.

---

## Select Specific Columns

```sql
select std_id from students;
```

---

## Real-Time Example

### Flipkart Example

```sql
SELECT product_name, price
FROM flipkart_products;
```

This retrieves:

* Product name
* Product price

---

# 10. OPERATORS IN SQL

## What are Operators?

Operators are symbols used to perform comparisons.

---

# TYPES OF OPERATORS

| Operator | Meaning                  |
| -------- | ------------------------ |
| =        | Equal                    |
| >        | Greater than             |
| <        | Less than                |
| >=       | Greater than or equal    |
| <=       | Less than or equal       |
| <>       | Not equal                |
| BETWEEN  | Range checking           |
| LIKE     | Pattern matching         |
| IN       | Multiple values checking |

---

# EQUAL OPERATOR (=)

## Example

```sql
SELECT * FROM STUDENTS1
WHERE city = 'HYD';
```

### Explanation

Returns students whose city is HYD.

---

# GREATER THAN (>)

```sql
SELECT * FROM STUDENTS1
WHERE marks > 88;
```

---

# LESS THAN (<)

```sql
SELECT * FROM STUDENTS1
WHERE marks < 88;
```

---

# GREATER THAN EQUAL (>=)

```sql
SELECT * FROM STUDENTS1
WHERE marks >= 88;
```

---

# LESS THAN EQUAL (<=)

```sql
SELECT * FROM STUDENTS1
WHERE marks <= 88;
```

---

# NOT EQUAL (<>)

```sql
select * from STUDENTS1
where city <> 'TPG';
```

---

# BETWEEN OPERATOR

## Definition

Used to select values within a range.

## Syntax

```sql
column_name BETWEEN start_value AND end_value
```

## Example

```sql
SELECT * FROM STUDENTS1
WHERE age BETWEEN 19 AND 21;
```

---

# LIKE OPERATOR

## Definition

Used for pattern matching.

---

# PATTERNS

| Pattern | Meaning       |
| ------- | ------------- |
| A%      | Starts with A |
| %A      | Ends with A   |
| %A%     | Contains A    |

---

## Examples

### Starts with C

```sql
select * from flipkart_products
where product_name LIKE 'C%';
```

### Ends with s

```sql
select * from flipkart_products
where product_name LIKE '%s';
```

### Contains Air

```sql
select * from flipkart_products
where product_name LIKE '%Air%';
```

---

# IN OPERATOR

## Definition

Used to specify multiple values.

## Without IN

```sql
select * from STUDENTS1
where city = 'HYD' or city = 'TPG' or city = 'VIJ';
```

## With IN

```sql
select * from STUDENTS1
where city IN ('HYD','TPG','VIJ');
```

---

# 11. WHERE CLAUSE

## Definition

Used to filter records.

## Syntax

```sql
SELECT columns
FROM table_name
WHERE condition;
```

## Example

```sql
SELECT * FROM STUDENTS1
WHERE name = 'APARNA';
```

---

# 12. DISTINCT KEYWORD

## Definition

Returns only unique values.

## Syntax

```sql
SELECT DISTINCT column_name
FROM table_name;
```

## Example

```sql
select distinct std_name FROM students;
```

---

# DISTINCT MULTIPLE COLUMNS

```sql
SELECT distinct EMP_DEPT, EMP_SAL FROM EMPLOYEES;
```

---

# 13. AGGREGATE FUNCTIONS

## What are Aggregate Functions?

Aggregate functions perform calculations on multiple rows.

---

# TYPES OF AGGREGATE FUNCTIONS

| Function | Purpose       |
| -------- | ------------- |
| COUNT()  | Counts rows   |
| SUM()    | Adds values   |
| AVG()    | Finds average |
| MAX()    | Maximum value |
| MIN()    | Minimum value |

---

# COUNT()

## Definition

Counts number of records.

## Example

```sql
SELECT COUNT(std_name) FROM students;
```

---

# COUNT DISTINCT

```sql
SELECT COUNT(distinct std_name) FROM students;
```

---

# SUM()

## Example

```sql
SELECT EMP_DEPT , SUM(EMP_SAL) AS TOTAL_SALARY
FROM EMPLOYEES GROUP BY EMP_DEPT;
```

---

# AVG()

```sql
SELECT EMP_DEPT , AVG(EMP_SAL) AS AVG_SAL_FOREACH_DEPT
FROM EMPLOYEES GROUP BY EMP_DEPT;
```

---

# MAX()

```sql
SELECT EMP_DEPT , MAX(EMP_SAL) AS MAX_SAL_FOREACH_DEPT
FROM EMPLOYEES GROUP BY EMP_DEPT;
```

---

# MIN()

```sql
SELECT EMP_DEPT , MIN(EMP_SAL) AS MIN_SAL_FOREACH_DEPT
FROM EMPLOYEES GROUP BY EMP_DEPT;
```

---

# 14. GROUP BY CLAUSE

## Definition

GROUP BY groups rows having same values.

### Real-Time Example

In a company:

* HR Department Salary Total
* IT Department Salary Total
* Testing Department Salary Total

---

# EMPLOYEE TABLE

```sql
CREATE TABLE EMPLOYEES(
EMP_ID INT primary KEY,
EMP_NAME VARCHAR(200) NOT NULL,
EMP_DEPT VARCHAR(20) NOT NULL,
EMP_SAL INT
);
```

---

# INSERT DATA

```sql
INSERT INTO EMPLOYEES VALUES
(1, 'ARYAN','HR',45000),
(2,'AYYAN','IT',60000),
(3,'RAHUL','HR',40000),
(4,'APARNA', 'IT',65000),
(5,'UDHAY','TESTING',67000);
```

---

# GROUP BY SYNTAX

```sql
SELECT COLUMN_1,
AGGREGATE_FUNCTION()
FROM TABLE_NAME
GROUP BY COLUMN_NAME;
```

---

# GROUP BY SINGLE COLUMN

```sql
SELECT EMP_DEPT , COUNT(*) AS COUNT_OF_DEPT
FROM EMPLOYEES GROUP BY EMP_DEPT;
```

---

# GROUP BY MULTIPLE COLUMNS

```sql
SELECT EMP_DEPT , EMP_SAL, COUNT(*)
FROM EMPLOYEES GROUP BY EMP_DEPT , EMP_SAL;
```

---

# 15. HAVING CLAUSE

## Definition

HAVING filters grouped records.

### Difference Between WHERE and HAVING

| WHERE                | HAVING              |
| -------------------- | ------------------- |
| Filters rows         | Filters groups      |
| Used before GROUP BY | Used after GROUP BY |

---

# HAVING SYNTAX

```sql
SELECT column_name,
aggregate_function()
FROM table_name
GROUP BY column_name
HAVING condition;
```

---

# Examples

## Count Employees Less Than 5

```sql
SELECT EMP_DEPT , COUNT(EMP_ID) AS EMP_COUNT
FROM EMPLOYEES
GROUP BY EMP_DEPT HAVING COUNT(EMP_ID) < 5;
```

---

## Average Salary Greater Than 55000

```sql
SELECT EMP_DEPT , AVG(EMP_SAL) AS AVG_SAL
FROM EMPLOYEES
GROUP BY EMP_DEPT HAVING AVG(EMP_SAL) > 55000;
```

---

## Maximum Salary Greater Than 64000

```sql
SELECT EMP_DEPT , MAX(EMP_SAL) AS AVG_SAL
FROM EMPLOYEES
GROUP BY EMP_DEPT HAVING MAX(EMP_SAL) > 64000;
```

---

# 16. ORDER BY CLAUSE

## Definition

Used to sort data.

---

# TYPES OF SORTING

| Keyword | Meaning    |
| ------- | ---------- |
| ASC     | Ascending  |
| DESC    | Descending |

---

# SYNTAX

```sql
SELECT columns
FROM table_name
ORDER BY column_name ASC;
```

---

# DESCENDING ORDER

```sql
SELECT EMP_ID, EMP_NAME , EMP_DEPT , EMP_SAL FROM EMPLOYEES
ORDER BY EMP_NAME DESC;
```

---

# ASCENDING ORDER

```sql
SELECT EMP_ID, EMP_NAME , EMP_DEPT , EMP_SAL FROM EMPLOYEES
ORDER BY EMP_NAME ASC;
```

---

# MULTIPLE COLUMN SORTING

```sql
SELECT * FROM EMPLOYEES
ORDER BY EMP_NAME, EMP_SAL ASC;
```

---

# 17. LIMIT CLAUSE

## Definition

Restricts number of rows returned.

---

# SYNTAX

```sql
SELECT column_name
FROM table_name
LIMIT offset, row_count;
```

---

# EXAMPLES

```sql
SELECT * FROM EMPLOYEES LIMIT 5;
```

```sql
SELECT * FROM EMPLOYEES LIMIT 9, 2;
```

---

# 18. CONSTRAINTS

## What are Constraints?

Constraints enforce rules on data.

---

# TYPES OF CONSTRAINTS

| Constraint     | Purpose             |
| -------------- | ------------------- |
| PRIMARY KEY    | Unique identifier   |
| FOREIGN KEY    | Links tables        |
| UNIQUE         | Prevents duplicates |
| NOT NULL       | Cannot store NULL   |
| DEFAULT        | Default value       |
| CHECK          | Validates values    |
| AUTO_INCREMENT | Automatic numbering |

---

# PRIMARY KEY

## Definition

Uniquely identifies each row.

## Example

```sql
customer_id INT PRIMARY KEY
```

---

# FOREIGN KEY

## Definition

Creates relationship between tables.

## Example

```sql
customer_id int,
FOREIGN KEY(customer_id)
REFERENCES Customers(customer_id)
```

---

# UNIQUE

## Definition

Prevents duplicate values.

## Example

```sql
email VARCHAR(100) UNIQUE
```

---

# NOT NULL

## Definition

Column cannot contain NULL values.

## Example

```sql
EMP_NAME VARCHAR(200) NOT NULL
```

---

# DEFAULT

## Definition

Provides default value.

## Example

```sql
created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
```

---

# CHECK

## Definition

Restricts values.

## Example

```sql
age INT CHECK(age >= 18)
```

---

# AUTO_INCREMENT

## Definition

Automatically increases values.

## Example

```sql
product_id INT AUTO_INCREMENT PRIMARY KEY
```

---

# 19. JOINS

# What are Joins?

Joins combine records from multiple tables.

### Real-Time Example

In Myntra:

* Customer table stores customer data.
* Orders table stores order data.

Using joins we connect both tables.

---

# CUSTOMER TABLE

```sql
create table Customers(
customer_id INT primary key,
customer_name varchar(200),
city varchar(50)
);
```

---

# ORDERS TABLE

```sql
create table Ordres(
order_id int primary key,
product_name varchar(70),
amount int,
customer_id int
);
```

---
# SQL Joins and Functions Notes

## Myntra / Ajio Orders Management System

---

# 1. Database Creation

## Definition

A database is a collection of organized data stored electronically.

## Syntax

```sql
CREATE DATABASE database_name;
USE database_name;
```

## Example

```sql
CREATE DATABASE Ajio;
USE Ajio;
```

---

# 2. Customers Table

## Definition

The `Customers` table stores customer information.

## Table Creation Syntax

```sql
CREATE TABLE table_name(
    column_name datatype constraints
);
```

## Example

```sql
CREATE TABLE Customers(
    customer_id INT PRIMARY KEY,
    customer_name VARCHAR(200),
    city VARCHAR(50)
);
```

## Insert Data Syntax

```sql
INSERT INTO table_name VALUES(value1, value2, ...);
```

## Example

```sql
INSERT INTO Customers VALUES
(1, 'rahul', 'hyd'),
(2, 'ramesh', 'vij'),
(3, 'suresh', 'hyd'),
(4, 'ram', 'viz'),
(5, 'rakesh', 'mtm'),
(6, 'akash', 'rzm');
```

## View Table Data

```sql
SELECT * FROM Customers;
```

---

# 3. Orders Table

## Definition

The `Ordres` table stores order details placed by customers.

## Example

```sql
CREATE TABLE Ordres(
    order_id INT PRIMARY KEY,
    product_name VARCHAR(70),
    amount INT,
    customer_id INT
);
```

## Insert Data

```sql
INSERT INTO Ordres VALUES
(101, 'laptop',55000, 1),
(102, 'mobile',20000, 2),
(103, 'headphoes',3000, 1),
(104, 'keyboard',1000, 3),
(105, 'mouse',2000, 7),
(106, 'lunch box',200, 4),
(107, 'TV',15000, 3);
```

## View Table

```sql
SELECT * FROM Ordres;
```

---

# 4. SQL Joins

# A) INNER JOIN

## Definition

`INNER JOIN` returns only matching rows from both tables.

## Syntax

```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

## Example

```sql
SELECT Customers.customer_id,
       Customers.customer_name,
       Ordres.product_name,
       Ordres.amount
FROM Customers
INNER JOIN Ordres
ON Customers.customer_id = Ordres.customer_id;
```

## Output Concept

Only customers having matching orders are displayed.

---

# B) LEFT JOIN

## Definition

`LEFT JOIN` returns all records from the left table and matching records from the right table.
If no match exists, NULL values are returned.

## Syntax

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```

## Example

```sql
SELECT Customers.customer_name,
       Ordres.product_name
FROM Customers
LEFT JOIN Ordres
ON Customers.customer_id = Ordres.customer_id;
```

## Output Concept

All customers are shown even if they did not place any orders.

---

# C) RIGHT JOIN

## Definition

`RIGHT JOIN` returns all records from the right table and matching records from the left table.

## Syntax

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```

## Example

```sql
SELECT Customers.customer_id,
       Customers.customer_name,
       Ordres.product_name
FROM Customers
RIGHT JOIN Ordres
ON Customers.customer_id = Ordres.customer_id;
```

## Output Concept

All orders are shown even if customer data is missing.

---

# D) FULL JOIN

## Definition

`FULL JOIN` returns all records from both tables.
Non-matching records return NULL values.

## Syntax

```sql
SELECT columns
FROM table1
FULL JOIN table2
ON table1.column = table2.column;
```

## Example

```sql
SELECT Customers.customer_name,
       Ordres.product_name
FROM Customers
FULL JOIN Ordres
ON Customers.customer_id = Ordres.customer_id;
```

---

# FULL JOIN Using UNION

## Definition

MySQL does not directly support FULL JOIN.
We can achieve it using `LEFT JOIN + RIGHT JOIN + UNION`.

## Example

```sql
SELECT Customers.customer_name,
       Ordres.product_name
FROM Customers
LEFT JOIN Ordres
ON Customers.customer_id = Ordres.customer_id

UNION

SELECT Customers.customer_name,
       Ordres.product_name
FROM Customers
RIGHT JOIN Ordres
ON Customers.customer_id = Ordres.customer_id;
```

---

# E) NATURAL JOIN

## Definition

`NATURAL JOIN` automatically joins tables using columns with the same name.

## Syntax

```sql
SELECT columns
FROM table1
NATURAL JOIN table2;
```

## Example

```sql
SELECT customer_name,
       product_name,
       amount
FROM Customers
NATURAL JOIN Ordres;
```

---

# F) CROSS JOIN

## Definition

`CROSS JOIN` returns all possible combinations of rows from both tables.

## Formula

```text
Rows in Table A × Rows in Table B
```

---

## Employee Table

```sql
CREATE TABLE employeeCJ(
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(200)
);

INSERT INTO employeeCJ VALUES
(3,'Vijay'),
(4,'Rajesh'),
(5,'Rajini'),
(6,'Kanth');
```

---

## Shifts Table

```sql
CREATE TABLE Shifts(
    shift_id INT PRIMARY KEY,
    shift_name VARCHAR(10)
);

INSERT INTO Shifts VALUES
(101,'Morning'),
(102,'Night');
```

---

## CROSS JOIN Example

```sql
SELECT employeeCJ.emp_name,
       Shifts.shift_name
FROM employeeCJ
CROSS JOIN Shifts;
```

## Output Concept

Each employee is combined with every shift.

---

# G) SELF JOIN

## Definition

A `SELF JOIN` joins a table with itself.

---

## Manager Table

```sql
CREATE TABLE manager(
    manager_id INT PRIMARY KEY,
    manager_name VARCHAR(200)
);

INSERT INTO manager VALUES
(1,'Indira'),
(2,'Rahul'),
(3,'Mahatma');
```

---

## Employee Self Join Table

```sql
CREATE TABLE employeeSJ(
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(200),
    manager_id INT
);

INSERT INTO employeeSJ VALUES
(1,'Vijay',NULL),
(2,'Rajesh',1),
(3,'Rajini',1),
(4,'Kanth',2);
```

---

## SELF JOIN Syntax

```sql
SELECT columns
FROM table1 a
JOIN table1 b
ON a.column = b.column;
```

## Example

```sql
SELECT e.emp_name AS Employee,
       m.emp_name AS Manager
FROM employeeSJ e
JOIN employeeSJ m
ON e.emp_id = m.manager_id;
```

---

# 5. SQL Functions

# Types of Functions

## 1. Single Row Functions

Works on each row individually.

### Examples

* UPPER()
* LOWER()
* LENGTH()
* CONCAT()
* SUBSTRING()
* ROUND()
* MOD()
* NOW()
* CURDATE()
* IFNULL()

---

## 2. Group Functions (Aggregate Functions)

Works on multiple rows and returns one result.

### Examples

* SUM()
* MAX()
* MIN()
* COUNT()
* AVG()

---

# 6. Instagram Users Table

## Table Creation

```sql
CREATE TABLE instagram_users(
    user_id INT,
    username VARCHAR(200),
    city VARCHAR(50),
    followers INT,
    amonut DECIMAL(10,2)
);
```

## Insert Data

```sql
INSERT INTO instagram_users
(user_id, username, city, followers, amonut)
VALUES
(1, 'virat_kohli', 'Delhi', 270000000, 1250000.50),
(2, 'msdhoni', 'Ranchi', 45000000, 850000.75),
(3, 'sachintendulkar', 'Mumbai', 42000000, 950000.00);
```

---

# 7. Character Functions

# A) UPPER()

## Definition

Converts text into uppercase letters.

## Syntax

```sql
SELECT UPPER(column_name)
FROM table_name;
```

## Example

```sql
SELECT UPPER(username)
FROM instagram_users;
```

---

# B) LOWER()

## Definition

Converts text into lowercase letters.

## Syntax

```sql
SELECT LOWER(column_name)
FROM table_name;
```

## Example

```sql
SELECT LOWER(username)
FROM instagram_users;
```

---

# C) LENGTH()

## Definition

Returns the number of characters in a string.

## Syntax

```sql
SELECT LENGTH(column_name)
FROM table_name;
```

## Example

```sql
SELECT username,
       LENGTH(username) AS total_characters
FROM instagram_users;
```

---

# D) CONCAT()

## Definition

Combines multiple strings into one string.

## Syntax

```sql
SELECT CONCAT(string1, column_name, string2)
FROM table_name;
```

## Example

```sql
SELECT CONCAT('Hello iam ',
              username,
              ' i lives in ',
              city) AS Profile_info
FROM instagram_users;
```

---

# E) SUBSTRING()

## Definition

Extracts part of a string.

## Syntax

```sql
SELECT SUBSTRING(column_name, start, length)
FROM table_name;
```

## Example

```sql
SELECT username,
       SUBSTRING(username,1,4) AS short_name
FROM instagram_users;
```

---

# 8. Number Functions

# A) ROUND()

## Definition

Rounds decimal values.

## Syntax

```sql
SELECT ROUND(column_name)
FROM table_name;
```

## Example

```sql
SELECT amonut,
       ROUND(amonut) AS rounded_amount
FROM instagram_users;
```

---

# B) MOD()

## Definition

Returns the remainder after division.

## Syntax

```sql
SELECT MOD(a,b);
```

## Example

```sql
SELECT MOD(10,3);
```

## Output

```text
1
```

---

# 9. Date Functions

# A) NOW()

## Definition

Returns current date and time.

## Example

```sql
SELECT NOW();
```

---

# B) CURDATE()

## Definition

Returns current date only.

## Example

```sql
SELECT CURDATE();
```

---

# 10. General Functions

# IFNULL()

## Definition

Replaces NULL values with another value.

## Syntax

```sql
SELECT IFNULL(column_name, 'replacement')
FROM table_name;
```

---

## Insert NULL Values

```sql
INSERT INTO instagram_users
(user_id, username, city, followers, amonut)
VALUES
(61, 'virat_kohli', NULL, 270000000, 1250000.50),
(62, 'msdhoni', NULL, 45000000, 850000.75),
(63, 'sachintendulkar', NULL, 42000000, 950000.00);
```

## Example

```sql
SELECT username,
       IFNULL(city, 'City Not Updated') AS City
FROM instagram_users;
```

---

# 11. Important Interview Points

## Difference Between INNER JOIN and LEFT JOIN

| INNER JOIN                 | LEFT JOIN                        |
| -------------------------- | -------------------------------- |
| Returns matching rows only | Returns all rows from left table |
| Non-matching rows ignored  | Non-matching rows show NULL      |

---

## Difference Between CROSS JOIN and SELF JOIN

| CROSS JOIN            | SELF JOIN                  |
| --------------------- | -------------------------- |
| Combines every row    | Joins table with itself    |
| Used for combinations | Used for hierarchical data |

---

# 12. Short Summary

## SQL Joins

* INNER JOIN → Matching rows only
* LEFT JOIN → All left rows
* RIGHT JOIN → All right rows
* FULL JOIN → All rows from both tables
* NATURAL JOIN → Automatic join
* CROSS JOIN → Every combination
* SELF JOIN → Same table join

## SQL Functions

* Character Functions → Text operations
* Number Functions → Numeric calculations
* Date Functions → Current date/time
* General Functions → Handle NULL values


# 20. SINGLE ROW FUNCTIONS

## Definition

Functions that operate on one row at a time.

---

# TYPES OF SINGLE ROW FUNCTIONS

1. Character Functions
2. Number Functions
3. Date Functions
4. General Functions

---

# 21. CHARACTER FUNCTIONS

# UPPER()

## Definition

Converts text to uppercase.

## Syntax

```sql
UPPER(column_name)
```

## Example

```sql
SELECT UPPER(name)
FROM STUDENTS1;
```

---

# LOWER()

## Definition

Converts text to lowercase.

## Example

```sql
SELECT LOWER(name)
FROM STUDENTS1;
```

---

# LENGTH()

## Definition

Returns number of characters.

## Example

```sql
SELECT LENGTH(name)
FROM STUDENTS1;
```

---

# CONCAT()

## Definition

Combines strings.

## Example

```sql
SELECT CONCAT(name, ' - ', city)
FROM STUDENTS1;
```

---

# SUBSTRING()

## Definition

Extracts part of string.

## Syntax

```sql
SUBSTRING(string, start, length)
```

## Example

```sql
SELECT SUBSTRING(name, 1, 3)
FROM STUDENTS1;
```

---

# 22. NUMBER FUNCTIONS

# ROUND()

## Definition

Rounds decimal values.

## Example

```sql
SELECT ROUND(45.678, 2);
```

---

# MOD()

## Definition

Returns remainder.

## Example

```sql
SELECT MOD(10,3);
```

---

# 23. DATE FUNCTIONS

# NOW()

## Definition

Returns current date and time.

## Example

```sql
SELECT NOW();
```

---

# CURDATE()

## Definition

Returns current date.

## Example

```sql
SELECT CURDATE();
```

---

# 24. GENERAL FUNCTIONS

# IFNULL()

## Definition

Replaces NULL with another value.

## Example

```sql
SELECT IFNULL(NULL, 'No Data');
```

---

# 25. TCL COMMANDS

# TCL - Transaction Control Language

Used to manage transactions.

## TCL Commands

* COMMIT
* ROLLBACK
* SAVEPOINT

---

# COMMIT

## Definition

Permanently saves transaction.

## Example

```sql
COMMIT;
```

---

# ROLLBACK

## Definition

Undo changes.

## Example

```sql
ROLLBACK;
```

---

# SAVEPOINT

## Definition

Creates rollback point.

## Example

```sql
SAVEPOINT sp1;
```

---

# 26. DCL COMMANDS

# DCL - Data Control Language

Controls permissions.

## Commands

* GRANT
* REVOKE

---

# GRANT

## Definition

Gives permissions.

## Example

```sql
GRANT SELECT ON students TO user1;
```

---

# REVOKE

## Definition

Removes permissions.

## Example

```sql
REVOKE SELECT ON students FROM user1;
```

---

# 27. REAL-TIME FLIPKART PROJECT EXAMPLE

# Flipkart Product Table

```sql
CREATE TABLE flipkart_products (
product_id INT AUTO_INCREMENT PRIMARY KEY,
product_name VARCHAR(255),
category VARCHAR(100),
brand VARCHAR(100),
price DECIMAL(10,2),
rating DECIMAL(2,1),
stock INT,
created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

# Real-Time Queries

## Find Expensive Products

```sql
SELECT * FROM flipkart_products
WHERE price > 50000;
```

---

## Find Apple Products

```sql
SELECT * FROM flipkart_products
WHERE brand = 'Apple';
```

---

## Find Products Starting with S

```sql
SELECT * FROM flipkart_products
WHERE product_name LIKE 'S%';
```

---

## Find Average Price

```sql
SELECT AVG(price)
FROM flipkart_products;
```

---

## Find Category Wise Product Count

```sql
SELECT category, COUNT(*)
FROM flipkart_products
GROUP BY category;
```

---

# 28. REAL-TIME INSTAGRAM EXAMPLES

## Instagram Users Table

```sql
CREATE TABLE instagram_users(
user_id INT PRIMARY KEY,
username VARCHAR(100),
followers INT,
following INT
);
```

---

## Insert Data

```sql
INSERT INTO instagram_users VALUES
(1,'mahesh',1200,500),
(2,'vishnu',800,200),
(3,'aparna',5000,1000);
```

---

## Find Popular Users

```sql
SELECT * FROM instagram_users
WHERE followers > 1000;
```

---

# 29. REAL-TIME SWIGGY EXAMPLES

## Swiggy Orders Table

```sql
CREATE TABLE swiggy_orders(
order_id INT PRIMARY KEY,
customer_name VARCHAR(100),
restaurant_name VARCHAR(100),
amount INT
);
```

---

## Insert Data

```sql
INSERT INTO swiggy_orders VALUES
(1,'Rahul','Paradise',450),
(2,'Ajay','KFC',650),
(3,'Vishnu','Dominos',700);
```

---

## Find Highest Order

```sql
SELECT MAX(amount)
FROM swiggy_orders;
```

---

# 30. INTERVIEW QUESTIONS

# Basic Questions

1. What is MySQL?
2. Difference between DELETE, DROP, TRUNCATE?
3. What is PRIMARY KEY?
4. What is FOREIGN KEY?
5. Difference between WHERE and HAVING?
6. Difference between CHAR and VARCHAR?
7. What are joins?
8. Difference between INNER JOIN and LEFT JOIN?
9. What is GROUP BY?
10. What are aggregate functions?

---

# 31. IMPORTANT NOTES

## DELETE vs TRUNCATE vs DROP

| Command  | Deletes Data | Deletes Structure |
| -------- | ------------ | ----------------- |
| DELETE   | Yes          | No                |
| TRUNCATE | Yes          | No                |
| DROP     | Yes          | Yes               |

---

# WHERE vs HAVING

| WHERE           | HAVING         |
| --------------- | -------------- |
| Filters rows    | Filters groups |
| Before GROUP BY | After GROUP BY |

---

# PRIMARY KEY RULES

* Cannot contain NULL
* Must be unique
* One primary key per table

---

# FOREIGN KEY PURPOSE

Maintains relationship between tables.

---

# AUTO_INCREMENT PURPOSE

Automatically generates IDs.

---

# 32. PRACTICE QUERIES

# STUDENT PRACTICE

## Create Table

```sql
CREATE TABLE students_practice(
id INT,
name VARCHAR(100),
marks INT
);
```

---

## Insert Values

```sql
INSERT INTO students_practice VALUES
(1,'Ajay',90),
(2,'Rahul',80),
(3,'Aparna',95);
```

---

## Fetch All Data

```sql
SELECT * FROM students_practice;
```

---

## Students with Marks Greater Than 85

```sql
SELECT * FROM students_practice
WHERE marks > 85;
```

---

## Count Students

```sql
SELECT COUNT(*)
FROM students_practice;
```

---

## Average Marks

```sql
SELECT AVG(marks)
FROM students_practice;
```

---

## Sort Students by Marks

```sql
SELECT * FROM students_practice
ORDER BY marks DESC;
```

---


# SubQueries  
-- A subquery means query inside another query 
-- inner query 
-- outer query (nested query)

#### syntax for subqueries
```sql
 select column_name 
 from table_name 
 where column_name OPERATOER 
 ( 
 select colmun_name from Table_name;
  );
```
-- first query retult -> used by the second query 
-- inner query execuites first then the outer query execute next 

```sql
CREATE DATABASE JFSEMPLOYEES;
USE JFSEMPLOYEES;

CREATE TABLE EMPLOYEES (EMP_ID INT, EMP_NAME VARCHAR(45), EMP_DEPT VARCHAR(25), EMP_SAL INT);

INSERT INTO EMPLOYEES VALUES 
(1,'MAHESH', 'IT',50000),
(2,'RAHUL', 'HR',30000),
(3,'TEJA', 'IT',55000),
(4,'KIRAN', 'SALES',45000),
(5,'SURESH', 'IT',60000),
(6,'INDRA', 'HR',40000),
(7,'RAMESH', 'DEV',20000);

SELECT * FROM EMPLOYEES
```

 ### SUBQUERIES Types
-- SINGLE ROW SUBQURIES --> RETURENS ONE ROW 
-- MULTIPLE ROW SUBQURIES --> RETURNS MULTIPLE ROWS 
-- CORELATED SUBQUERIES --> INNER QUUERY DEPENDS ON OUTER QUERY 
-- NESTED SUBQUERIES --> QUERY INSED QUERY INSIDE ANOTHER QUERY 

 ## SINGLE ROW SUBQURIES 
-- SUBQUERY RETURNS ONLY ONE VALUE

-- TO FINED THE EMPLOYEES EARNING MORE THAN AVERAGE SALARY 
```sql
SELECT AVG(EMP_SAL) FROM EMPLOYEES;
SELECT * FROM EMPLOYEES WHERE EMP_SAL > 42857;


SELECT * FROM EMPLOYEES 
WHERE EMP_SAL > (SELECT AVG(EMP_SAL) FROM EMPLOYEES);
```

## MULTIPLE ROW SUBQUERY 
-- SUBQUERY RETURNS MULTPLE VALUES 
```sql
-- FIND EMPLOYEES FROM DEPERTEMTS WHERE SALARY IS ABOVE 50000;


SELECT EMP_NAME , EMP_DEPT , EMP_SAL
FROM EMPLOYEES 
WHERE EMP_DEPT IN 
(SELECT EMP_DEPT FROM EMPLOYEES WHERE EMP_SAL > 50000 );
```

---

# MySQL Stored Procedures and Triggers - Complete Notes

> Database Used: Banking_System  
> Tables Used:
> - bank_accounts
> - transaction_log
> - deleted_accounts

Based on the same tables and data used in class. :contentReference[oaicite:0]{index=0}

---

# PART 1 : STORED PROCEDURES

# What is a Stored Procedure?

A Stored Procedure is a collection of SQL statements stored inside the database that can be executed whenever needed.

Instead of writing the same SQL query repeatedly, we create a procedure once and call it whenever required.

---

# Advantages of Stored Procedures

1. Reduces code duplication
2. Improves performance
3. Easy maintenance
4. Better security
5. Faster execution
6. Reusable code

---

# Basic Syntax

```sql
DELIMITER //

CREATE PROCEDURE procedure_name()

BEGIN

SQL Statements;

END //

DELIMITER ;
```

---

# Create Database

```sql
CREATE DATABASE Banking_System;

USE Banking_System;
```

---

# Create Table

```sql
CREATE TABLE bank_accounts
(
acc_no INT PRIMARY KEY,
customer_name VARCHAR(50),
balance INT
);
```

---

# Insert Data

```sql
INSERT INTO bank_accounts
(acc_no,customer_name,balance)

VALUES

(1001,'Aarav Sharma',24567),
(1002,'Priya Patel',85643),
(1003,'Rahul Kumar',12345),
(1004,'Ananya Singh',67890),
(1005,'Vikram Reddy',45678),
(1006,'Sneha Gupta',78901),
(1007,'Arjun Mehta',23456),
(1008,'Divya Joshi',56789),
(1009,'Karan Desai',89012),
(1010,'Riya Nair',34567),
(1011,'Siddharth Iyer',11234),
(1012,'Meera Pillai',55678),
(1013,'Rohan Banerjee',77890),
(1014,'Pooja Agarwal',33456),
(1015,'Aditya Verma',66789),
(1016,'Nisha Yadav',88901),
(1017,'Kunal Mishra',22345),
(1018,'Tanya Saxena',44567),
(1019,'Manish Chauhan',55678),
(1020,'Shreya Malhotra',77890),
(1021,'Vishal Thakur',11223),
(1022,'Aishwarya Roy',33445),
(1023,'Gaurav Pandey',55667),
(1024,'Neha Kapoor',77889),
(1025,'Rajesh Jain',99012),
(1026,'Swati Bhatia',22334),
(1027,'Akash Dubey',44556),
(1028,'Kavya Singhania',66778),
(1029,'Prateek Rawat',88990),
(1030,'Anjali Tyagi',11234),
(1031,'Saurabh Biswas',33456),
(1032,'Riddhi Shah',55678),
(1033,'Nikhil Pawar',77890),
(1034,'Simran Kaur',99012),
(1035,'Abhishek Das',22345),
(1036,'Payal Sen',44567),
(1037,'Yashwant Rao',66789),
(1038,'Deepika Shetty',88901);
```

---

# View Data

```sql
SELECT * FROM bank_accounts;
```

---

# Procedure Example 1

## Display all accounts

```sql
DELIMITER //

CREATE PROCEDURE getAllAccounts()

BEGIN

SELECT * FROM bank_accounts;

END //

DELIMITER ;
```

---

# Execute Procedure

```sql
CALL getAllAccounts();
```

---

# Procedure Example 2

## High Balance Accounts

```sql
DELIMITER //

CREATE PROCEDURE HighBalanceAccounts()

BEGIN

SELECT *
FROM bank_accounts
WHERE balance>50000;

END //

DELIMITER ;
```

---

# Execute

```sql
CALL HighBalanceAccounts();
```

---

# Delete Procedure

```sql
DROP PROCEDURE HighBalanceAccounts;
```

---

# Show Procedures

```sql
SHOW PROCEDURE STATUS;
```

---

# Parameters in Procedures

There are 3 types:

1. IN
2. OUT
3. INOUT

---

# IN Parameter

Accepts values from user.

## Syntax

```sql
DELIMITER //

CREATE PROCEDURE procedure_name
(IN variable datatype)

BEGIN

SQL Statements;

END//

DELIMITER ;
```

---

## Example

```sql
DELIMITER //

CREATE PROCEDURE getAccount
(
IN p_accountNo INT
)

BEGIN

SELECT *
FROM bank_accounts
WHERE acc_no=p_accountNo;

END//

DELIMITER ;
```

---

## Execute

```sql
CALL getAccount(1030);
```

---

# OUT Parameter

Returns values to user.

---

## Example

```sql
DELIMITER //

CREATE PROCEDURE GetBalance
(
IN p_accountNo INT,
OUT p_balance INT
)

BEGIN

SELECT balance
INTO p_balance

FROM bank_accounts

WHERE acc_no=p_accountNo;

END//

DELIMITER ;
```

---

## Execute

```sql
CALL GetBalance(1030,@balance);

SELECT @balance;
```

---

# INOUT Parameter

Accepts and returns values.

---

## Example

```sql
DELIMITER //

CREATE PROCEDURE BONUS
(
INOUT amount INT
)

BEGIN

SET amount=amount+5000;

END//

DELIMITER ;
```

---

## Execute

```sql
SET @money=10000;

CALL BONUS(@money);

SELECT @money;
```

---

# Procedure Flow

```text
Create Procedure
       ↓
Store in Database
       ↓
Call Procedure
       ↓
Procedure Executes
       ↓
Returns Result
```

---

# PART 2 : TRIGGERS

# What is Trigger?

A Trigger is a special stored program that automatically executes when an event occurs in a table.

Events:

1. INSERT
2. UPDATE
3. DELETE

---

# Trigger Types

### BEFORE INSERT

Runs before insertion.

### AFTER INSERT

Runs after insertion.

### BEFORE UPDATE

Runs before update.

### AFTER UPDATE

Runs after update.

### BEFORE DELETE

Runs before deletion.

### AFTER DELETE

Runs after deletion.

---

# Trigger Syntax

```sql
DELIMITER //

CREATE TRIGGER trigger_name

BEFORE/AFTER

INSERT/UPDATE/DELETE

ON table_name

FOR EACH ROW

BEGIN

SQL Statements;

END//

DELIMITER ;
```

---

# Create Supporting Tables

## Transaction Log Table

```sql
CREATE TABLE transaction_log
(
id INT AUTO_INCREMENT PRIMARY KEY,
message VARCHAR(200)
);
```

---

## Deleted Accounts Table

```sql
CREATE TABLE deleted_accounts
(
acc_no INT,
customer_name VARCHAR(50),
balance INT
);
```

---

# BEFORE INSERT Trigger

```sql
DELIMITER //

CREATE TRIGGER BEFORE_INSERT_BALANCE

BEFORE INSERT
ON bank_accounts

FOR EACH ROW

BEGIN

IF NEW.balance<1000 THEN

SET NEW.balance=1000;

END IF;

END//

DELIMITER ;
```

---

## Test

```sql
INSERT INTO bank_accounts
VALUES
(1039,'Mahesh',500);

SELECT * FROM bank_accounts;
```

---

# AFTER INSERT Trigger

```sql
DELIMITER //

CREATE TRIGGER AFTER_INSERT_LOG

AFTER INSERT
ON bank_accounts

FOR EACH ROW

BEGIN

INSERT INTO transaction_log(message)

VALUES
(CONCAT
(
'NEW CUSTOMER ADDED : ',
NEW.customer_name
));

END//

DELIMITER ;
```

---

# BEFORE UPDATE Trigger

```sql
DELIMITER //

CREATE TRIGGER BEFORE_UPDATE_BALANCE

BEFORE UPDATE
ON bank_accounts

FOR EACH ROW

BEGIN

IF NEW.balance<0 THEN

SET NEW.balance=0;

END IF;

END//

DELIMITER ;
```

---

# AFTER UPDATE Trigger

```sql
DELIMITER //

CREATE TRIGGER AFTER_UPDATE_LOG

AFTER UPDATE
ON bank_accounts

FOR EACH ROW

BEGIN

INSERT INTO transaction_log(message)

VALUES
(
CONCAT
(
'BALANCE UPDATED FOR : ',
NEW.customer_name
)
);

END//

DELIMITER ;
```

---

# BEFORE DELETE Trigger

```sql
DELIMITER //

CREATE TRIGGER BEFORE_DELETE_BACKUP

BEFORE DELETE
ON bank_accounts

FOR EACH ROW

BEGIN

INSERT INTO deleted_accounts

VALUES
(
OLD.acc_no,
OLD.customer_name,
OLD.balance
);

END//

DELIMITER ;
```

---

# AFTER DELETE Trigger

```sql
DELIMITER //

CREATE TRIGGER AFTER_DELETE_LOG

AFTER DELETE
ON bank_accounts

FOR EACH ROW

BEGIN

INSERT INTO transaction_log(message)

VALUES
(
CONCAT
(
'DELETED CUSTOMER : ',
OLD.customer_name
)
);

END//

DELIMITER ;
```

---

# Show Triggers

```sql
SHOW TRIGGERS;
```

---

# Delete Trigger

```sql
DROP TRIGGER AFTER_DELETE_LOG;
```

---

# Difference Between Procedures and Triggers

| Stored Procedure | Trigger |
|-----------------|----------|
| Called manually | Executes automatically |
| Uses CALL statement | No CALL required |
| Can accept parameters | Cannot accept parameters |
| Can return values | Cannot return values |
| User controls execution | Event controls execution |

---

# Interview Questions

### What is Stored Procedure?

A stored procedure is a stored collection of SQL statements executed when called.

---

### What is Trigger?

A trigger is a stored program that automatically executes when INSERT, UPDATE, or DELETE events occur.

---

### Difference between OLD and NEW?

NEW → New values

OLD → Previous values

---

### Types of Parameters?

IN

OUT

INOUT

---

### Which trigger is used for backup?

BEFORE DELETE

---
