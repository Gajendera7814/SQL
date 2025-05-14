
---

## What Are Temporary Tables in SQL?

A **temporary table** in SQL is a special type of table created and stored in the system's temporary database (like **TempDB** in SQL Server). Temporary tables are primarily used to store intermediate or transient data while executing a query, stored procedure, or session.

These tables are automatically deleted when the session or transaction that created them ends, making them perfect for temporary or intermediate data storage. They are especially useful for performing calculations or data transformations without affecting the permanent database structure.

### Syntax

#### To Create a Temporary Table:
```sql
CREATE TABLE #EmpDetails (id INT, name VARCHAR(25));  
````

#### To Insert Values Into the Temporary Table:

```sql
INSERT INTO #EmpDetails VALUES (01, 'Lalit'), (02, 'Atharva');
```

#### To Select Values from the Temporary Table:

```sql
SELECT * FROM #EmpDetails;
```

**Result:**

| id | name    |
| -- | ------- |
| 1  | Lalit   |
| 2  | Atharva |

---

## Types of Temporary Tables in SQL

There are **two types** of Temporary Tables:

1. **Local Temporary Table**
2. **Global Temporary Table**

### Local Temporary Table

A **Local Temporary Table** is available only for the session that has created it. It is automatically dropped when the connection that created it is closed.

* A Local Temporary Table uses a **single `#`** as the prefix.
* If created inside a stored procedure, the table will be automatically dropped upon completion of the procedure.

#### Example:

```sql
CREATE PROCEDURE ProcTemp 
AS
BEGIN
    CREATE TABLE #EmpDetails (id INT, name VARCHAR(25)); 
    INSERT INTO #EmpDetails VALUES (01, 'Lalit'), (02, 'Atharva');
    SELECT * FROM #EmpDetails;
END;

EXECUTE ProcTemp;
```

### Global Temporary Table

A **Global Temporary Table** is available to all sessions and remains available until the last connection referencing the table is closed.

* A Global Temporary Table uses **double `##`** as the prefix.
* The table must have a unique name to avoid conflicts.

#### Example:

```sql
CREATE TABLE ##EmpDetails (id INT, name VARCHAR(25)); 
```

---

## Differences Between Local and Global Temporary Tables

| Feature           | Local Temporary Table                   | Global Temporary Table                              |
| ----------------- | --------------------------------------- | --------------------------------------------------- |
| **Prefix**        | `#` (Single hash)                       | `##` (Double hash)                                  |
| **Scope**         | Only the session that created it        | Available to all sessions                           |
| **Lifetime**      | Automatically dropped when session ends | Dropped when last connection referencing it ends    |
| **Accessibility** | Only the creating session can access it | All sessions can access it                          |
| **Usage**         | Session-specific data storage           | Shared temporary data storage for multiple sessions |

---

## Conclusion

Temporary tables in SQL are powerful tools for managing central data, performing complex calculations, and improving query performance. Whether you use local temporary tables for session-specific operations or global temporary tables to share data across multiple sessions, understanding how to use these tables effectively will enhance your database management process.

Temporary tables allow you to store and manipulate data without impacting the permanent database structure, making them ideal for tasks such as:

* Data manipulation
* Backup operations
* Testing and experimentation

---
