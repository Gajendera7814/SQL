
---

# SQL DELETE Statement

The SQL DELETE statement is one of the most commonly used commands in SQL (Structured Query Language). It allows you to remove one or more rows from the table depending on the situation. Unlike the DROP statement, which removes the entire table, the DELETE statement removes data (rows) from the table retaining only the table structure, constraints, and schema.

---

## SQL DELETE Statement

The SQL DELETE statement removes one or more rows from a database table based on a condition specified in the WHERE clause. It's a DML (Data Manipulation Language) operation that modifies the data within the table without altering its structure.

### Syntax

```sql
DELETE FROM table_name
WHERE some_condition;
````

### Parameter Explanation

* **some\_condition**: A condition used to filter the rows you want to delete.
* **table\_name**: The name of the table from which you want to delete the rows.

> **Note:** We can delete single as well as multiple records depending on the condition we provide in the WHERE clause. If we omit the WHERE clause then all of the records will be deleted and the table will be empty.

---

## Examples of SQL DELETE Statement

Assume we have created a table named `GFG_Employees` in SQL, which contains the personal details of the employee including their id, name, email and department etc. as shown below:

```sql
CREATE TABLE GFG_Employees (
   id INT PRIMARY KEY,
   name VARCHAR(20),
   email VARCHAR(25),
   department VARCHAR(20)
);
```

```sql
INSERT INTO GFG_Employees (id, name, email, department) VALUES 
(1, 'Jessie', 'jessie23@gmail.com', 'Development'),
(2, 'Praveen', 'praveen_dagger@yahoo.com', 'HR'),
(3, 'Bisa', 'dragonBall@gmail.com', 'Sales'),
(4, 'Rithvik', 'msvv@hotmail.com', 'IT'),
(5, 'Suraj', 'srjsunny@gmail.com', 'Quality Assurance'),
(6, 'Om', 'OmShukla@yahoo.com', 'IT'),
(7, 'Naruto', 'uzumaki@konoha.com', 'Development');
```

```sql
SELECT * FROM GFG_Employees;
```

### Output

| id | name    | email                                                        | department        |
| -- | ------- | ------------------------------------------------------------ | ----------------- |
| 1  | Jessie  | [jessie23@gmail.com](mailto:jessie23@gmail.com)              | Development       |
| 2  | Praveen | [praveen\_dagger@yahoo.com](mailto:praveen_dagger@yahoo.com) | HR                |
| 3  | Bisa    | [dragonBall@gmail.com](mailto:dragonBall@gmail.com)          | Sales             |
| 4  | Rithvik | [msvv@hotmail.com](mailto:msvv@hotmail.com)                  | IT                |
| 5  | Suraj   | [srjsunny@gmail.com](mailto:srjsunny@gmail.com)              | Quality Assurance |
| 6  | Om      | [OmShukla@yahoo.com](mailto:OmShukla@yahoo.com)              | IT                |
| 7  | Naruto  | [uzumaki@konoha.com](mailto:uzumaki@konoha.com)              | Development       |

---

### Example 1: Deleting Single Record

We can use the DELETE statement with a condition to delete a specific row from a table. The WHERE clause ensures only the intended record is removed. We can delete the records named **Rithvik** by using the below query:

```sql
DELETE FROM GFG_Employees WHERE NAME = 'Rithvik';
```

### Output

The record with name `Rithvik` is deleted from the table.

---

### Example 2: Deleting Multiple Records

To delete multiple records, you can specify a condition that matches several rows. Let's delete the rows from the table `GFG_Employees` where the department is "Development". This will delete 2 rows (the first row and the seventh row).

```sql
DELETE FROM GFG_Employees 
WHERE department = 'Development';
```

### Output

Rows with `department = 'Development'` (Jessie and Naruto) are deleted.

---

### Example 3: Delete All Records from a Table

If we need to delete all records from the table, we can omit the WHERE clause, or alternatively use the DELETE statement with an asterisk `*` to denote all rows.

```sql
DELETE FROM GFG_Employees;
-- OR
DELETE * FROM GFG_Employees;
```

### Output

All of the records in the table will be deleted. There are no records left to display. The table `GFG_Employees` will become empty.

---

## Rolling Back DELETE Operations

Since the DELETE statement is a DML operation, it can be rolled back when executed in a transaction. If you accidentally delete records or need to repeat the process, you can use the `ROLLBACK` command.

```sql
START TRANSACTION;
DELETE FROM GFG_Employees WHERE department = 'Development';
-- If needed, you can rollback the deletion
ROLLBACK;
```

**Explanation**: The `ROLLBACK` command will undo the changes made by the DELETE statement, effectively restoring the records that were deleted during the transaction.

---

## Best Practices for Using SQL DELETE

To use the SQL DELETE statement safely and efficiently, here are some best practices:

* **Use Transactions**: Wrap DELETE statements in transactions to provide an option to roll back changes if necessary. This ensures data integrity.
* **Always Use a WHERE Clause**: Avoid deleting all rows by accident. Always filter records using a WHERE clause to specify which rows to delete. Omitting the WHERE clause will delete all records.
* **Backup Data**: Before performing large deletions, ensure that you have a backup of the data to avoid irreversible loss.
* **Test on Development Server**: Always test your DELETE queries on a development or staging environment to ensure they produce the desired result before executing them on a live database.
* **Optimize Deletions**: For large datasets, delete records in batches to reduce performance impact and avoid long-running queries.
* **Use Caution When Deleting Data**: Be extra cautious when deleting records from sensitive or production databases. Always verify the condition in the WHERE clause to ensure you're deleting the right data.

---

## Conclusion

The SQL DELETE statement is a powerful tool for removing data from a database table based on specific conditions. By understanding the correct syntax, how to delete individual or multiple records, and how to handle performance issues, you can use the DELETE statement efficiently and safely.

---
