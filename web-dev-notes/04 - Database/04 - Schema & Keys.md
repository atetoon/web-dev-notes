# Database Schema & Keys

## What is a Schema?

A **schema** is the logical blueprint of a database — defines tables, columns, data types, relationships, constraints.

## Table / Column / Row

| Concept | Meaning |
| --- | --- |
| Table | Stores related data in rows and columns |
| Column | A specific property of a record (attribute) |
| Row (Tuple) | One complete record |

## Data Types

| Data Type | Stores |
| --- | --- |
| `INTEGER` | Whole numbers |
| `DECIMAL` | Decimal numbers |
| `VARCHAR(n)` | Variable-length text |
| `TEXT` | Large text |
| `BOOLEAN` | `TRUE` / `FALSE` |
| `DATE` | Date |
| `TIMESTAMP` | Date and time |

## CREATE TABLE

```sql
CREATE TABLE students (
    student_id INTEGER,
    name VARCHAR(100),
    age INTEGER
);
```

## ALTER TABLE

```sql
ALTER TABLE students ADD email VARCHAR(100);          -- add column
ALTER TABLE students DROP COLUMN email;                -- drop column
ALTER TABLE students RENAME COLUMN age TO student_age; -- rename column
```

## DROP TABLE

```sql
DROP TABLE students;
```

> ⚠️ Removes both structure and all data.

## Schema Design Flow

```
Requirements → Entities → Tables → Columns → Data Types → Relationships
```

---

## Database Keys

Keys uniquely identify records and establish relationships between tables.

## Primary Key (PK)

Uniquely identifies each row. Unique, cannot be `NULL`, one per table.

```sql
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100)
);
```

## Foreign Key (FK)

Links one table to another by referencing the Primary Key of another table.

```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    student_id INT,
    FOREIGN KEY (student_id) REFERENCES students(student_id)
);
```

## Composite Key

Made up of two or more columns — used when a single column can't uniquely identify a row.

```sql
PRIMARY KEY (student_id, course_id)
```

## Candidate Key

Any column (or combination) that can uniquely identify a row. One is chosen as Primary Key.

## Alternate Key

A candidate key that is **not selected** as the Primary Key.

## Surrogate Key

System-generated key with no business meaning (Auto Increment, Serial ID, UUID).

```sql
student_id SERIAL PRIMARY KEY
```

## Natural Key

A key that already exists in real-world data (Email, Aadhaar Number, Passport Number).

## Primary Key vs Foreign Key

| Primary Key | Foreign Key |
| --- | --- |
| Uniquely identifies a row | References another table |
| Unique | Can contain duplicates |
| Cannot be `NULL` | Can be `NULL` (unless restricted) |
| One per table | Multiple allowed |

## Primary Key vs Unique

| PRIMARY KEY | UNIQUE |
| --- | --- |
| Only one per table | Multiple allowed |
| Cannot be `NULL` | Can contain `NULL` (PostgreSQL allows multiple `NULL`s) |
| Uniquely identifies rows | Prevents duplicate values |

---

## Database Relationships

A **relationship** connects tables using Primary Keys and Foreign Keys.

## One-to-One (1:1)

Each record in one table relates to **exactly one** record in another.

Use cases: Person ↔ Passport, User ↔ Profile

## One-to-Many (1:N)

One record can have **multiple related records** in another table. Most common relationship.

Use cases: Customer → Orders, Department → Employees

## Many-to-Many (M:N)

Many records relate to many records — requires a **Junction Table**.

Use cases: Students ↔ Courses, Movies ↔ Actors

## Junction Table

Resolves M:N relationships by containing FKs of both tables.

```
| student_id | course_id |
| 1          | C101      |
| 1          | C102      |
| 2          | C101      |
```

## Cardinality

| Relationship | Cardinality |
| --- | --- |
| One-to-One | 1 : 1 |
| One-to-Many | 1 : N |
| Many-to-Many | M : N |

---

## Designing Relational Databases

## Entity / Attribute / Relationship

| Concept | Becomes |
| --- | --- |
| Entity | Table |
| Attribute | Column |
| Relationship | Foreign Key |

## ER Diagram

Visually represents entities, attributes, relationships, and cardinality.

## Crow's Foot Notation

```
|──|      One
|──<      Many
```

```
Customer |──< Order
Student |──< Enrollment >──| Course
```

## Three-Tier Architecture

```
Presentation Layer (UI)
        ↓
Application Layer (Business Logic)
        ↓
Database Layer (Storage)
```

| Layer | Examples |
| --- | --- |
| Presentation | React, Angular, HTML/CSS |
| Application | Node.js, Express.js, Django |
| Database | PostgreSQL |

## Database Design Workflow

```
Requirements → Identify Entities → Identify Attributes →
Choose Primary Keys → Define Relationships → Create ER Diagram → Implement
```

---
## Related
- [[03 - Joins]]
- [[06 - Normalization]]
- [[05 - Constraints & Triggers]]
