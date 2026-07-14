# PostgreSQL Constraints & Triggers

## What are Constraints?

Rules applied to table columns to ensure data accuracy and integrity — prevent invalid or inconsistent data.

## NOT NULL

```sql
CREATE TABLE students (
    id INT,
    name VARCHAR(100) NOT NULL
);
```

## UNIQUE

```sql
CREATE TABLE users (
    email VARCHAR(100) UNIQUE
);
```

## PRIMARY KEY

```sql
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100)
);
```

## CHECK

```sql
CREATE TABLE students (
    age INT CHECK (age >= 18)
);
```

## FOREIGN KEY

```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    student_id INT,
    FOREIGN KEY (student_id) REFERENCES students(student_id)
);
```

## Referential Integrity

Ensures every Foreign Key references a valid Primary Key.

## ON DELETE CASCADE

Automatically deletes child rows when the parent row is deleted.

```sql
FOREIGN KEY (student_id)
REFERENCES students(student_id)
ON DELETE CASCADE;
```

## ALTER TABLE for Constraints

```sql
-- Add constraint
ALTER TABLE users ADD CONSTRAINT unique_email UNIQUE(email);

-- Set NOT NULL
ALTER TABLE users ALTER COLUMN email SET NOT NULL;

-- Drop NOT NULL
ALTER TABLE users ALTER COLUMN email DROP NOT NULL;

-- Drop constraint
ALTER TABLE users DROP CONSTRAINT unique_email;
```

> Before adding constraints, existing invalid data must be corrected (backfilled), or PostgreSQL will reject the constraint.

## PRIMARY KEY vs UNIQUE

| PRIMARY KEY | UNIQUE |
| --- | --- |
| One per table | Multiple allowed |
| Cannot be `NULL` | Allows `NULL` values |
| Identifies each row | Prevents duplicate values |

## Constraint Hierarchy

```
Data Types → NOT NULL → UNIQUE → PRIMARY KEY → FOREIGN KEY → Referential Integrity
```

---

## PostgreSQL Triggers

A **Trigger** automatically executes a function when a specified event occurs on a table.

```
INSERT / UPDATE / DELETE / TRUNCATE → Trigger Fires → Trigger Function Executes
```

## Why Use Triggers?

Automate repetitive tasks, maintain audit logs, enforce business rules, validate data, synchronize related tables.

## Trigger Syntax

```sql
CREATE TRIGGER trigger_name
AFTER INSERT
ON employees
FOR EACH ROW
EXECUTE FUNCTION function_name();
```

## BEFORE vs AFTER

| BEFORE Trigger | AFTER Trigger |
| --- | --- |
| Runs before the event | Runs after the event completes |
| Validation, modifying data | Audit logging, notifications |

## FOR EACH ROW vs FOR EACH STATEMENT

| FOR EACH ROW | FOR EACH STATEMENT |
| --- | --- |
| Once per affected row | Once per SQL statement |
| 100 rows updated → runs 100 times | 100 rows updated → runs 1 time |

## WHEN Clause

```sql
CREATE TRIGGER salary_check
BEFORE UPDATE
ON employees
FOR EACH ROW
WHEN (NEW.salary > 100000)
EXECUTE FUNCTION check_salary();
```

## Trigger Order

Multiple triggers on the same event run in **alphabetical order of trigger names**.

## DROP TRIGGER

```sql
DROP TRIGGER trigger_name ON table_name;
```

## Viewing Triggers

```sql
SELECT * FROM information_schema.triggers;
```

## Trigger Flow

```
Database Event → BEFORE Trigger → Database Operation → AFTER Trigger
```

## Common Use Cases

- Audit logs
- Automatic timestamps
- Data validation
- Business rule enforcement
- Synchronizing related tables

---
## Related
- [[04 - Schema & Keys]]
- [[07 - PostgreSQL]]
