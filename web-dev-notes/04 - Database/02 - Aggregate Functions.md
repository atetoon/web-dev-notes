# Aggregate Functions

Aggregate functions perform calculations on **multiple rows** and return a **single value**. Used for data analysis, reports, statistics, summarizing data.

## COUNT()

```sql
SELECT COUNT(*) FROM table_name;
SELECT COUNT(column_name) FROM table_name;  -- non-NULL only

SELECT COUNT(*) FROM employees;
```

## SUM()

```sql
SELECT SUM(salary) FROM employees;
```

## AVG()

```sql
SELECT AVG(salary) FROM employees;
```

## MIN()

```sql
SELECT MIN(price) FROM products;
```

## MAX()

```sql
SELECT MAX(price) FROM products;
```

## ROUND()

```sql
SELECT ROUND(AVG(salary), 2) FROM employees;
```

## GROUP BY

Groups rows having the same values into a single group. Used with aggregate functions.

```
Employees → Department → HR / IT / Sales → Aggregate Function
```

```sql
SELECT department, COUNT(*)
FROM employees
GROUP BY department;
```

## HAVING

Filters **groups** after `GROUP BY`.

> `WHERE` filters rows, `HAVING` filters groups.

```sql
SELECT department, AVG(salary)
FROM employees
GROUP BY department
HAVING AVG(salary) > 50000;
```

## WHERE vs HAVING

| WHERE | HAVING |
| --- | --- |
| Filters rows | Filters groups |
| Before `GROUP BY` | After `GROUP BY` |
| Cannot use aggregate functions | Can use aggregate functions |

## Execution Order

```
FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT
```

## Combining Aggregate Functions

```sql
SELECT
  COUNT(*) AS total_employees,
  AVG(salary) AS avg_salary,
  MIN(salary) AS lowest_salary,
  MAX(salary) AS highest_salary
FROM employees;
```

---
## Related
- [[01 - SQL Basics]]
- [[03 - Joins]]
