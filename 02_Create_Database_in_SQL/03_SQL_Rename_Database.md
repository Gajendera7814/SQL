
---

## 📘 SQL Query to Rename Database

Renaming a database in SQL allows you to change the name of an existing database without losing any data. However, this operation must be performed carefully, as it may involve downtime or system-specific limitations.

### ✅ Syntax

The syntax for renaming a database varies slightly across different SQL systems. Below is the general format:

```sql
ALTER DATABASE old_database_name RENAME TO new_database_name;
````

### 💡 Example

```sql
ALTER DATABASE school_db RENAME TO school_db_new;
```

---

## 🔄 How to Rename Database in SQL?

Renaming a database involves using the `ALTER DATABASE` statement, which is supported by most relational database management systems (RDBMS). Follow these steps:

1. **Ensure No Active Connections:**

   * Before renaming a database, ensure there are no active connections to the database.
2. **Use the Correct SQL Command:**

   * Use the appropriate command for your SQL system. Here's the general syntax for renaming a database.

---

## 💪 SQL Rename Database Example

### Example 1: Renaming a Database in MySQL and PostgreSQL

```sql
ALTER DATABASE school_db RENAME TO school_db_new;
```

This command renames the `school_db` to `school_db_new` in MySQL and PostgreSQL.

### Example 2: Renaming a Database in SQL Server

In SQL Server, renaming a database requires using the `sp_renamedb` stored procedure:

```sql
EXEC sp_renamedb 'old_database_name', 'new_database_name';
```

### 💡 Example

```sql
EXEC sp_renamedb 'school_db', 'school_db_new';
```

This will rename `school_db` to `school_db_new` in SQL Server.

---

## 📝 Important Considerations When Renaming a Database

1. **Active Connections:**

   * Ensure there are no active connections to the database before renaming it. Most systems will prevent renaming if there are open connections.

2. **Permissions:**

   * You must have sufficient privileges to rename a database. Typically, this requires admin or superuser access.

3. **Backup the Database:**

   * It's always a good idea to back up your database before performing operations like renaming, just in case something goes wrong.

4. **Application Configuration:**

   * After renaming the database, you must update any applications, scripts, or services that depend on the old database name to avoid connection issues.

5. **Database Compatibility:**

   * Not all database systems support renaming a database directly. Ensure that your system supports this operation (for example, SQLite does not support `ALTER DATABASE`).

---

## ⚠️ Troubleshooting Database Rename Issues

### 1. **Database is in Use**

* **Error Message:** "Cannot rename database because it is in use."
* **Solution:** Disconnect all active connections to the database before renaming it. You may need to shut down any applications using the database temporarily.

### 2. **Insufficient Privileges**

* **Error Message:** "You do not have permission to rename the database."
* **Solution:** Ensure you have the necessary privileges (admin or superuser). Contact your database administrator if needed.

### 3. **Database System Does Not Support Renaming**

* **Error Message:** "Renaming a database is not supported."
* **Solution:** If your RDBMS doesn’t support renaming a database, you may need to create a new database, copy data from the old one, and then drop the old database.

---

## ✅ Summary

* Renaming a database can be done using the `ALTER DATABASE` statement in most SQL systems.
* Always ensure there are no active connections, and you have the correct permissions before renaming a database.
* Some systems, like SQLite, do not support renaming databases directly.
* Troubleshoot common issues like active connections and permission errors before proceeding with a rename operation.

```