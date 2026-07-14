# Database Normalization

## What is Normalization?

Organizing data into multiple related tables to reduce redundancy, eliminate anomalies, improve integrity, and make maintenance easier.

## Data Redundancy

Unnecessary repetition of the same data.

| Student | Course | Instructor |
| --- | --- | --- |
| Alice | DBMS | John |
| Bob | DBMS | John |
| Charlie | DBMS | John |

## Data Anomalies

| Anomaly | Description |
| --- | --- |
| Update Anomaly | Same info must be updated in multiple rows |
| Insertion Anomaly | Can't insert data without inserting unrelated data |
| Deletion Anomaly | Deleting one record accidentally removes useful info |

## First Normal Form (1NF)

- Each column contains a single (atomic) value
- No repeating groups
- Each row is unique

```
Before: Alice | DBMS, OS
After:  Alice | DBMS
        Alice | OS
```

## Second Normal Form (2NF)

- Already in 1NF
- No **partial dependency** (non-key attribute depends on only part of a composite key)

Solution: move partially dependent columns into a separate table.

## Third Normal Form (3NF)

- Already in 2NF
- No **transitive dependency** (non-key attribute depends on another non-key attribute)

Solution: store dependent data in a separate table.

## Before vs After Normalization

```
Before:
Students (student_id, student_name, course_name, instructor_name, department)

After:
Students (student_id, student_name)
Courses (course_id, course_name)
Instructors (instructor_id, instructor_name)
Enrollments (student_id, course_id)
```

## Junction Table

Resolves Many-to-Many relationships.

| student_id | course_id |
| --- | --- |
| 1 | DBMS |
| 1 | OS |
| 2 | DBMS |

## Denormalization

Intentionally adding redundancy to improve read performance.

| Advantages | Disadvantages |
| --- | --- |
| Faster read queries | More redundancy |
| Fewer JOINs | Higher storage usage |
| Better reporting performance | Harder to maintain consistency |

Use cases: Reporting systems, data warehouses, read-heavy applications.

> Normalize first. Denormalize only when performance becomes a bottleneck.

## Normalization Process

```
Unnormalized Data
↓
1NF (Remove repeating groups)
↓
2NF (Remove partial dependency)
↓
3NF (Remove transitive dependency)
```

## 1NF vs 2NF vs 3NF

| Normal Form | Removes |
| --- | --- |
| 1NF | Repeating groups / Non-atomic values |
| 2NF | Partial dependency |
| 3NF | Transitive dependency |

---
## Related
- [[04 - Schema & Keys]]
