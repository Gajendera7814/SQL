# 🏗️ SQL CREATE DATABASE – Complete Guide

This README provides a complete overview of the `CREATE DATABASE` command in SQL, how to switch to a database, delete one, system compatibility, and common mistakes to avoid.

---

## 📘 What is the `CREATE DATABASE` Command?

The `CREATE DATABASE` command is used to **create a new database** in SQL. It's the first step in organizing and managing your data.

### ✅ Syntax

```sql
CREATE DATABASE database_name;
```

### 💪 Example

```sql
CREATE DATABASE school_db;
```

---

## 🔄 Switching to Your New Database

Once a database is created, you must **select it** before creating tables or inserting data.

### ✅ Syntax

```sql
USE database_name;
```

### 💪 Example

```sql
USE school_db;
```

> ⚠️ Note: The `USE` command is not supported in **SQLite**. Instead, databases are accessed through file connections.

---

## ❌ Deleting a Database

To **permanently delete a database**, use the `DROP DATABASE` command.

### ✅ Syntax

```sql
DROP DATABASE database_name;
```

### 💪 Example

```sql
DROP DATABASE school_db;
```

> ⚠️ Be very careful! This removes all data and cannot be undone.

---

## 🌐 Database Compatibility Across SQL Systems

| Feature           | MySQL | PostgreSQL | SQL Server | SQLite           |
| ----------------- | ----- | ---------- | ---------- | ---------------- |
| `CREATE DATABASE` | ✅     | ✅          | ✅          | ✅ (file-based)   |
| `USE`             | ✅     | ✅          | ✅          | ❌ Not supported  |
| `DROP DATABASE`   | ✅     | ✅          | ✅          | ✅ (deletes file) |

> 💡 SQLite manages each database as a separate file — there's no `USE` command.

---

## ⚠️ Common Errors and How to Avoid Them

### 1. **Database Already Exists**

* **Error:** `Can't create database; database exists`
* **Fix:** Use `IF NOT EXISTS`:

  ```sql
  CREATE DATABASE IF NOT EXISTS school_db;
  ```

### 2. **Permission Denied**

* **Cause:** User doesn't have CREATE/DROP privileges
* **Fix:** Ask your DBA or use a higher-privilege account.

### 3. **Syntax Errors**

* **Fix:** Ensure correct SQL syntax — database names shouldn't start with numbers or contain spaces.

---

## ✅ Summary

* `CREATE DATABASE` initializes a new database.
* Use `USE database_name;` to begin using it.
* `DROP DATABASE` deletes it entirely.
* Syntax and support can vary slightly by SQL system.
