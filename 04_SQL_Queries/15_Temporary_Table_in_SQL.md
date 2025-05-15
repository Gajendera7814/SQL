
---

## What Are Temporary Tables in SQL?

A temporary table in SQL is a special type of table that is created and stored in the system's temporary database (such as TempDB in SQL Server). This table is primarily used to store and generate important mediation results when executing a query, stored procedure, or session.

Temporary tables are automatically deleted when the session or transaction that created them ends, making them perfect for temporary or intermediate data storage. They are particularly useful in situations where you need to perform calculations or data transformations without changing the permanent database structure.

---

## Syntax:

### To Create a Temporary Table

```sql
CREATE TABLE #EmpDetails (id INT, name VARCHAR(25));
````

### To Insert Values Into Temporary Table

```sql
INSERT INTO #EmpDetails VALUES (01, 'Lalit'), (02, 'Atharva');
```

### To Select Values from the Temporary Table

```sql
SELECT * FROM #EmpDetails;
```

### Result:

| id | name    |
| -- | ------- |
| 1  | Lalit   |
| 2  | Atharva |

---

## Types of Temporary Tables in SQL

There are 2 types of Temporary Tables: **Local Temporary Table**, and **Global Temporary Table**. These are explained as following below.

---

### Local Temporary Table

A Local Temp Table is available only for the session that has created it. It is automatically dropped (deleted) when the connection that has created it, is closed. To create Local Temporary Table single "#" is used as the prefix of a table name. Also, the user can drop this temporary table by using the `DROP TABLE #EmpDetails` query. There will be random numbers appended to the name of the table. If the Temporary Table is created inside the stored procedure, it gets dropped automatically upon the completion of stored procedure execution.

#### Example:

```sql
CREATE PROCEDURE ProcTemp 
AS
BEGIN
    CREATE TABLE #EmpDetails (id INT, name VARCHAR(25));
    INSERT INTO #EmpDetails VALUES (01, 'Lalit'), (02, 'Atharva');
    SELECT * FROM #EmpDetails;
END
EXECUTE ProcTemp;
```

---

### Global Temporary Table

To create a Global Temporary Table, add the "##" symbol before the table name.

#### Example:

```sql
CREATE TABLE ##EmpDetails (id INT, name VARCHAR(25));
```

Global Temporary Tables are visible to all connections and dropped when the last connection referencing the table is closed. Global Table Name must have a unique table name. There will be no random numbers suffixed at the end of the Table Name.

---

## Differences Between Local and Global Temporary Tables

| Feature       | Local Temporary Table                       | Global Temporary Table                                      |
| ------------- | ------------------------------------------- | ----------------------------------------------------------- |
| Prefix        | # (Single hash)                             | ## (Double hash)                                            |
| Scope         | Only the session that created it            | Available to all sessions                                   |
| Lifetime      | Automatically dropped when the session ends | Dropped when the last connection referencing the table ends |
| Accessibility | Only the creating session can access it     | All sessions can access it                                  |
| Usage         | Session-specific data storage               | Shared temporary data storage for multiple sessions         |

---

## Conclusion

Temporary tables in SQL are powerful tools for managing central data, performing complex calculations, and improving query performance. Whether you use local temporary tables for session-specific operations or global temporary tables to share data across multiple sessions, understanding how to use these tables effectively will inform your database management processes.

---
