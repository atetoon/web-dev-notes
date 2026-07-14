# PostgreSQL — Roles, Security, ACID, Injection, Indexes, Maintenance & Deployment

## Roles & Security

### What is a Role?

An identity used to manage authentication and permissions. Can own objects, log in, grant permissions, inherit from other roles.

### Login Role vs Group Role

```sql
CREATE ROLE dhruv LOGIN PASSWORD 'password';  -- can log in
```

Group roles can't log in — used to group permissions for multiple users.

### Role Attributes

```sql
CREATE ROLE admin LOGIN CREATEDB CREATEROLE;
```

| Attribute | Purpose |
| --- | --- |
| `LOGIN` | Allows login |
| `SUPERUSER` | Full database privileges |
| `CREATEDB` | Can create databases |
| `CREATEROLE` | Can create/manage roles |

### GRANT / REVOKE

```sql
GRANT SELECT ON students TO dhruv;
GRANT SELECT, INSERT, UPDATE ON students TO dhruv;

REVOKE INSERT ON students FROM dhruv;
```

### ALTER DEFAULT PRIVILEGES

Permissions automatically applied to future objects.

```sql
ALTER DEFAULT PRIVILEGES
GRANT SELECT ON TABLES TO developer;
```

### Column-Level Security

```sql
GRANT SELECT (name) ON students TO dhruv;
```

Useful for hiding sensitive columns (salary, password, email).

### Row-Level Security (RLS)

```sql
CREATE POLICY student_policy
ON students
FOR SELECT
USING (student_id = current_user_id);
```

### Viewing Roles & Privileges

```sql
SELECT * FROM pg_roles;
SELECT * FROM information_schema.table_privileges;
SELECT * FROM information_schema.column_privileges;
```

---

## ACID Properties

**ACID** ensures database transactions are reliable, consistent, and safe.

### Transaction

```sql
BEGIN;
UPDATE accounts SET balance = balance - 500 WHERE id = 1;
UPDATE accounts SET balance = balance + 500 WHERE id = 2;
COMMIT;
```

### The Four Properties

| Property | Meaning |
| --- | --- |
| Atomicity | All operations succeed, or none do |
| Consistency | Transaction leaves DB in a valid state (constraints preserved) |
| Isolation | Transactions don't interfere with each other |
| Durability | Once committed, changes are permanent — survive crashes |

### COMMIT / ROLLBACK

```sql
COMMIT;    -- save changes permanently
ROLLBACK;  -- cancel transaction, restore previous state
```

### Real-World Example — Bank Transfer

```
A → ₹500 → B
```

If the second update fails → `ROLLBACK` → no money is deducted. Without Atomicity, money could disappear.

---

## SQL Injection

### What is SQL Injection?

A vulnerability where an attacker inserts malicious SQL through user input to manipulate queries.

```sql
-- ❌ Unsafe
SELECT * FROM users
WHERE username = '$username'
AND password = '$password';
```

### Types

| Type | Purpose |
| --- | --- |
| Union-Based | Retrieve additional data using `UNION` |
| Error-Based | Reveal DB info via error messages |
| Boolean-Based | Infer info using TRUE/FALSE conditions (`' OR 1=1 --`) |
| Time-Based | Infer info using response delays |
| Out-of-Band | Retrieve data through external channels (DNS, HTTP) |

### Preventing SQL Injection

**Prepared Statements (Parameterized Queries)** — safest method.

```sql
SELECT * FROM users
WHERE username = ?
AND password = ?;
```

Other defenses: input validation, least privilege (limit permissions granted to app users).

### Secure Flow

```
User Input → Prepared Statement → Safe Query → Database
```

---

## PostgreSQL Indexes

### What is an Index?

A data structure that speeds up data retrieval by avoiding full table scans.

### Trade-off

| Advantages | Disadvantages |
| --- | --- |
| Faster queries | Extra storage |
| Faster searching | Slower INSERT |
| Faster filtering | Slower UPDATE |
| Faster sorting | Slower DELETE |

### Creating & Viewing

```sql
CREATE INDEX idx_email ON users(email);
SELECT * FROM pg_indexes;
```

### Query Analysis

```sql
EXPLAIN ANALYZE
SELECT * FROM users WHERE email = 'abc@gmail.com';
```

### Scan Types

| Scan | Description |
| --- | --- |
| Sequential Scan | Scans every row — best for small tables |
| Index Scan | Uses index to find matching rows |
| Bitmap Index Scan | Batches matches for many-row results |
| Index Only Scan | Reads directly from index — fastest |

### Index Types

```sql
CREATE INDEX idx_name ON users(name);                       -- single-column
CREATE INDEX idx_name_email ON users(name, email);           -- composite
CREATE UNIQUE INDEX idx_email ON users(email);                -- unique
CREATE INDEX idx_active_users ON users(email) WHERE active = TRUE; -- partial
CREATE INDEX idx_lower_email ON users(LOWER(email));           -- expression
```

### Index Seek vs Sequential Scan

| Scan | Time Complexity |
| --- | --- |
| Sequential Scan | O(n) |
| Index Seek | O(log n) |

### Measuring Size

```sql
SELECT pg_size_pretty(pg_table_size('users'));
SELECT pg_size_pretty(pg_indexes_size('users'));
SELECT pg_size_pretty(pg_total_relation_size('users'));
```

### Dropping an Index

```sql
DROP INDEX idx_email;
```

### When to Create an Index

Create on: Primary Keys, Foreign Keys, frequently searched/sorted columns, columns in `WHERE`/`JOIN`/`ORDER BY`.

Avoid on: very small tables, frequently updated columns, columns with few unique values.

---

## Database Maintenance

### Measuring Object Size

```sql
SELECT pg_table_size('users');
SELECT pg_indexes_size('users');
SELECT pg_total_relation_size('users');
```

### Dead Tuples

When `UPDATE`/`DELETE` runs, old rows aren't immediately removed — they become **Dead Tuples**. They occupy disk space and slow queries.

### VACUUM

Removes dead tuples, makes space reusable.

```sql
VACUUM users;
```

### ANALYZE

Updates statistics used by the query planner.

```sql
ANALYZE users;
```

### VACUUM ANALYZE

```sql
VACUUM ANALYZE users;
```

Recommended after large `INSERT`/`UPDATE`/`DELETE`.

### Autovacuum

PostgreSQL automatically runs `VACUUM ANALYZE` in the background.

### Monitoring

```sql
SELECT relname, n_live_tup, n_dead_tup, last_vacuum, last_autovacuum, last_analyze
FROM pg_stat_all_tables;
```

### VACUUM FULL

Rewrites the table, shrinks size, returns space to OS — but blocks reads/writes while running.

```sql
VACUUM FULL users;
```

### TRUNCATE vs DELETE

| DELETE | TRUNCATE |
| --- | --- |
| Removes selected rows | Removes all rows |
| Supports `WHERE` | No `WHERE` |
| Creates dead tuples | No dead tuples |
| Slower | Faster |

### Maintenance Workflow

```
INSERT/UPDATE/DELETE → Dead Tuples → VACUUM → Reusable Space
Need planner stats? → ANALYZE
Need both? → VACUUM ANALYZE
Need disk space back? → VACUUM FULL
```

---

## Connecting Database to Server & Deployment

### Overall Flow

```
Client → Express Server → pool.query() → PostgreSQL → Response
```

### Required Packages

```bash
npm install pg dotenv
```

### Store Credentials (.env)

```
DB_USER=postgres
DB_HOST=localhost
DB_NAME=api
DB_PASSWORD=******
DB_PORT=5432
```

> Never push `.env` to GitHub.

### Load Credentials

```js
dotenv.config();
process.env.DB_USER
```

### Create Pool

```js
const pool = new Pool({
    user: process.env.DB_USER,
    host: process.env.DB_HOST,
    database: process.env.DB_NAME,
    password: process.env.DB_PASSWORD,
    port: process.env.DB_PORT,
});
```

### Run Queries

```js
await pool.query(
    "SELECT * FROM users WHERE id=$1",
    [id]
);
```

`$1` = parameterized query → prevents SQL Injection.

### Better Structure

```js
// db/index.js
export const query = (text, params) => pool.query(text, params);

// usage
db.query(...)
```

### SDLC

```
Plan → Design → Develop → Test → Deploy → Maintain
```

### Environments

```
Local → Staging → Production
```

### Render (PaaS)

Hosts backend, database, infrastructure.

### Deploy Flow

```
Local → git push → GitHub → Render → Live App
```

### Render Build Settings

```bash
# Build
npm install

# Start
node app.js
```

### Environment Variables (Render)

```
DATABASE_URL=...
PORT=10000
```

```js
process.env.DATABASE_URL
```

### Health Check

```js
app.get("/health", (req, res) => {
    res.sendStatus(200);
});
```

### Monitoring

- **Events** → Deployment history
- **Metrics** → Usage & bandwidth
- **Logs** → Errors & debugging

### Complete Flow

```
Write Code → GitHub → Render → Environment Variables → PostgreSQL → Users
```

### Remember

```
pg              → PostgreSQL driver
.env            → Store secrets
process.env     → Read secrets
Pool            → Manage DB connections
pool.query()    → Execute SQL
Render          → Deploy app
DATABASE_URL    → Connect Render app to Render DB
git push        → Auto Deploy
```

---
## Related
- [[01 - SQL Basics]]
- [[04 - Schema & Keys]]
- [[05 - Constraints & Triggers]]
- [[../05 - Backend/04 - Express.js]]
