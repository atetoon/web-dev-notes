# 1️⃣ Database Basics

## 1. Database

A **database** is an organized collection of data.

Example:

```
Users
Movies
Products
Orders
```

Instead of storing data in arrays, it's stored permanently in a database.

---

## 2. Relational Database

Stores data in **tables**.

Example:

```
films

name
release_year
rating
runtime
```

Each table consists of:

- Rows (records)
- Columns (fields)

---

## 3. RDBMS

A **Relational Database Management System** is software that manages relational databases.

Examples:

- PostgreSQL ✅
- MySQL
- SQLite
- SQL Server
- Oracle

---

## 4. SQL

SQL is the language used to communicate with relational databases.

You learned the basic CRUD operations:

---

## 5. Constraints

You learned how to protect your data using:

- `PRIMARY KEY`
- `UNIQUE`
- `NOT NULL`
- `DEFAULT`

These prevent invalid data from being stored.

---

## 6. SQL vs NoSQL

### SQL

- Tables
- Fixed schema
- Uses SQL
- PostgreSQL, MySQL

### NoSQL

- Documents, key-value, graph, etc.
- Flexible schema
- MongoDB, Redis

---

## 7. PostgreSQL

You learned how to:

- Install PostgreSQL
- Start/stop the server
- Create databases
- Connect using `psql`
- Create tables
- Insert data
- Update data
- Delete data
- Add constraints

---

# 🛠️ IMPORTANT COMMANDS

```sql
CREATE DATABASE movies_db;
```

```sql
\c movies_db
```

```sql
CREATE TABLE films (...);
```

```sql
INSERT INTO films ...
```

```sql
SELECT * FROM films;
```

```sql
UPDATE films ...
```

```sql
DELETE FROM films ...
```

```sql
ALTER TABLE films ...
```

```sql
DROP TABLE films;
```

---

# 2️⃣SQL Manipulation Commands

## 1. CREATE

Creates a new table.

```sql
CREATE TABLE students (
    id INTEGER,
    name TEXT
);
```

---

## 2. INSERT

Adds a new row.

```sql
INSERT INTO table_name (column1, column2, column3) 
VALUES (value1, value2, value3);
```

---

## 3. SELECT

Retrieves data.

```sql
SELECT * FROM students;
```

or

```sql
SELECT name FROM students;
```

---

## 4. ALTER

Modifies the table structure.

```sql
ALTER TABLE students
ADD COLUMN age INTEGER;
				or
DROP COLUMN xyz TYPE;
```

---

## 5. UPDATE

Modifies existing data.

```sql
UPDATE students
SET age = 20
WHERE id = 1;
```

---

## 6. DELETE

Deletes rows.

```sql
DELETE FROM students
WHERE id = 1;
```

---

# CRUD Mapping

|SQL|Purpose|
|---|---|
|`CREATE TABLE`|Create a table|
|`INSERT INTO`|Add data|
|`SELECT`|Read data|
|`ALTER TABLE`|Modify table structure|
|`UPDATE`|Update data|
|`DELETE`|Delete data|

|CRUD|SQL|
|---|---|
|Create|`INSERT INTO`|
|Read|`SELECT`|
|Update|`UPDATE`|
|Delete|`DELETE`|

> Note: `CREATE TABLE` creates the table itself (schema), while `INSERT INTO` creates new records (data).

---

# Constraints

|Constraint|Purpose|
|---|---|
|`PRIMARY KEY`|Unique identifier for each row|
|`UNIQUE`|Prevent duplicate values|
|`NOT NULL`|Value is required|
|`DEFAULT`|Use a default value if none is provided|

Example:

```sql
CREATE TABLE students (
    id INTEGER PRIMARY KEY,
    email TEXT UNIQUE,
    name TEXT NOT NULL,
    country TEXT DEFAULT 'India'
);
```

---

# SQL Workflow

```
Create Table
      ↓
Insert Data
      ↓
Read Data
      ↓
Modify Data
      ↓
Delete Data
```

Corresponding SQL:

```
CREATE TABLE
      ↓
INSERT INTO
      ↓
SELECT
      ↓
UPDATE
      ↓
DELETE
```

---

# 3️⃣Aggregate Functions

---

# 1. `COUNT()` — Count Rows

Counts the number of rows.

```sql
SELECT COUNT(*)
FROM employees;
```

Count only non-`NULL` values:

```sql
SELECT COUNT(email)
FROM employees;
```

---

# 2. `SUM()` — Total

Adds all values in a numeric column.

```sql
SELECT SUM(salary)
FROM employees;
```

---

# 3. `MAX()` / `MIN()`

Highest value:

```sql
SELECT MAX(salary)
FROM employees;
```

Lowest value:

```sql
SELECT MIN(salary)
FROM employees;
```

---

# 4. `AVG()` — Average

Returns the average value.

```sql
SELECT AVG(salary)
FROM employees;
```

---

# 5. `ROUND()`

Rounds a number to a specified number of decimal places.

```sql
SELECT ROUND(AVG(salary), 2)
FROM employees;
```

---

# 6. `GROUP BY`

Groups rows having the same value so aggregate functions are calculated **per group**.

Without `GROUP BY`:

```sql
SELECT AVG(salary)
FROM employees;
```

Result:

```
55000
```

With `GROUP BY`:

```sql
SELECT department,
       AVG(salary)
FROM employees
GROUP BY department;
```

Result:

|Department|Avg Salary|
|---|---|
|HR|42000|
|IT|67000|
|Sales|51000|

---

# 7. `HAVING`

Filters **groups**, not individual rows.

```sql
SELECT department,
       COUNT(*)
FROM employees
GROUP BY department
HAVING COUNT(*) > 5;
```

Returns only departments having more than 5 employees.

---

# 8. `ORDER BY`

Sorts the final result.

Ascending (default):

```sql
SELECT department,
       AVG(salary)
FROM employees
GROUP BY department
ORDER BY department;
```

Descending:

```sql
SELECT department,
       AVG(salary)
FROM employees
GROUP BY department
ORDER BY AVG(salary) DESC;
```

You can sort by:

- Column name

```sql
ORDER BY department;
```

- Aggregate function

```sql
ORDER BY AVG(salary) DESC;
```

- Column position

```sql
ORDER BY 2 DESC;
```

---

# WHERE vs HAVING

|WHERE|HAVING|
|---|---|
|Filters rows|Filters groups|
|Before `GROUP BY`|After `GROUP BY`|
|Cannot use aggregate functions (`SUM`, `AVG`, etc.)|Used specifically with aggregate functions|

Example:

```sql
SELECT department,
       AVG(salary)
FROM employees
WHERE salary > 30000
GROUP BY department
HAVING AVG(salary) > 50000;
```

Execution:

1. `WHERE`
2. `GROUP BY`
3. Aggregate Functions
4. `HAVING`

---

# Complete SQL Clause Order ⭐

```sql
SELECT
FROM
WHERE
GROUP BY
HAVING
ORDER BY
LIMIT
```

Example:

```sql
SELECT category,
       AVG(downloads)
FROM fake_apps
WHERE price = 0
GROUP BY category
HAVING AVG(downloads) > 10000
ORDER BY AVG(downloads) DESC
LIMIT 5;
```

# Aggregate Functions Summary

|Function / Clause|Purpose|
|---|---|
|`COUNT()`|Count rows|
|`SUM()`|Sum values|
|`AVG()`|Calculate average|
|`MAX()`|Largest value|
|`MIN()`|Smallest value|
|`ROUND()`|Round numbers|
|`GROUP BY`|Group rows for aggregate calculations|
|`HAVING`|Filter groups|
|`ORDER BY`|Sort results (`ASC`/`DESC`)|

---

# 4️⃣ Multiple Tables

Relational databases become powerful when multiple tables are connected.

Example:

```
Customers
Orders
Products
```

Instead of storing everything in one table, data is split into related tables.

---

# Why Multiple Tables?

Instead of:

```
Order ID
Customer Name
Customer Address
Product Name
Product Price
```

Store data separately:

```
Customers
Orders
Products
```

Advantages:

- Less redundancy
- Less storage
- Easier updates
- Better organization

---

# 1. INNER JOIN (`JOIN`)

Combines matching rows from two tables.

```sql
SELECT table_one.column_one AS alias_one, table_two.column_two AS alias_two, table_three.column_three AS alias_three
FROM table_one
INNER JOIN table_two
ON table_one.primary_key = table_two.foreign_key
INNER JOIN table_three
ON table_two.primary_key = table_three.foreign_key;
```

```sql
SELECT *
FROM orders
JOIN customers
ON orders.customer_id = customers.customer_id;
```

Only matching rows are returned.

Visualization:

```
Orders        Customers

1 ---------> Customer 1
2 ---------> Customer 2
3 ---------> Customer 3
```

---

# 2. LEFT JOIN

Returns every row from the **left table**.

If no match exists, the right side becomes `NULL`.

```sql
SELECT *
FROM customers
LEFT JOIN orders
ON customers.id = orders.customer_id;
```

Find customers with no orders:

```sql
SELECT *
FROM customers
LEFT JOIN orders
ON customers.id = orders.customer_id
WHERE orders.customer_id IS NULL;
```

---

# 3. CROSS JOIN

Returns every possible combination.

```sql
SELECT *
FROM shirts
CROSS JOIN pants;
```

If:

```
3 shirts
2 pants
```

Result:

```
3 × 2 = 6 rows
```

---

# 4. UNION

Stacks two result sets vertically.

```sql
SELECT *
FROM newspaper

UNION

SELECT *
FROM online;
```

Requirements:

- Same number of columns
- Same data types
- Same column order

---

# 5. WITH (CTE)

Creates a temporary table for the query.

```sql
WITH sales AS (

SELECT customer_id,
       COUNT(*) AS total_orders
FROM orders
GROUP BY customer_id

)

SELECT *
FROM sales;
```

Useful for breaking large queries into smaller readable parts.

---

# Primary Key vs Foreign Key

### Primary Key (PK)

Uniquely identifies a row.

```
Customers

customer_id (PK)
```

---

### Foreign Key (FK)

References another table's Primary Key.

```
Orders

customer_id (FK)
```

Relationship:

```
Customers
customer_id (PK)
        ▲
        │
        │
Orders
customer_id (FK)
```

---

# Old vs Modern JOIN

Old syntax:

```sql
SELECT *
FROM person, email
WHERE person.id = email.person_id;
```

Modern syntax: ✅

```sql
SELECT *
FROM person
JOIN email
ON person.id = email.person_id;
```

Prefer the modern syntax.

---

# Multiple Tables Summary

|Clause|Purpose|
|---|---|
|`JOIN`|Matching rows|
|`LEFT JOIN`|Keep all rows from left table|
|`CROSS JOIN`|Every possible combination|
|`UNION`|Stack two queries|
|`WITH`|Temporary table (CTE)|

---

# 5️⃣ Database Schema

A **Database Schema** is the blueprint of a database.

It describes:

- Tables
- Columns
- Data types
- Constraints
- Relationships

---

# Designing a Schema

Steps:

1. Define the database purpose.
2. Identify the entities.
3. Create tables.
4. Define columns.
5. Choose data types.
6. Avoid redundant data.
7. Create relationships.

---

# Common PostgreSQL Data Types

|Data Type|Purpose|
|---|---|
|`INTEGER`|Whole numbers|
|`DECIMAL(p,s)`|Decimal numbers|
|`MONEY`|Currency|
|`BOOLEAN`|True / False|
|`CHAR(n)`|Fixed-length text|
|`VARCHAR(n)`|Variable-length text|
|`TEXT`|Unlimited text|

---

# Creating Tables

```sql
CREATE TABLE book (

title VARCHAR(100),
isbn VARCHAR(50),
pages INTEGER,
price MONEY,
description VARCHAR(256),
publisher VARCHAR(100)

);
```

---

# Inserting Data

```sql
INSERT INTO book
VALUES (
'Postgres Basics',
'12345',
250,
19.99,
'Learn PostgreSQL',
'Codecademy'
);
```

---

# Querying Data

```sql
SELECT *
FROM book;
```

---

# Database Schema Summary

|Topic|Purpose|
|---|---|
|Schema|Database blueprint|
|Tables|Store related data|
|Columns|Store attributes|
|Data Types|Define allowed values|
|Relationships|Connect tables|

---

# 6️⃣ Database Keys

Keys uniquely identify rows and connect tables.

---

# 1. Primary Key (PK)

Uniquely identifies each row.

Rules:

- Unique
- Cannot be `NULL`
- One primary key constraint per table

```sql
CREATE TABLE users (

id INTEGER PRIMARY KEY,
name VARCHAR(50)

);
```

---

# 2. Composite Primary Key

Used when a single column isn't unique.

```sql
PRIMARY KEY
(student_id, course_id)
```

Example:

|student_id|course_id|
|---|---|
|1|101|
|1|102|
|2|101|

Neither column is unique, but together they are.

---

# 3. Foreign Key (FK)

References another table's Primary Key.

```sql
CREATE TABLE chapter (

id INTEGER PRIMARY KEY,
title VARCHAR(50),

book_isbn VARCHAR(50)
REFERENCES book(isbn)

);
```

Relationship:

```
Book

isbn (PK)

      ▲
      │
      │
Chapter

book_isbn (FK)
```

One book can have many chapters.

---

# Joining Related Tables

```sql
SELECT
book.title AS book,
chapter.title AS chapter
FROM book
JOIN chapter
ON book.isbn = chapter.book_isbn;
```

---

# Validating Keys

PostgreSQL stores metadata in `information_schema`.

```sql
SELECT
constraint_name,
table_name,
column_name
FROM information_schema.key_column_usage
WHERE table_name = 'book';
```

---

# Primary Key vs Foreign Key

|Primary Key|Foreign Key|
|---|---|
|Identifies a row|References another table|
|Unique|Can repeat|
|Cannot be NULL|May be NULL|
|One per table|Multiple allowed|

---

# Database Keys Summary

|Key|Purpose|
|---|---|
|`PRIMARY KEY`|Unique row identifier|
|`COMPOSITE PRIMARY KEY`|Unique combination of columns|
|`FOREIGN KEY`|Creates relationships between tables|

---

# SQL Clause Order ⭐

```sql
SELECT
FROM
JOIN
ON
WHERE
GROUP BY
HAVING
ORDER BY
LIMIT
```

---

# Query Execution Order ⭐

```
FROM
JOIN
ON
WHERE
GROUP BY
Aggregate Functions
HAVING
SELECT
ORDER BY
LIMIT
```

---

# 7️⃣ Database Relationships

Relationships define how tables are connected.

There are **3 types**:

- One-to-One (1:1)
- One-to-Many (1:N)
- Many-to-Many (M:N)

---

# 1. One-to-One (1:1)

One row in table A corresponds to exactly one row in table B.

Example:

```
Restaurant ───── Address
```

Each restaurant has one address.

Each address belongs to one restaurant.

Implementation:

```sql
CREATE TABLE address (
    id INTEGER PRIMARY KEY,
    street VARCHAR(50),

    restaurant_id INTEGER
    REFERENCES restaurant(id)
    UNIQUE
);
```

The `UNIQUE` constraint on the foreign key enforces the one-to-one relationship.

Visualization:

```
Restaurant

id = 1
      │
      │
      ▼

Address

restaurant_id = 1
```

---

# 2. One-to-Many (1:N)

One row in table A can relate to many rows in table B.

Example:

```
Restaurant ─────< Review
```

A restaurant can have many reviews.

Each review belongs to one restaurant.

Implementation:

```sql
CREATE TABLE review (
    id INTEGER PRIMARY KEY,
    rating DECIMAL,

    restaurant_id INTEGER
    REFERENCES restaurant(id)
);
```

Visualization:

```
Restaurant

id = 1
      │
      ├────────► Review 1
      ├────────► Review 2
      └────────► Review 3
```

No `UNIQUE` is used because multiple reviews can reference the same restaurant.

---

# 3. Many-to-Many (M:N)

Many rows in table A can relate to many rows in table B.

Example:

```
Category ↔ Dish
```

A category contains many dishes.

A dish can appear in many categories.

This cannot be implemented directly.

We create a **junction (cross-reference) table**.

```sql
CREATE TABLE categories_dishes (

    category_id VARCHAR(2)
    REFERENCES category(id),

    dish_id INTEGER
    REFERENCES dish(id),

    price MONEY,

    PRIMARY KEY(category_id, dish_id)

);
```

Visualization:

```
Category
     │
     │
     ▼

categories_dishes

     ▲
     │
     │

Dish
```

---

# Why Composite Primary Key?

In a junction table, neither foreign key is unique individually.

Example:

```
category_id   dish_id

C             1
LS            1
HS            6
```

`category_id` repeats.

`dish_id` repeats.

But together:

```
(C,1)
(LS,1)
(HS,6)
```

are unique.

So we use:

```sql
PRIMARY KEY(category_id, dish_id)
```

This prevents duplicate category–dish pairs.

---

# Relationship Summary

|Relationship|Foreign Key|UNIQUE|Junction Table|
|---|---|---|---|
|One-to-One|✅|✅|❌|
|One-to-Many|✅|❌|❌|
|Many-to-Many|✅|❌|✅|

---

# How to Identify Relationships

|Situation|Relationship|
|---|---|
|One person → One passport|One-to-One|
|One restaurant → Many reviews|One-to-Many|
|One category → Many dishes, one dish → Many categories|Many-to-Many|

---

# Example ER Diagram

```
Restaurant
     │
     │ 1:1
     ▼
Address

Restaurant
     │
     │ 1:N
     ▼
Review

Category
     │
     │
     ▼
categories_dishes
     ▲
     │
Dish
```

---

# Relationship Implementation Cheat Sheet ⭐

|Relationship|SQL Implementation|
|---|---|
|One-to-One|`FOREIGN KEY + UNIQUE`|
|One-to-Many|`FOREIGN KEY`|
|Many-to-Many|`Junction Table + 2 Foreign Keys + Composite Primary Key`|

---

# 8️⃣ Database Triggers

---

# 1. What is a Trigger?

A **trigger** is a block of SQL code that **automatically executes** when a specified event occurs on a table or view.

Think of it as an automatic event listener for your database.

Example events:

- `INSERT`
- `UPDATE`
- `DELETE`
- `TRUNCATE`

---

# Why Use Triggers?

Without a trigger:

```
UPDATE Customer

↓

Developer forgets to update
last_modified
```

With a trigger:

```
UPDATE Customer

↓

Trigger executes

↓

last_modified updated automatically
```

Triggers help maintain **data integrity** and **business rules**.

---

# Common Uses

- Audit logs
- Automatically update timestamps
- Validate data
- Maintain consistency
- Synchronize tables
- Enforce business rules

---

# General Trigger Syntax

```sql
CREATE TRIGGER trigger_name
BEFORE | AFTER
INSERT | UPDATE | DELETE | TRUNCATE
ON table_name
FOR EACH ROW | FOR EACH STATEMENT
[WHEN (condition)]
EXECUTE PROCEDURE function_name();
```

> Newer PostgreSQL versions use `EXECUTE FUNCTION` instead of `EXECUTE PROCEDURE`.

---

# Trigger Function

Triggers execute **functions**, not SQL directly.

Example:

```sql
CREATE OR REPLACE FUNCTION check_account_update()
RETURNS TRIGGER AS $$

BEGIN
    NEW.active := TRUE;
    RETURN NEW;
END;

$$ LANGUAGE plpgsql;
```

---

# Supported Events

|Event|Fires When|
|---|---|
|`INSERT`|Row inserted|
|`UPDATE`|Row updated|
|`DELETE`|Row deleted|
|`TRUNCATE`|Table emptied|

---

# BEFORE vs AFTER

## BEFORE

Runs **before** the SQL statement.

Can modify the row.

Example:

```sql
CREATE TRIGGER update_trigger
BEFORE UPDATE
ON customers
FOR EACH ROW
EXECUTE PROCEDURE update_function();
```

Flow:

```
UPDATE

↓

BEFORE Trigger

↓

Modify NEW row

↓

Save Row
```

---

## AFTER

Runs **after** the SQL statement.

Cannot modify the saved row.

Used for:

- Audit logs
- Notifications
- Statistics
- Logging

Example:

```sql
CREATE TRIGGER log_trigger
AFTER UPDATE
ON customers
FOR EACH ROW
EXECUTE PROCEDURE log_changes();
```

Flow:

```
UPDATE

↓

Row Saved

↓

AFTER Trigger

↓

Insert Log
```

---

# FOR EACH ROW vs FOR EACH STATEMENT

## FOR EACH ROW

Runs once **for every affected row**.

Example:

```sql
UPDATE customers
SET age = age + 1;
```

10 rows updated

↓

Trigger executes **10 times**

---

## FOR EACH STATEMENT

Runs once **for the entire SQL statement**.

Same update:

10 rows updated

↓

Trigger executes **1 time**

---

## Comparison

|Feature|FOR EACH ROW|FOR EACH STATEMENT|
|---|---|---|
|Executes per row|✅|❌|
|Executes per query|❌|✅|
|Performance|Slower|Faster|
|Best for|Validation, row modifications|Logging, auditing|

---

# WHEN Clause

Sometimes a trigger should execute only under certain conditions.

Syntax:

```sql
CREATE TRIGGER trigger_name
BEFORE UPDATE
ON clients
FOR EACH ROW
WHEN (condition)
EXECUTE PROCEDURE function_name();
```

---

Example:

```sql
CREATE TRIGGER update_trigger_high
BEFORE UPDATE
ON clients
FOR EACH ROW
WHEN (NEW.total_spent >= 1000)
EXECUTE PROCEDURE set_high_spender();
```

Only executes when:

```
NEW.total_spent >= 1000
```

---

# NEW and OLD

Trigger functions can access two special records.

## NEW

Represents the row **after** modification.

Available for:

- INSERT
- UPDATE

Example:

```sql
NEW.salary
```

---

## OLD

Represents the row **before** modification.

Available for:

- UPDATE
- DELETE

Example:

```sql
OLD.salary
```

---

## Availability

|Event|OLD|NEW|
|---|---|---|
|INSERT|❌|✅|
|UPDATE|✅|✅|
|DELETE|✅|❌|

---

# Multiple Triggers

A table may have multiple triggers for the same event.

Example:

```sql
CREATE TRIGGER update_alpha ...
```

```sql
CREATE TRIGGER update_bravo ...
```

Both execute.

---

# Trigger Execution Order

Multiple triggers execute **alphabetically by trigger name**.

Example:

```
audit_trigger

↓

log_trigger

↓

security_trigger
```

Creation order **does not matter**.

---

# Trigger Chaining

One trigger can activate another.

Example:

```
DELETE Customer

↓

DELETE Trigger

↓

Insert into customers_deleted

↓

INSERT Trigger

↓

Update security table
```

One SQL statement may cause several triggers to execute.

---

# SELECT Cannot Have Triggers

Triggers only exist for operations that modify data.

Supported:

- INSERT
- UPDATE
- DELETE
- TRUNCATE

Not supported:

```sql
SELECT * FROM customers;
```

Reason:

`SELECT` does not modify rows.

---

# Removing Triggers

Remove a trigger:

```sql
DROP TRIGGER trigger_name
ON table_name;
```

Example:

```sql
DROP TRIGGER insert_trigger
ON customers;
```

Only the trigger is removed.

The trigger function remains.

---

# View Existing Triggers

```sql
SELECT *
FROM information_schema.triggers;
```

Returns:

- Trigger name
- Table
- Event
- Timing

---

# Trigger Lifecycle

```
Create Trigger

↓

Database Uses Trigger

↓

View Trigger

↓

DROP TRIGGER

↓

Trigger Removed
```

---

# Trigger Flow

```
INSERT / UPDATE / DELETE / TRUNCATE

↓

Trigger Checks

↓

WHEN condition?

├── TRUE
│      ↓
│  Execute Function
│
└── FALSE
       ↓
   Do Nothing
```

---

# Summary Table

|Feature|Description|
|---|---|
|Trigger|Automatically executes SQL code|
|Fires On|`INSERT`, `UPDATE`, `DELETE`, `TRUNCATE`|
|BEFORE|Runs before operation; can modify `NEW`|
|AFTER|Runs after operation; used for logging/auditing|
|FOR EACH ROW|Runs once per affected row|
|FOR EACH STATEMENT|Runs once per SQL statement|
|`WHEN`|Executes trigger only if condition is true|
|`NEW`|New row values|
|`OLD`|Old row values|
|Multiple Triggers|Allowed on the same table|
|Execution Order|Alphabetical by trigger name|
|SELECT Trigger|❌ Not supported|
|Remove Trigger|`DROP TRIGGER`|
|View Triggers|`information_schema.triggers`|

---

# Complete Trigger Syntax ⭐

```sql
CREATE TRIGGER trigger_name
BEFORE | AFTER
INSERT | UPDATE | DELETE | TRUNCATE
ON table_name
FOR EACH ROW | FOR EACH STATEMENT
WHEN (condition)
EXECUTE PROCEDURE function_name();
```

---

# Quick Cheat Sheet ⭐

|Task|Command|
|---|---|
|Create Trigger|`CREATE TRIGGER`|
|Remove Trigger|`DROP TRIGGER`|
|View Triggers|`SELECT * FROM information_schema.triggers;`|
|Before Operation|`BEFORE`|
|After Operation|`AFTER`|
|Per Row|`FOR EACH ROW`|
|Per Query|`FOR EACH STATEMENT`|
|Conditional Trigger|`WHEN (...)`|
|New Values|`NEW.column_name`|
|Old Values|`OLD.column_name`|

---

# 9️⃣ Designing Relational Databases

---

# 1. Database Schema

A **database schema** is the **blueprint** of a database.

It describes:

- Tables
- Columns
- Data types
- Constraints
- Relationships

Think of it as the architectural plan before building the database.

---

## Steps to Design a Schema

1. Define the purpose of the database.
2. Identify the data to store.
3. Organize the data into tables.
4. Define columns and data types.
5. Remove redundant data.
6. Define relationships between tables.

---

# 2. Entity Relationship Diagram (ERD)

An **ERD (Entity Relationship Diagram)** is a visual representation of a database.

Instead of SQL, it shows the database as connected boxes.

Example:

```
Customer
---------
customer_id
name
email
      │
      │
      ▼
Order
---------
order_id
customer_id
amount
```

---

## ERD Components

### Entity

Represents a table.

Example:

```
+-----------+
| Customer  |
+-----------+
```

---

### Attributes

Represent columns.

```
Customer

customer_id
name
email
phone
```

---

### Relationships

Represent how tables are connected.

Example:

```
Customer

1 ------- *

Orders
```

One customer can have many orders.

---

### Connecting Lines

Show relationships and cardinality.

Examples:

```
1 ----- 1
```

One-to-One

```
1 ----- *
```

One-to-Many

```
* ----- *
```

Many-to-Many

---

# 3. Database Relationships

---

## One-to-One (1:1)

One row matches exactly one row.

Example:

```
Restaurant

1 -------- 1

Address
```

Implementation:

- Foreign key
- `UNIQUE`

```sql
restaurant_id INTEGER REFERENCES restaurant(id) UNIQUE
```

---

## One-to-Many (1:N)

One parent has many children.

Example:

```
Restaurant

1 -------- *

Review
```

Implementation:

Foreign key on child table.

```sql
restaurant_id INTEGER REFERENCES restaurant(id)
```

---

## Many-to-Many (M:N)

Many records on both sides.

Example:

```
Dish

* -------- *

Category
```

Requires a **junction (cross-reference) table**.

Example:

```
categories_dishes

category_id
dish_id
```

---

# 4. Keys

---

## Primary Key

Uniquely identifies each row.

```sql
id INTEGER PRIMARY KEY
```

Rules:

- Unique
- Cannot be NULL

---

## Foreign Key

References another table's primary key.

```sql
restaurant_id
REFERENCES restaurant(id)
```

Purpose:

- Connect tables
- Maintain referential integrity

---

## Composite Primary Key

Primary key made from multiple columns.

```sql
PRIMARY KEY(category_id, dish_id)
```

Neither column alone is unique.

The combination is.

Example:

|category_id|dish_id|
|---|---|
|C|1|
|C|2|
|LS|1|

Each pair is unique.

---

# 5. Database Normalization (Basic Idea)

Normalization means:

> Organize data to reduce redundancy.

Bad:

```
Restaurant

Dish1
Dish2
Dish3
Dish4
```

Good:

```
Restaurant

↓

Dish Table

↓

Relationship
```

Benefits:

- Less duplicate data
- Easier updates
- Better consistency
- Better scalability

---

# 6. Three-Tier Architecture

Modern applications are usually divided into **three layers**.

```
Presentation

↓

Application

↓

Data
```

---

## Presentation Tier

The user interface.

Examples:

- HTML
- CSS
- JavaScript
- React

Responsibilities:

- Display data
- Receive user input

---

## Application Tier

The backend.

Examples:

- Node.js
- Java
- Python
- Express

Responsibilities:

- Business logic
- Validation
- Processing
- Database queries

Acts as the bridge between frontend and database.

---

## Data Tier

The database itself.

Examples:

- PostgreSQL
- MySQL
- MongoDB

Responsibilities:

- Store data
- Retrieve data

No business logic.

---

## Architecture Flow

```
User

↓

Frontend (Presentation)

↓

Backend (Application)

↓

Database (Data)

↓

Backend

↓

Frontend

↓

User
```

---

# Why Use Three-Tier Architecture?

- Easier maintenance
- Independent scaling
- Better security
- Clear separation of responsibilities
- Teams can work independently

Example:

Frontend team changes UI without touching the database.

---

# 7. Schema Design Tools

Popular tools:

- **[dbdiagram.io](http://dbdiagram.io)** ⭐
- DBDesigner
- SQLDBM
- Lucidchart

These generate ER diagrams and often SQL code.

---

# 8. Schema Design Best Practices

- Use meaningful table names.
- Keep one concept per table.
- Avoid duplicate data.
- Use primary keys.
- Use foreign keys.
- Normalize data.
- Clearly define relationships.
- Choose appropriate data types.

---

# Relationship Summary

|Relationship|Example|Implementation|
|---|---|---|
|One-to-One|Restaurant ↔ Address|FK + `UNIQUE`|
|One-to-Many|Restaurant → Reviews|FK in child table|
|Many-to-Many|Categories ↔ Dishes|Junction table + Composite PK|

---

# Key Summary

|Key|Purpose|
|---|---|
|Primary Key|Uniquely identifies a row|
|Foreign Key|Links tables|
|Composite Primary Key|Uniquely identifies a row using multiple columns|

---

# ERD Symbols Cheat Sheet

```
[Entity]
   │
Attributes

Customer
---------
customer_id (PK)
name
email
```

```
1 ───── 1
```

One-to-One

```
1 ───── *
```

One-to-Many

```
* ───── *
```

Many-to-Many

---

# 6️⃣ PostgreSQL Constraints

Constraints are rules that control what data is allowed in a table. They help maintain **data integrity**, prevent invalid data, and enforce relationships between tables.

---

# Why Constraints?

Without constraints, a database could contain:

- Missing required values
- Duplicate records
- Invalid numbers
- Broken relationships

Constraints prevent these issues automatically.

---

# 1. Data Types

The first level of validation.

They define **what kind of data** a column can store.

Example:

```sql
CREATE TABLE attendees (
    id INTEGER,
    name VARCHAR,
    total_tickets_reserved INTEGER
);
```

Common types:

|Data Type|Purpose|
|---|---|
|`INTEGER`|Whole numbers|
|`VARCHAR(n)`|Variable-length text|
|`TEXT`|Unlimited text|
|`BOOLEAN`|True/False|
|`DATE`|Date|
|`TIME`|Time|
|`NUMERIC(a,b)`|Decimal numbers|

> Data types validate the type of data, not business rules.

---

# 2. NOT NULL

Ensures a column always has a value.

```sql
CREATE TABLE speakers (
    id INTEGER,
    email VARCHAR NOT NULL,
    name VARCHAR NOT NULL
);
```

Adding later:

```sql
ALTER TABLE speakers
ALTER COLUMN name
SET NOT NULL;
```

Removing:

```sql
ALTER TABLE speakers
ALTER COLUMN name
DROP NOT NULL;
```

Backfill before adding:

```sql
UPDATE speakers
SET organization = 'Unknown'
WHERE organization IS NULL;
```

---

# 3. CHECK

Applies custom validation rules.

Example:

```sql
CHECK (estimated_length > 0)
```

Add later:

```sql
ALTER TABLE talks
ADD CHECK (estimated_length > 0);
```

Multiple conditions:

```sql
CHECK (
    estimated_length > 0
    AND estimated_length < 120
)
```

Compare columns:

```sql
CHECK (
    standard_tickets_reserved +
    vip_tickets_reserved =
    total_tickets_reserved
)
```

Useful operators:

- `AND`
- `OR`
- `BETWEEN`
- `IN`
- `LIKE`

---

# 4. UNIQUE

Prevents duplicate values.

Single column:

```sql
email VARCHAR UNIQUE
```

Or:

```sql
ALTER TABLE attendees
ADD UNIQUE (email);
```

Composite UNIQUE:

```sql
UNIQUE (attendee_id, session_timeslot)
```

This makes the **combination** unique.

---

# 5. PRIMARY KEY

Uniquely identifies every row.

Rules:

- Unique
- Not NULL

```sql
id INTEGER PRIMARY KEY
```

Or:

```sql
ALTER TABLE speakers
ADD PRIMARY KEY (id);
```

Composite PK:

```sql
PRIMARY KEY (student_id, course_id)
```

Comparison:

|PRIMARY KEY|UNIQUE|
|---|---|
|One per table|Many allowed|
|Unique|Unique|
|NOT NULL|NULL allowed unless specified|

---

# 6. FOREIGN KEY

Creates relationships between tables.

```sql
FOREIGN KEY (speaker_id)
REFERENCES speakers(id)
```

Or:

```sql
ALTER TABLE talks
ADD FOREIGN KEY (speaker_id)
REFERENCES speakers(id);
```

Foreign keys enforce **referential integrity**.

A child row cannot reference a parent row that doesn't exist.

---

# Parent & Child Tables

```
Parent Table
-------------
speakers
id (PK)

        ▲
        │

Child Table
-------------
talks
speaker_id (FK)
```

---

# 7. Cascading Changes

## Default (`RESTRICT`)

Deleting a parent row with existing children is blocked.

```
Delete Parent

↓

Child Exists

↓

❌ ERROR
```

---

## ON DELETE CASCADE

Automatically deletes child rows.

```sql
FOREIGN KEY (speaker_id)
REFERENCES speakers(id)
ON DELETE CASCADE
```

Example:

Delete a speaker:

```sql
DELETE FROM speakers
WHERE id = 2;
```

All talks by that speaker are automatically deleted.

---

## ON UPDATE CASCADE

Automatically updates foreign keys if the parent primary key changes.

```sql
FOREIGN KEY (speaker_id)
REFERENCES speakers(id)
ON UPDATE CASCADE
```

---

# Improving Existing Tables

Modify an existing table:

```sql
ALTER TABLE table_name
```

Common operations:

```sql
ALTER TABLE talks
ALTER COLUMN title SET NOT NULL;
```

```sql
ALTER TABLE attendees
ADD UNIQUE(email);
```

```sql
ALTER TABLE speakers
ADD PRIMARY KEY(id);
```

```sql
ALTER TABLE talks
ADD CHECK (estimated_length > 0);
```

```sql
ALTER TABLE registrations
ADD FOREIGN KEY (talk_id)
REFERENCES talks(id);
```

---

# Constraint Summary

|Constraint|Purpose|
|---|---|
|Data Type|Defines allowed data type|
|`NOT NULL`|Prevent missing values|
|`CHECK`|Enforce custom rules|
|`UNIQUE`|Prevent duplicates|
|`PRIMARY KEY`|Unique identifier (`UNIQUE + NOT NULL`)|
|`FOREIGN KEY`|Maintain relationships between tables|
|`ON DELETE CASCADE`|Delete child rows automatically|
|`ON UPDATE CASCADE`|Update child foreign keys automatically|

---

# Choosing the Right Constraint

|Requirement|Constraint|
|---|---|
|Value required|`NOT NULL`|
|Positive number|`CHECK`|
|Email must be unique|`UNIQUE`|
|Unique row identifier|`PRIMARY KEY`|
|Link two tables|`FOREIGN KEY`|
|Delete child records with parent|`ON DELETE CASCADE`|
|Update child references automatically|`ON UPDATE CASCADE`|

---

# 🔟 PostgreSQL Roles & Database Security

## 1. Roles

A **role** represents a database user or a group of users.

Types:

- **Login Role** → Can log in.
- **Group Role** → Holds permissions for other roles.

---

## 2. Superuser

Has unrestricted access.

Can:

- Create databases
- Create roles
- Grant/Revoke permissions
- Bypass permission checks

Check current user:

```sql
SELECT current_user;
```

---

## 3. Create & Modify Roles

Create:

```sql
CREATE ROLE analyst
WITH LOGIN NOSUPERUSER;
```

Alter:

```sql
ALTER ROLE analyst
WITH CREATEDB;
```

---

## 4. Role Permissions

|Permission|Purpose|
|---|---|
|`LOGIN`|Can log in|
|`SUPERUSER`|Full access|
|`CREATEDB`|Create databases|
|`CREATEROLE`|Create roles|

---

## 5. Grant & Revoke

Grant schema access:

```sql
GRANT USAGE, CREATE
ON SCHEMA finance
TO analyst;
```

Grant table access:

```sql
GRANT SELECT, INSERT, UPDATE
ON finance.sales
TO analyst;
```

Remove permission:

```sql
REVOKE UPDATE
ON finance.sales
FROM analyst;
```

---

## 6. Default Privileges

Automatically grant permissions to future tables.

```sql
ALTER DEFAULT PRIVILEGES
IN SCHEMA finance
GRANT SELECT
ON TABLES TO analyst;
```

---

## 7. Group Roles

Create group:

```sql
CREATE ROLE employees NOLOGIN;
```

Add member:

```sql
GRANT employees TO alice;
```

Members inherit group permissions.

---

## 8. Column-Level Security

Restrict specific columns.

```sql
GRANT SELECT (name, email)
ON users TO manager;
```

Grant update on selected columns:

```sql
GRANT UPDATE (status)
ON projects TO manager;
```

---

## 9. Row-Level Security (RLS)

Restrict access to specific rows.

Create policy:

```sql
CREATE POLICY sales_policy
ON accounts
FOR SELECT
TO sales
USING (salesperson = current_user);
```

Enable:

```sql
ALTER TABLE accounts
ENABLE ROW LEVEL SECURITY;
```

---

## Security Summary

|Feature|Purpose|
|---|---|
|Role|Database user/group|
|GRANT|Give permission|
|REVOKE|Remove permission|
|Default Privileges|Future table permissions|
|Group Roles|Shared permissions|
|Column Security|Restrict columns|
|Row-Level Security|Restrict rows|

---

# 1️⃣1️⃣ ACID Properties

Transactions must satisfy **ACID**.

## Transaction

A sequence of SQL operations treated as **one unit of work**.

---

## Atomicity

**All or Nothing**

- Every operation succeeds
- Otherwise rollback

---

## Consistency

Database remains **valid** before and after the transaction.

Example:

- No broken constraints
- Data integrity preserved

---

## Isolation

Concurrent transactions don't interfere.

Appears as if transactions run one after another.

---

## Durability

Once committed, data is permanent.

Survives crashes and power failures.

---

## ACID Summary

|Property|Meaning|
|---|---|
|Atomicity|All or nothing|
|Consistency|Valid state maintained|
|Isolation|Transactions don't interfere|
|Durability|Committed data persists|

**Mnemonic:** **A**ll, **C**orrect, **I**ndependent, **D**urable.

---

# 1️⃣2️⃣ SQL Injection

## SQL Injection

A security attack where malicious SQL is inserted into user input.

Example:

```sql
' OR 1=1 --
```

Can bypass authentication or expose data.

---

## Types

### UNION-Based

Uses `UNION` to retrieve extra data.

### Error-Based

Extracts data from database error messages.

### Boolean-Based

Infers information using TRUE/FALSE conditions.

### Time-Based

Uses delays (`SLEEP()`) to infer information.

### Out-of-Band

Exfiltrates data through another channel (DNS/HTTP).

---

## Prevention

### 1. Prepared Statements ✅

Safest method.

```sql
SELECT * FROM users
WHERE name = ?;
```

User input is treated only as data.

---

### 2. Input Sanitization

Escape/remove dangerous characters:

- `'`
- `;`
- `-`

Useful, but **not sufficient alone**.

---

## SQL Injection Summary

|Topic|Purpose|
|---|---|
|SQL Injection|Malicious SQL via input|
|UNION|Retrieve extra data|
|Error-Based|Leak via errors|
|Boolean-Based|Infer TRUE/FALSE|
|Time-Based|Infer using delays|
|Out-of-Band|External data exfiltration|
|Prevention|Prepared Statements > Sanitization|

---

# 1️⃣3️⃣Indexes — Complete Summary 📚

## What is an Index?

An **index** is a data structure that helps PostgreSQL **find rows faster** without scanning the entire table.

Most indexes use a **B-Tree**, giving search performance of approximately **O(log n)** instead of **O(n)**.

---

## Why Use Indexes?

Indexes improve the performance of:

- `SELECT`
- `WHERE`
- `JOIN ... ON`
- `ORDER BY`
- (Sometimes) `GROUP BY`

Instead of performing a **Sequential Scan**, PostgreSQL can directly locate the required rows.

---

## View Existing Indexes

```sql
SELECT *
FROM pg_indexes
WHERE tablename = '<table_name>';
```

Lists all indexes on a table.

---

## Analyze Query Performance

```sql
EXPLAIN ANALYZE
SELECT *
FROM customers;
```

Useful for checking:

- Query execution plan
- Whether an index is used
- Planning time
- Execution time

Look for:

- `Seq Scan` → No index used
- `Index Scan` / `Bitmap Index Scan` → Index used

---

## Create an Index

```sql
CREATE INDEX index_name
ON table_name(column_name);
```

Example:

```sql
CREATE INDEX customers_user_name_idx
ON customers(user_name);
```

---

## Multicolumn (Composite) Index

Create an index on multiple columns:

```sql
CREATE INDEX index_name
ON table_name(column1, column2);
```

Example:

```sql
CREATE INDEX customers_last_name_first_name_idx
ON customers(last_name, first_name);
```

**Important:** Column order matters.

- `(last_name, first_name)` ≠ `(first_name, last_name)`

---

## Drop an Index

```sql
DROP INDEX IF EXISTS index_name;
```

Example:

```sql
DROP INDEX IF EXISTS customers_city_idx;
```

Only the index is removed; the table and its data remain unchanged.

---

## Check Table Size

```sql
SELECT pg_size_pretty(
    pg_total_relation_size('<table_name>')
);
```

Shows the total size of a table (including indexes) in a readable format.

---

# Benefits of Indexes ✅

- Faster searches (`SELECT`)
- Faster filtering (`WHERE`)
- Faster joins (`JOIN`)
- Faster sorting (`ORDER BY`)
- Better performance on large datasets

---

# Costs of Indexes ⚠️

- Extra disk space
- Slower `INSERT`
- Slower `UPDATE` (when indexed columns change)
- Slower `DELETE`
- Larger backups and database transfers

---

# When Should You Add an Index?

✅ Good candidates:

- Frequently searched columns
- Frequently joined columns
- Read-heavy tables

⚠️ Avoid excessive indexes on:

- Write-heavy tables
- Columns that are rarely queried

---

## Best Practices

- Index columns commonly used in `WHERE` and `JOIN` clauses.
- Don't index every column.
- Keep the number of indexes reasonable.
- Use `EXPLAIN ANALYZE` to verify that an index is actually improving performance.
- Remove indexes that provide little benefit but add maintenance overhead.

---

## Cheat Sheet 📝

|Task|SQL|
|---|---|
|View indexes|`SELECT * FROM pg_indexes WHERE tablename='table';`|
|Analyze query|`EXPLAIN ANALYZE SELECT ...;`|
|Create index|`CREATE INDEX idx ON table(column);`|
|Create composite index|`CREATE INDEX idx ON table(col1, col2);`|
|Drop index|`DROP INDEX IF EXISTS idx;`|
|Check table size|`SELECT pg_size_pretty(pg_total_relation_size('table'));`|

---

## Scan vs Seek

### Sequential Scan

- Reads every row
- Used when no useful index exists
- Better when most rows are returned

### Index Seek (Index Scan)

- Uses index
- Faster for retrieving a small subset of rows

The PostgreSQL **query planner** chooses whichever is cheaper.

---

## Index Pros & Cons

### Advantages

- Faster searching
- Faster filtering
- Faster joins
- Faster sorting

### Disadvantages

- Extra storage
- Slower INSERT
- Slower UPDATE
- Slower DELETE

Indexes improve **read performance** at the cost of **write performance**.

---

# 1️⃣4️⃣ Database Normalization

## What is Normalization?

Normalization organizes data into well-structured tables to:

- Reduce redundancy
- Prevent anomalies
- Improve consistency
- Simplify maintenance

Goal:

> **Store each fact only once.**

---

## Problems with Poor Database Design

### Duplicate Data

Same information stored repeatedly.

---

### Update Anomaly

Updating one fact requires changing multiple rows.

---

### Insertion Anomaly

Cannot insert data because unrelated data is missing.

---

### Deletion Anomaly

Deleting one row accidentally removes important information.

---

### Search Problems

Repeated or multi-valued columns make queries difficult.

Example:

```
major1
major2
major3
```

instead of a separate table.

---

## Solution

Split large tables into related tables.

Example:

### Students

```
id
name
email
advisor_id
```

### Advisors

```
id
name
department
email
```

### Majors

```
id
major
credits_required
```

### Students_Majors

```
student_id
major_id
```

Represents a **many-to-many** relationship.

---

## Keys & Constraints

### Primary Key

```sql
PRIMARY KEY
```

- Unique
- NOT NULL
- Identifies each row

---

### Foreign Key

```sql
REFERENCES other_table(id)
```

Maintains referential integrity.

---

### Unique Constraint

```sql
UNIQUE(column)
```

Prevents duplicate values.

---

## Why Use IDs?

IDs:

- Never change
- Smaller and faster
- Better for relationships

Emails or names can change.

---

## Joins After Normalization

Since data is split across tables, use joins.

Example:

```sql
SELECT s.name, a.name
FROM students s
JOIN advisors a
ON s.advisor_id = a.id;
```

Trade-off:

- More joins
- Much better data integrity

---

# Academic Normal Forms

## 1NF (First Normal Form)

Requirements:

- Atomic values
- No repeating groups
- Unique rows

❌

```
Books = LOTR, Hobbit
```

✅

```
LOTR
Hobbit
```

---

## 2NF (Second Normal Form)

Requirements:

- Must satisfy 1NF
- No partial dependency

Every non-key attribute depends on the **entire** primary key.

---

## 3NF (Third Normal Form)

Requirements:

- Must satisfy 2NF
- No transitive dependency

Non-key attributes depend **only** on the primary key.

---

## Database Anomalies

### Update Anomaly

Repeated data becomes inconsistent.

### Insertion Anomaly

Cannot insert independent data.

### Deletion Anomaly

Deleting one row removes unrelated information.

---

# 🔑 SQL Commands Learned

```sql
-- View indexes
SELECT * FROM pg_indexes
WHERE tablename = 'table';

-- Analyze query
EXPLAIN ANALYZE
SELECT ...;

-- Create index
CREATE INDEX idx
ON table(column);

-- Composite index
CREATE INDEX idx
ON table(col1, col2);

-- Partial index
CREATE INDEX idx
ON table(column)
WHERE condition;

-- Ordered index
CREATE INDEX idx
ON table(column DESC);

-- Unique index
CREATE UNIQUE INDEX idx
ON table(column);

-- Expression index
CREATE INDEX idx
ON table(LOWER(column));

-- Cluster table
CLUSTER table
USING idx;

-- Drop index
DROP INDEX IF EXISTS idx;

-- Table size
SELECT pg_size_pretty(
    pg_total_relation_size('table')
);
```

---

# 1️⃣5️⃣PostgreSQL Database Maintenance

---

# 1. Why Database Maintenance?

Purpose:

- Keep queries fast
- Reduce wasted disk space
- Prevent table bloat
- Improve performance

```
UPDATE / DELETE
        ↓
Dead Tuples
        ↓
VACUUM
        ↓
Reusable Space
```

---

# 2. Measuring Table Size

### Table Data

```sql
SELECT pg_table_size('employees');
```

---

### Index Size

```sql
SELECT pg_indexes_size('employees');
```

---

### Total Size

```sql
SELECT pg_total_relation_size('employees');
```

---

### Human Readable

```sql
SELECT pg_size_pretty(
    pg_total_relation_size('employees')
);
```

---

# 3. Dead Tuples

Created by:

- UPDATE
- DELETE

Dead tuples:

- Not visible
- Occupy disk
- Cleaned by VACUUM

```
Old Row
   ↓
Dead Tuple
   ↓
VACUUM
   ↓
Reusable Space
```

---

# 4. VACUUM

```sql
VACUUM employees;
```

Purpose:

- Clean dead tuples
- Reuse storage
- Prevent bloat

Does NOT:

- Shrink table
- Return space to OS

---

# 5. ANALYZE

```sql
ANALYZE employees;
```

Updates:

- Row count
- Data distribution
- Query planner statistics

---

# 6. VACUUM ANALYZE

```sql
VACUUM ANALYZE employees;
```

Performs:

- VACUUM
- ANALYZE

Recommended after:

- Large INSERT
- Large UPDATE
- Large DELETE

---

# 7. VACUUM FULL

```sql
VACUUM FULL employees;
```

Rewrites table.

Advantages:

- Removes dead tuples
- Shrinks table
- Returns disk space

Disadvantages:

- Slow
- Blocks reads/writes

---

# 8. Autovacuum

Runs automatically.

```
Many UPDATEs
        ↓
Autovacuum
        ↓
VACUUM ANALYZE
```

---

# 9. pg_stat_all_tables

Useful columns:

- n_live_tup
- n_dead_tup
- last_vacuum
- last_autovacuum
- last_analyze

---

# 10. TRUNCATE

```sql
TRUNCATE employees;
```

Removes:

- All rows

Keeps:

- Table
- Columns
- Constraints

Advantages:

- Very fast
- No dead tuples
- Frees space immediately

---

# 11. VACUUM vs VACUUM FULL

|VACUUM|VACUUM FULL|
|---|---|
|Reuses space|Shrinks table|
|Doesn't block|Blocks table|
|Fast|Slow|
|Routine maintenance|Occasional maintenance|

---

# 12. DELETE vs TRUNCATE

|DELETE|TRUNCATE|
|---|---|
|WHERE supported|No WHERE|
|Creates dead tuples|No dead tuples|
|Slower|Faster|
|Needs VACUUM|No VACUUM needed|

---

# 30-Second Revision

```
UPDATE / DELETE
        ↓
Dead Tuples
        ↓
VACUUM
        ↓
Reusable Space

Need planner stats?
        ↓
ANALYZE

Need both?
        ↓
VACUUM ANALYZE

Need disk space back?
        ↓
VACUUM FULL

Remove all rows?
        ↓
TRUNCATE
```

### Memory Formula

```
UPDATE/DELETE
      ↓
Dead Tuples
      ↓
VACUUM
      ↓
ANALYZE
      ↓
Autovacuum
      ↓
VACUUM FULL (Rare)

Clear Entire Table
      ↓
TRUNCATE
```

## 1️⃣6️⃣ Connecting Database to Server

---

## 1. Overall Flow

### Definition

An **Express server** acts as the bridge between the client and the PostgreSQL database.

### Flow

```
Client
   │
   ▼
Express Server
   │
pool.query()
   │
   ▼
PostgreSQL
   │
   ▼
Response
```

---

## 2. Required Packages

### Definition

Two packages are required to connect Node.js with PostgreSQL.

### Installation

```bash
npm install pg dotenv
```

### Packages

|Package|Purpose|
|---|---|
|`pg`|Connects Node.js to PostgreSQL|
|`dotenv`|Loads environment variables from `.env`|

---

## 3. Store Credentials

### Definition

Store database credentials inside a **`.env`** file instead of hardcoding them.

### Example

```
DB_USER=postgres
DB_HOST=localhost
DB_NAME=api
DB_PASSWORD=******
DB_PORT=5432
```

> ⚠️ Never commit `.env` to GitHub.

---

## 4. Load Credentials

### Definition

Load environment variables into the application.

### Syntax

```jsx
dotenv.config();
```

Access values using:

```jsx
process.env.DB_USER
```

---

## 5. Create Connection Pool

### Definition

A **Pool** manages multiple database connections efficiently.

### Syntax

```jsx
const pool = new Pool({
    user: process.env.DB_USER,
    host: process.env.DB_HOST,
    database: process.env.DB_NAME,
    password: process.env.DB_PASSWORD,
    port: process.env.DB_PORT,
});
```

### Purpose

- Stores database configuration
- Reuses connections
- Improves performance

---

## 6. Run Queries

### Definition

Use `pool.query()` to execute SQL statements.

### Syntax

```jsx
await pool.query(sql, values);
```

### Example

```jsx
await pool.query(
    "SELECT * FROM users WHERE id = $1",
    [id]
);
```

---

## 7. Parameterized Queries

### Definition

Use placeholders (`$1`, `$2`, ...) instead of directly inserting user input.

### Syntax

```jsx
SELECT * FROM users
WHERE id = $1;
```

### Advantages

- Prevents SQL Injection
- Improves security
- Separates SQL from user input

---

## 8. Better Project Structure

### Definition

Keep database code in a separate folder for better organization.

### Structure

```
db/
 └── index.js
```

### Example

```jsx
export const query = (text, params) =>
    pool.query(text, params);
```

Use:

```jsx
db.query(...)
```

instead of

```jsx
pool.query(...)
```

---

# 1️⃣7️⃣ Deployment

---

## 1. Deployment

### Definition

**Deployment** is the process of making an application available online for users.

---

## 2. SDLC

### Definition

The **Software Development Life Cycle (SDLC)** describes the stages of software development.

### Flow

```
Plan
 ↓
Design
 ↓
Develop
 ↓
Test
 ↓
Deploy
 ↓
Maintain
```

---

## 3. Environments

### Definition

Applications are developed and tested in different environments before going live.

|Environment|Purpose|
|---|---|
|Local|Development on your computer|
|Staging|Testing before release|
|Production|Live application used by users|

### Flow

```
Local
   ↓
Staging
   ↓
Production
```

---

# 1️⃣8️⃣ Deploying with Render

---

## 1. Render

### Definition

**Render** is a **Platform as a Service (PaaS)** used to deploy backend applications and databases.

### Services

- Backend Hosting
- PostgreSQL Database
- Infrastructure Management

---

## 2. Deploy Flow

### Flow

```
Local
   │
git push
   │
GitHub
   │
Render
   │
Live App
```

---

## 3. Build & Start Commands

### Build

```bash
npm install
```

### Start

```bash
node app.js
```

---

## 4. Creating PostgreSQL Database

### Steps

1. Open Render Dashboard
2. Select **New**
3. Choose **PostgreSQL**
4. Create the database

Render provides:

- Host
- Username
- Password
- Database Name
- `DATABASE_URL`

---

## 5. Environment Variables

### Definition

Environment variables securely store configuration values.

### Example

```
DATABASE_URL=...
PORT=10000
```

Access using:

```jsx
process.env.DATABASE_URL
```

---

## 6. Auto Deploy

### Definition

Render automatically redeploys the application after every GitHub push.

### Flow

```
git push
    │
GitHub
    │
Render
    │
Automatic Deployment
```

---

## 7. Health Check Endpoint

### Definition

A health endpoint confirms that the server is running.

### Example

```jsx
app.get("/health", (req, res) => {
    res.sendStatus(200);
});
```

Returns:

```
200 OK
```

---

## 8. Monitoring

### Definition

Render provides monitoring tools for deployed applications.

|Tool|Purpose|
|---|---|
|Events|Deployment history|
|Metrics|Resource usage & bandwidth|
|Logs|Errors and debugging|

---

# 1️⃣9️⃣ Connecting Render Database

---

## 1. DATABASE_URL

### Definition

`DATABASE_URL` is a single connection string provided by Render to connect your application to the PostgreSQL database.

### Example

```
postgres://user:password@host:5432/database
```

---

## 2. process.env.DATABASE_URL

### Definition

Retrieve the connection string from environment variables.

### Example

```jsx
const pool = new Pool({
    connectionString: process.env.DATABASE_URL,
});
```

---

## 3. Express ↔ PostgreSQL Connection

### Flow

```
Express Route
      │
      ▼
pool.query()
      │
      ▼
PostgreSQL
      │
      ▼
Query Result
      │
      ▼
Express Response
```

---

## 4. Complete Request Flow

```
Write Code
    │
GitHub
    │
Render
    │
Environment Variables
    │
Express Server
    │
PostgreSQL
    │
Users
```

---

## Quick Revision

|Component|Purpose|
|---|---|
|`pg`|PostgreSQL driver|
|`dotenv`|Load `.env` variables|
|`.env`|Store secrets|
|`process.env`|Access environment variables|
|`Pool`|Manage database connections|
|`pool.query()`|Execute SQL queries|
|`DATABASE_URL`|Connect to Render PostgreSQL|
|`git push`|Trigger auto deployment|
|Health Check|Verify server status|
|Render|Host backend and database|

# 🧪 JavaScript Testing

---

# 1️⃣ Types of Testing

## Definition

**Testing** is the process of verifying that code behaves as expected before deploying it to users.

### Purpose

- Find bugs early
- Improve software reliability
- Ensure code works correctly
- Prevent future regressions

---

## Types of Testing

|Type|Tests|External Services|
|---|---|---|
|Unit Testing|Single function/module|Mocked|
|Integration Testing|Multiple units together|Mocked|
|End-to-End (E2E) Testing|Complete application|Real|

---

### Unit Testing

Tests the **smallest piece of code**, usually a single function.

Characteristics:

- Fast
- Independent
- External services are mocked

Example:

```jsx
function add(a, b) {
    return a + b;
}
```

Test:

```jsx
assert.strictEqual(add(2,3),5);
```

---

### Integration Testing

Tests how multiple modules work together.

Example:

```
Frontend
     │
     ▼
API
     │
     ▼
Database (Mock)
```

---

### End-to-End Testing

Tests the application exactly like a real user.

Example:

```
User
 ↓
Browser
 ↓
Server
 ↓
Database
```

Uses:

- Real Database
- Real APIs
- Real Browser

---

### Testing Pyramid

```
        E2E
      ▲
 Integration
      ▲
     Unit
```

- Unit tests → Most
- Integration → Fewer
- E2E → Fewest

---

# 2️⃣ Testing Methodologies

---

## Definition

A **testing methodology** is a strategy for writing and organizing tests.

---

## Why Testing Methodologies?

- Better code quality
- Fewer bugs
- Easier maintenance
- Better collaboration

---

## Common Methodologies

|Method|Focus|
|---|---|
|TDD|Code|
|BDD|User Behavior|
|ATDD|Acceptance Criteria|
|SBE|Specifications|

---

## TDD (Test-Driven Development)

Write tests **before** writing code.

Flow:

```
Write Test
     ↓
Fail
     ↓
Write Code
     ↓
Pass
     ↓
Refactor
```

Benefits:

- Cleaner code
- Better design
- High test coverage

---

## BDD (Behavior Driven Development)

Focuses on **user behavior**.

Example:

> A customer should be able to login.

Instead of:

> login() should return true.

---

## ATDD

Acceptance Test Driven Development.

Tests are written from business requirements.

---

## SBE

Specification By Example.

Requirements are written as real-world examples.

---

# 3️⃣ Mocha — Setup & Structure

---

## Definition

**Mocha** is a JavaScript testing framework used to organize and run tests.

---

## Installation

```bash
npm install mocha -D
```

---

## Run Tests

```bash
npm test
```

Single file:

```bash
mocha test/index_test.js
```

---

## Test Structure

```jsx
describe('Math', () => {

    describe('.max', () => {

        it('returns maximum value', () => {

        });

    });

});
```

---

## describe()

Groups related tests.

```jsx
describe("Math", () => {

});
```

---

## it()

Defines one test case.

```jsx
it("adds numbers", () => {

});
```

---

## Structure

```
describe
   │
   ├── it
   ├── it
   └── it
```

---

# 4️⃣ The Four Phases of a Test

---

## Definition

Every test should follow **four phases**.

---

## 1. Setup

Prepare data.

```jsx
const arr = [1,2,3];
```

---

## 2. Exercise

Run the function.

```jsx
arr.pop();
```

---

## 3. Verify

Check results.

```jsx
assert.strictEqual(arr.length,2);
```

---

## 4. Teardown

Clean up resources if necessary.

Example:

- Delete temporary file
- Reset database
- Close connection

---

## Complete Example

```jsx
it("removes last element", () => {

    // Setup
    const arr = [1,2,3];

    // Exercise
    arr.pop();

    // Verify
    assert.strictEqual(arr.length,2);

    // Teardown
    // Reset if needed

});
```

---

## Four Phases Flow

```
Setup
   │
   ▼
Exercise
   │
   ▼
Verify
   │
   ▼
Teardown
```

---

## Quick Revision

|Topic|Purpose|
|---|---|
|Unit Test|Test one function|
|Integration Test|Test modules together|
|E2E Test|Test complete application|
|TDD|Tests before code|
|BDD|Behavior-focused testing|
|Mocha|JavaScript testing framework|
|describe()|Group tests|
|it()|Single test|
|Setup|Prepare data|
|Exercise|Run code|
|Verify|Check result|
|Teardown|Clean up|

---

# 5️⃣ Hooks

---

## Definition

**Hooks** are Mocha functions that automatically run setup and teardown code before or after tests.

### Purpose

- Reduce duplicate code
- Share setup between tests
- Automatically clean up after tests

---

## Types of Hooks

|Hook|Runs|
|---|---|
|`before()`|Once before all tests|
|`after()`|Once after all tests|
|`beforeEach()`|Before every test|
|`afterEach()`|After every test|

---

## before()

Runs **once** before the first test.

```jsx
before(() => {
    // setup code
});
```

---

## after()

Runs **once** after the last test.

```jsx
after(() => {
    // cleanup code
});
```

---

## beforeEach()

Runs **before every test**.

```jsx
beforeEach(() => {
    value = 5;
});
```

---

## afterEach()

Runs **after every test**.

```jsx
afterEach(() => {
    // cleanup
});
```

---

## Example

```jsx
describe("Calculator", () => {

    let value;

    before(() => {
        console.log("Start");
    });

    beforeEach(() => {
        value = 10;
    });

    afterEach(() => {
        value = null;
    });

    after(() => {
        console.log("End");
    });

    it("adds", () => {
        value += 5;
        assert.strictEqual(value, 15);
    });

});
```

---

## Hook Execution Order

```
before()

      │
      ▼

beforeEach()

      │
      ▼

it()

      │
      ▼

afterEach()

      │
      ▼

after()
```

---

# 6️⃣ Assert Methods

---

## Definition

**Assert methods** compare the expected and actual values during testing.

If they don't match, the test fails.

---

## Import

Node.js

```jsx
const assert = require("assert");
```

Chai

```jsx
const { assert } = require("chai");
```

---

## Common Assert Methods

|Method|Purpose|
|---|---|
|`assert.ok()`|Checks truthy value|
|`assert.equal()`|Loose equality (`==`)|
|`assert.strictEqual()`|Strict equality (`===`)|
|`assert.deepStrictEqual()`|Compare objects/arrays|
|`assert.throws()`|Check thrown errors|

---

## assert.ok()

Checks if a value is truthy.

```jsx
assert.ok(true);
```

---

## assert.equal()

Uses **loose equality**.

```jsx
assert.equal(3, "3");
```

✅ Passes

---

## assert.strictEqual()

Uses **strict equality**.

```jsx
assert.strictEqual(3, 3);
```

```jsx
assert.strictEqual(3, "3");
```

❌ Fails

---

## assert.deepStrictEqual()

Used for objects and arrays.

```jsx
assert.deepStrictEqual(
    [1,2,3],
    [1,2,3]
);
```

---

## assert.throws()

Checks if a function throws an error.

```jsx
assert.throws(
    () => {
        fn(-1);
    },
    RangeError
);
```

---

## Comparison

|Method|Uses|
|---|---|
|`ok()`|Truthy|
|`equal()`|`==`|
|`strictEqual()`|`===`|
|`deepStrictEqual()`|Objects & Arrays|
|`throws()`|Error checking|

---

# 7️⃣ TDD — Red, Green, Refactor Cycle

---

## Definition

**Test-Driven Development (TDD)** is a software development approach where tests are written **before** the actual code.

---

## Cycle

```
Write Test
    │
    ▼

RED
(Test Fails)

    │
    ▼

GREEN
(Write Minimum Code)

    │
    ▼

REFACTOR
(Clean Code)

    │
    ▼

Repeat
```

---

## 1. Red

Write a test.

Run it.

The test **must fail**.

---

## 2. Green

Write the **minimum amount of code** needed to pass the test.

Don't add unnecessary features.

---

## 3. Refactor

Improve code quality without changing functionality.

Examples:

- Better variable names
- Remove duplicate code
- Improve readability

---

## Example

Test:

```jsx
assert.strictEqual(
    Phrase.initials("Nelson Mandela"),
    "NM"
);
```

Minimum implementation:

```jsx
const Phrase = {
    initials() {
        return "NM";
    }
};
```

Later refactor:

```jsx
initials(name) {
    return name
        .split(" ")
        .map(word => word[0])
        .join("");
}
```

---

## Benefits

- Better code quality
- Better design
- High test coverage
- Easier maintenance

---

# 8️⃣ Edge Cases

---

## Definition

An **edge case** is an unusual or extreme input that may cause unexpected behavior.

---

## Common Edge Cases

- Empty string
- Empty array
- Negative number
- `null`
- `undefined`
- Wrong data type

---

## Example

```jsx
Phrase.initials(14);
```

Should throw an error because the input isn't a string.

---

## Test

```jsx
it("throws if input is not a string", () => {

    const exercise = () => {
        Phrase.initials(14);
    };

    assert.throws(
        exercise,
        /only use string/
    );

});
```

---

## Implementation

```jsx
initials(name){

    if(typeof name !== "string"){
        throw new Error(
            "only use string"
        );
    }

}
```

---

## Why Test Edge Cases?

- Prevent crashes
- Improve reliability
- Handle invalid inputs safely

---

## Edge Case Examples

|Input|Expected Result|
|---|---|
|`""`|Handle empty string|
|`[]`|Handle empty array|
|`null`|Throw error|
|`undefined`|Throw error|
|`-5`|Validate if allowed|
|Wrong data type|Throw error|

---

## Quick Revision

|Topic|Purpose|
|---|---|
|`before()`|Runs once before all tests|
|`after()`|Runs once after all tests|
|`beforeEach()`|Runs before every test|
|`afterEach()`|Runs after every test|
|`assert.ok()`|Truthy check|
|`assert.equal()`|Loose equality|
|`assert.strictEqual()`|Strict equality|
|`assert.deepStrictEqual()`|Compare objects/arrays|
|`assert.throws()`|Verify thrown errors|
|Red|Write failing test|
|Green|Write minimum code|
|Refactor|Improve code|
|Edge Case|Test unusual inputs|

---

# 9️⃣ Server Testing Stack

---

## Definition

**Server testing** verifies backend APIs, routes, and responses without using a browser.

### Purpose

- Test API endpoints
- Verify HTTP status codes
- Validate request/response handling
- Test error scenarios

---

## Common Tools

|Tool|Purpose|
|---|---|
|Chai|Assertions|
|Supertest|HTTP requests to Express server|
|jsdom|Parse HTML responses|
|async/await|Handle asynchronous tests|

---

## Installation

```bash
npm install chai supertest
```

---

## Supertest

### Definition

**Supertest** sends HTTP requests directly to an Express application.

### Example

```jsx
const request = require("supertest");
```

---

### GET Request

```jsx
const response = await request(app)
    .get("/")
    .send();
```

---

### POST Request

```jsx
await request(app)
    .post("/messages")
    .type("form")
    .send({
        author,
        message
    });
```

---

## HTTP Status Codes

|Code|Meaning|
|---|---|
|`200`|OK|
|`201`|Created|
|`400`|Bad Request|
|`401`|Unauthorized|
|`404`|Not Found|
|`500`|Internal Server Error|

---

## Testing Status Code

```jsx
it("returns 200", async () => {

    const response =
        await request(app)
        .get("/")
        .send();

    assert.strictEqual(
        response.status,
        200
    );

});
```

---

## Happy Path vs Sad Path

### Happy Path

Expected valid input.

```jsx
assert.strictEqual(
    response.status,
    200
);
```

---

### Sad Path

Invalid or unexpected input.

```jsx
assert.strictEqual(
    response.status,
    400
);
```

---

## parseTextFromHTML()

Extracts text from an HTML response.

```jsx
parseTextFromHTML(
    response.text,
    "#page-title"
);
```

---

## Server Testing Flow

```
Client

   │
   ▼

Express

   │
   ▼

Supertest

   │
   ▼

Assert Response
```

---

# 🔟 Code Coverage & Test Coverage

---

## 1. Code Coverage

### Definition

Measures the percentage of source code executed while running tests.

---

## 2. Test Coverage

### Definition

Measures how many application requirements are tested.

---

## Code Coverage Criteria

|Coverage|Purpose|
|---|---|
|Function Coverage|Every function executed|
|Statement Coverage|Every statement executed|
|Path Coverage|Every branch tested|
|Condition Coverage|Every Boolean condition tested|

---

## Example

```jsx
function sum(x, y){

    if(x && y){
        return x + y;
    }

    return null;

}
```

Tests:

```jsx
sum(1,2);

sum(1,false);

sum(false,2);

sum();
```

---

## Does 100% Coverage Mean Bug-Free?

❌ No.

Example:

```jsx
sum("1","2");
```

Returns:

```
"12"
```

instead of

```
3
```

Coverage is high, but a bug still exists.

---

## Coverage Summary

|Type|Meaning|
|---|---|
|Code Coverage|% of code executed|
|Test Coverage|% of requirements tested|

---

# 1️⃣1️⃣ Mocking

---

## Definition

**Mocking** creates a fake version of an external dependency for testing.

### Purpose

- Isolate code
- Remove external dependencies
- Make tests faster

---

## Unit Testing

Everything external is mocked.

```
Database

↓

Mock
```

---

## Integration Testing

Only external services are mocked.

Internal modules communicate normally.

---

## Comparison

|Test|External Services|Internal Modules|
|---|---|---|
|Unit Test|Mocked|Mocked|
|Integration Test|Mocked|Real|

---

## Advantages

- Faster tests
- Independent tests
- Reliable results

---

# 1️⃣2️⃣ Spies (Sinon.js)

---

## Definition

A **Spy** records information about function calls without changing the function.

---

## Installation

```bash
npm install sinon
```

---

## Create Spy

```jsx
sinon.spy(robot, "greet");
```

---

## Information Recorded

- Arguments
- Return value
- Number of calls
- Exceptions

---

## Useful Methods

|Method|Purpose|
|---|---|
|`.called`|Was function called?|
|`.calledWith()`|Called with arguments?|
|`.returned()`|Returned expected value?|
|`.restore()`|Remove spy|

---

## Example

```jsx
sinon.spy(robot,"greet");

robot.greet("Codey");

expect(
robot.greet.called
).to.be.true;

expect(
robot.greet.calledWith("Codey")
).to.be.true;

robot.greet.restore();
```

---

## Spy Flow

```
Function

   │
   ▼

Spy Records

   │
   ▼

Assertions
```

---

# 1️⃣3️⃣ Web Security Fundamentals

---

## Definition

**Web Security** protects applications, users, and data from attacks.

---

## CIA Triad

|Principle|Meaning|
|---|---|
|🔒 Confidentiality|Only authorized users access data|
|✅ Integrity|Data remains accurate|
|🌐 Availability|Services remain available|

---

## OWASP Top Risks

|Risk|Description|
|---|---|
|SQL Injection|Malicious SQL execution|
|Broken Authentication|Weak login/session security|
|Sensitive Data Exposure|Unprotected sensitive data|
|XXE|XML parser attack|
|Broken Access Control|Unauthorized access|
|Security Misconfiguration|Unsafe server settings|
|XSS|Malicious JavaScript|
|Insecure Deserialization|Malicious objects|
|Known Vulnerabilities|Outdated software|
|Poor Logging & Monitoring|Delayed attack detection|

---

## Security Best Practices

- Validate user input
- Sanitize data
- Use parameterized queries
- Encrypt sensitive data
- Use authentication & authorization
- Keep software updated
- Configure servers securely
- Monitor logs
- Perform regular security testing

---

## Security Flow

```
User Input

     │
     ▼

Validate

     │
     ▼

Sanitize

     │
     ▼

Parameterized Query

     │
     ▼

Database
```

---

# ⭐ JavaScript Testing Cheat Sheet

|Topic|Key Point|
|---|---|
|Server Testing|Test backend APIs|
|Supertest|Send HTTP requests|
|Chai|Assertions|
|HTTP 200|Success|
|HTTP 404|Not Found|
|Code Coverage|% code executed|
|Test Coverage|% requirements tested|
|Mocking|Fake external services|
|Spy|Observe function calls|
|Sinon.js|Spy/Stub library|
|CIA|Confidentiality, Integrity, Availability|
|OWASP|Top web security risks|