# SQL Basics

## Database

A **database** is an organized collection of related data that allows efficient storage, retrieval, modification, and deletion.

### Purpose

- Store data permanently
- Retrieve data efficiently
- Reduce data redundancy
- Manage large amounts of data

### Examples

- Student Management System
- Banking System
- E-commerce Website
- Social Media Platform

## Relational Database

Stores data in **tables** consisting of rows and columns.

```
Database
     │
     ▼
 Tables
 ┌─────────┐
 │ Rows    │ → Records
 │ Columns │ → Attributes
 └─────────┘
```

Examples: PostgreSQL, MySQL, SQLite, Oracle, SQL Server

## RDBMS

Software used to create, manage, and interact with relational databases.

Responsibilities: Store data, Execute SQL queries, Manage users/permissions, Enforce constraints, Handle transactions, Maintain data integrity.

## SQL

**SQL (Structured Query Language)** is the standard language used to communicate with an RDBMS.

```sql
SELECT
INSERT
UPDATE
DELETE
CREATE
ALTER
DROP
```

| Category | Purpose |
| --- | --- |
| DDL | Define database objects |
| DML | Manipulate data |
| DQL | Retrieve data |
| DCL | Control permissions |
| TCL | Manage transactions |

## SQL vs PostgreSQL

| SQL | PostgreSQL |
| --- | --- |
| Query language | RDBMS |
| Standard language | Software implementing SQL |
| Used to write queries | Executes SQL queries |

## Terminology

| Term | Meaning |
| --- | --- |
| Database | Collection of related data |
| Table | Collection of related records |
| Row (Tuple) | One record |
| Column (Attribute) | Property of a record |
| Schema | Database structure |
| Query | SQL command sent to the database |

---

## CRUD Operations

| Operation | SQL Command | Purpose |
| --- | --- | --- |
| Create | `INSERT` | Add new records |
| Read | `SELECT` | Retrieve records |
| Update | `UPDATE` | Modify existing records |
| Delete | `DELETE` | Remove records |

## SELECT

```sql
SELECT column1, column2
FROM table_name;

SELECT * FROM table_name;

SELECT name, age FROM users;
```

## DISTINCT

Returns only unique values by removing duplicates.

```sql
SELECT DISTINCT department
FROM employees;
```

## INSERT

```sql
INSERT INTO users (name, age)
VALUES ('Dhruv', 19);

-- Multiple rows
INSERT INTO users (name, age)
VALUES
('Dhruv', 19),
('Rahul', 20);
```

## UPDATE

```sql
UPDATE users
SET age = 20
WHERE name = 'Dhruv';
```

> ⚠️ Omitting `WHERE` updates **every row**.

## DELETE

```sql
DELETE FROM users
WHERE age < 18;
```

> ⚠️ Omitting `WHERE` deletes **all rows**.

## WHERE

| Operator | Meaning |
| --- | --- |
| `=` | Equal |
| `!=` / `<>` | Not Equal |
| `>` | Greater Than |
| `<` | Less Than |
| `>=` | Greater Than or Equal |
| `<=` | Less Than or Equal |

```sql
SELECT * FROM users WHERE age >= 18;
```

## Logical Operators

```sql
-- AND: all conditions must be true
SELECT * FROM users WHERE age >= 18 AND city = 'Delhi';

-- OR: at least one condition true
SELECT * FROM users WHERE city = 'Delhi' OR city = 'Mumbai';

-- NOT: negates a condition
SELECT * FROM users WHERE NOT city = 'Delhi';
```

## LIKE

| Wildcard | Meaning |
| --- | --- |
| `%` | Zero or more characters |
| `_` | Exactly one character |

```sql
WHERE name LIKE 'D%';     -- starts with
WHERE name LIKE '%v';     -- ends with
WHERE name LIKE '%ru%';   -- contains
WHERE name LIKE '_ohn';   -- single character
```

## BETWEEN

```sql
SELECT * FROM products
WHERE price BETWEEN 100 AND 500;
```

## IN

```sql
SELECT * FROM users
WHERE city IN ('Delhi', 'Mumbai');
```

## IS NULL

```sql
SELECT * FROM users WHERE phone IS NULL;
SELECT * FROM users WHERE phone IS NOT NULL;
```

## AS (Alias)

```sql
SELECT name AS student_name
FROM students;
```

## LIMIT

```sql
SELECT * FROM users LIMIT 5;
```

## ORDER BY

```sql
SELECT * FROM users ORDER BY age ASC;
SELECT * FROM users ORDER BY age DESC;
```

> `ASC` is the default order.

## Execution Order

```
FROM → WHERE → SELECT → ORDER BY → LIMIT
```

---
## Related
- [[02 - Aggregate Functions]]
- [[03 - Joins]]
