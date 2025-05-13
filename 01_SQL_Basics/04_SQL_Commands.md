
---

# 🛠️ SQL Commands – DDL, DQL, DML, DCL, TCL

This guide explains the five main types of SQL commands with examples. These commands are the foundation for interacting with relational databases.

---

## 📦 1. DDL – Data Definition Language

DDL commands define the structure of a database (tables, schemas, etc.).

| Command | Description |
|---------|-------------|
| `CREATE` | Creates a new table or database |
| `ALTER`  | Modifies an existing table (add/remove columns) |
| `DROP`   | Deletes a table or database permanently |
| `TRUNCATE` | Removes all data from a table but keeps the structure |

🔹 **Example:**
```sql
CREATE TABLE users (
  id INT PRIMARY KEY,
  name VARCHAR(100)
);
````

---

## 🔍 2. DQL – Data Query Language

DQL is used to **fetch/query** data from the database.

| Command  | Description                            |
| -------- | -------------------------------------- |
| `SELECT` | Retrieves data from one or more tables |

🔹 **Example:**

```sql
SELECT name FROM users WHERE id = 1;
```

---

## ✏️ 3. DML – Data Manipulation Language

DML commands are used to modify data **inside** tables.

| Command  | Description               |
| -------- | ------------------------- |
| `INSERT` | Adds new data to a table  |
| `UPDATE` | Modifies existing records |
| `DELETE` | Removes data from a table |

🔹 **Example:**

```sql
INSERT INTO users (id, name) VALUES (1, 'Alice');
```

---

## 🔐 4. DCL – Data Control Language

DCL controls **access permissions** and **security** of the database.

| Command  | Description                  |
| -------- | ---------------------------- |
| `GRANT`  | Gives user access privileges |
| `REVOKE` | Removes access privileges    |

🔹 **Example:**

```sql
GRANT SELECT ON users TO 'read_only_user';
```

---

## 🔄 5. TCL – Transaction Control Language

TCL manages **transactions** (groups of operations) and ensures data integrity.

| Command           | Description                                 |
| ----------------- | ------------------------------------------- |
| `COMMIT`          | Saves all changes made during a transaction |
| `ROLLBACK`        | Undoes changes if an error occurs           |
| `SAVEPOINT`       | Sets a checkpoint in a transaction          |
| `SET TRANSACTION` | Sets properties for a transaction           |

🔹 **Example:**

```sql
BEGIN;
UPDATE users SET name = 'Bob' WHERE id = 1;
COMMIT;
```

---

## 🧠 Summary Table

| Category | Commands                      |
| -------- | ----------------------------- |
| DDL      | CREATE, ALTER, DROP, TRUNCATE |
| DQL      | SELECT                        |
| DML      | INSERT, UPDATE, DELETE        |
| DCL      | GRANT, REVOKE                 |
| TCL      | COMMIT, ROLLBACK, SAVEPOINT   |

---


# 🗃️ DROP vs TRUNCATE vs DELETE in SQL

This document explains the key differences between the `DROP`, `TRUNCATE`, and `DELETE` commands in SQL. All three are used to remove data, but they behave differently in terms of structure, speed, and rollback capability.

---

## 🔍 Purpose

| Command  | Description |
|----------|-------------|
| `DROP`   | Completely deletes the table including its structure |
| `TRUNCATE` | Removes all rows from the table, but keeps the structure |
| `DELETE` | Deletes specific rows using conditions (optional) |

---

## 🔄 Key Differences

| Feature | `DROP` | `TRUNCATE` | `DELETE` |
|--------|--------|------------|----------|
| Removes Table Structure | ✅ Yes | ❌ No | ❌ No |
| Removes All Data | ✅ Yes | ✅ Yes | ✅ Optional |
| Supports `WHERE` Clause | ❌ No | ❌ No | ✅ Yes |
| Can Be Rolled Back | ❌ No (irreversible) | ✅ Yes (if inside a transaction) | ✅ Yes |
| Affects Table Schema | ✅ Deletes schema | ❌ Keeps schema | ❌ Keeps schema |
| Triggers Executed | ❌ No | ❌ No | ✅ Yes |
| Execution Speed | ⚡ Fastest | ⚡ Faster | 🐢 Slower (row-by-row) |

---

## 💡 Use Cases

- Use `**DELETE**` when:
  - You want to remove selected rows using a condition.
  - You need to fire triggers or maintain audit logs.

- Use `**TRUNCATE**` when:
  - You want to quickly delete all rows from a table.
  - You don’t need triggers or conditions.
  - You want to keep the table structure for future use.

- Use `**DROP**` when:
  - You want to permanently remove the table and its data.

---

## 🧪 SQL Examples

```sql
-- DELETE specific rows
DELETE FROM employees WHERE department = 'HR';

-- TRUNCATE the entire table (remove all rows)
TRUNCATE TABLE employees;

-- DROP the table completely
DROP TABLE employees;

