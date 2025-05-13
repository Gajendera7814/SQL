
---

# 🧹 SQL DELETE Statement

The **SQL DELETE** statement is used to remove one or more rows from a table based on conditions specified in the `WHERE` clause. This is a **Data Manipulation Language (DML)** command that modifies data **without altering the structure** of the table.

---

## 🧾 Syntax

```sql
DELETE FROM table_name
WHERE some_condition;
````

### 📌 Parameters

* **`table_name`**: Name of the table from which rows are to be deleted.
* **`some_condition`**: A filtering condition to match the rows to be deleted.

> ⚠️ **Note**: Omitting the `WHERE` clause will delete **all records** from the table, making it empty.

---

## 📘 Examples of SQL DELETE Statement

Assume a table `GFG_Employees` has been created and populated with the following structure and records:

```sql
CREATE TABLE GFG_Employees (
   id INT PRIMARY KEY,
   name VARCHAR(20),
   email VARCHAR(25),
   department VARCHAR(20)
);

INSERT INTO GFG_Employees (id, name, email, department) VALUES 
(1, 'Jessie', 'jessie23@gmail.com', 'Development'),
(2, 'Praveen', 'praveen_dagger@yahoo.com', 'HR'),
(3, 'Bisa', 'dragonBall@gmail.com', 'Sales'),
(4, 'Rithvik', 'msvv@hotmail.com', 'IT'),
(5, 'Suraj', 'srjsunny@gmail.com', 'Quality Assurance'),
(6, 'Om', 'OmShukla@yahoo.com', 'IT'),
(7, 'Naruto', 'uzumaki@konoha.com', 'Development');
```

---

### ✅ Example 1: Deleting a Single Record

Delete a single employee where the name is `'Rithvik'`.

```sql
DELETE FROM GFG_Employees WHERE name = 'Rithvik';
```

✔️ This removes only the record that matches the condition.

---

### ✅ Example 2: Deleting Multiple Records

Delete employees from the `'Development'` department.

```sql
DELETE FROM GFG_Employees 
WHERE department = 'Development';
```

✔️ This will delete 2 rows: `'Jessie'` and `'Naruto'`.

---

### ✅ Example 3: Delete All Records from a Table

You can delete all data from the table using:

```sql
DELETE FROM GFG_Employees;
-- or (not recommended in most databases)
DELETE * FROM GFG_Employees;
```

✔️ This removes **all records**, making the table empty.

---

## ♻️ Rolling Back DELETE Operations

Since `DELETE` is a DML command, it **can be rolled back** if wrapped in a transaction.

```sql
START TRANSACTION;

DELETE FROM GFG_Employees 
WHERE department = 'Development';

-- Undo changes if needed
ROLLBACK;
```

> 📝 The `ROLLBACK` command undoes the deletion, restoring all deleted rows.

---

## ✅ Best Practices for Using SQL DELETE

1. **Use Transactions**
   Wrap deletions in transactions to provide rollback safety.

2. **Always Use a WHERE Clause**
   Prevent accidental full-table deletes.

3. **Backup Data**
   Always have a backup before running large deletions.

4. **Test in a Dev Environment**
   Verify your query's behavior before running in production.

5. **Batch Deletes for Large Datasets**
   Break large deletions into smaller batches to minimize performance impact.

6. **Double Check the WHERE Clause**
   Validate your filters to ensure only the intended records are deleted.

---

> ⚠️ Use caution when using `DELETE` on production systems. Deletion is permanent unless backed up or rolled back inside a transaction.

```