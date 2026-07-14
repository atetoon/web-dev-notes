# Multiple Tables & Joins

## Why Multiple Tables?

Instead of storing everything in one table, data is divided into related tables to reduce redundancy, improve integrity, follow normalization, and make updates easier. Related tables are connected using **keys**.

## JOIN

A **JOIN** combines data from two or more tables based on a related column.

```sql
SELECT columns
FROM table1
JOIN table2
ON table1.column = table2.column;
```

## INNER JOIN

Returns **only matching rows** from both tables.

```sql
SELECT *
FROM customers
INNER JOIN orders
ON customers.customer_id = orders.customer_id;
```

Use case: Retrieve customers who have placed orders.

## LEFT JOIN

Returns all rows from the left table + matching rows from the right table (`NULL` if no match).

```sql
SELECT *
FROM customers
LEFT JOIN orders
ON customers.customer_id = orders.customer_id;
```

Use case: Find customers who haven't placed any orders.

## RIGHT JOIN

Returns all rows from the right table + matching rows from the left table.

```sql
SELECT *
FROM customers
RIGHT JOIN orders
ON customers.customer_id = orders.customer_id;
```

## FULL OUTER JOIN

Returns matching + non-matching rows from both tables.

```sql
SELECT *
FROM customers
FULL OUTER JOIN orders
ON customers.customer_id = orders.customer_id;
```

## CROSS JOIN

Returns every possible combination of rows (3 customers × 2 products = 6 rows).

```sql
SELECT * FROM customers CROSS JOIN products;
```

## SELF JOIN

A table joined with itself. Useful when rows are related within the same table.

```sql
SELECT
  e.name,
  m.name AS manager
FROM employees e
JOIN employees m
ON e.manager_id = m.employee_id;
```

## UNION

Combines results of multiple queries. Duplicate rows removed.

```sql
SELECT city FROM customers
UNION
SELECT city FROM suppliers;
```

Rules: same number of columns, compatible data types.

## UNION ALL

Same as `UNION` but keeps duplicate rows.

```sql
SELECT city FROM customers
UNION ALL
SELECT city FROM suppliers;
```

## JOIN vs UNION

| JOIN | UNION |
| --- | --- |
| Combines columns | Combines rows |
| Works on related tables | Works on query results |
| Uses `ON` condition | No `ON` condition |

## Common JOIN Types

| JOIN | Returns |
| --- | --- |
| INNER JOIN | Matching rows only |
| LEFT JOIN | All left + matching right |
| RIGHT JOIN | All right + matching left |
| FULL OUTER JOIN | All rows from both tables |
| CROSS JOIN | Every possible combination |
| SELF JOIN | Table joined with itself |

## Query Execution Flow

```
FROM → JOIN → ON → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT
```

---
## Related
- [[01 - SQL Basics]]
- [[04 - Schema & Keys]]
