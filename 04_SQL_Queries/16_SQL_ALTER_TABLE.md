
---

## SQL ALTER TABLE STATEMENT

The ALTER TABLE statement in SQL is used to modify an existing table structure in a database without losing any data. It allows you to add, remove, or modify columns, change data types, or apply constraints to improve data integrity and ensure that the table meets evolving business requirements. It allows for structural changes like adding new columns, modifying existing ones, deleting columns, and renaming columns within a table. To alter/modify the table use the ALTER TABLE syntax:

### Syntax:

```sql
ALTER TABLE table_name
[ADD | DROP | MODIFY] column_name datatype;
````

### Key Terms

* `table_name` refers to the name of the table you want to modify.
* `ADD` is used to add a new column.
* `DROP` is used to remove an existing column.
* `MODIFY` is used to change the datatype or definition of an existing column.

---

## Common Use Cases for SQL ALTER TABLE

### 1. ADD - To add a new column to the table

The ADD clause is used to add a new column to an existing table. You must specify the name of the new column and its data type.

**Query:**

```sql
ALTER TABLE table_name
ADD column_name datatype;
```

---

### 2. MODIFY/ALTER - To change the data type of an existing column

The MODIFY (or ALTER COLUMN in some databases like SQL Server) clause is used to modify the definition of an existing column, such as changing its data type or size.

**Query:**

```sql
ALTER TABLE table_name
MODIFY COLUMN column_name datatype;
```

---

### 3. DROP - To delete an existing column from the table

The DROP clause allows you to remove a column from a table. Be cautious when using this command as it will permanently remove the column and its data.

**Query:**

```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

---

### 4. RENAME COLUMN - To rename an existing column

We can rename an existing column using the RENAME COLUMN clause. This allows you to change the name of a column while preserving its data type and content.

**Query:**

```sql
ALTER TABLE table_name
RENAME COLUMN old_name TO new_name;
```

---

### 5. RENAME TO - To rename the table itself

We can rename an entire table using the RENAME TO clause. This changes the name of the table while preserving its structure and data.

```sql
ALTER TABLE table_name
RENAME TO new_table_name;
```

---

## SQL ALTER TABLE Examples

Below are various examples demonstrating different use cases of the ALTER TABLE statement in SQL. These examples showcase how to add, modify, drop, and rename columns or tables, providing a clear understanding of the flexibility and utility of the ALTER TABLE statement.

---

### 1. Adding a New Column to a Table

To add a new column to an existing table, you can use the ADD clause. Here’s an example where we add a column named `Email` to the `Students` table:

```sql
ALTER TABLE Students
ADD Email varchar(255);
```

---

### 2. Removing a Column from a Table

We can remove an existing column from a table using the DROP COLUMN clause. Here’s an example where we remove the `Email` column from the `Students` table:

```sql
ALTER TABLE Students
DROP COLUMN Email;
```

---

### 3. Modifying an Existing Column's Data Type

To change the data type or size of an existing column, you can use the MODIFY clause. For instance, if you want to change the data type of a column, use:

```sql
ALTER TABLE table_name
MODIFY COLUMN column_name datatype;
```

---

## SQL ALTER TABLE Queries

Let's explore the ALTER TABLE queries using a `Student` table with columns `ROLL_NO` and `NAME`, and demonstrate various modifications such as adding, modifying, and dropping columns. Here's how you can execute these operations:

| ROLL\_NO | NAME  |
| -------- | ----- |
| 1        | Ram   |
| 2        | Abhi  |
| 3        | Rahul |
| 4        | Tanu  |

---

### 1. Add Columns (AGE and COURSE) to the Student Table

To add new columns `AGE` and `COURSE` to the Student table, you can use the ALTER TABLE statement with the ADD clause.

**Query:**

```sql
ALTER TABLE Student ADD 
(AGE number(3), COURSE varchar(40));
```

**Output:**

| ROLL\_NO | NAME  |
| -------- | ----- |
| 1        | Ram   |
| 2        | Abhi  |
| 3        | Rahul |
| 4        | Tanu  |

**Explanation:** This adds the `AGE` column with a numeric data type and the `COURSE` column with a `VARCHAR(40)` type. The columns are added to the table, but the values are empty initially.

---

### 2. Modify Column COURSE to Reduce its Size

If you want to reduce the size of the `COURSE` column from `VARCHAR(40)` to `VARCHAR(20)`, you can modify the column's data type using the MODIFY clause.

**Query:**

```sql
ALTER TABLE Student 
MODIFY COURSE varchar(20);
```

**Explanation:** After running the above query, the `COURSE` column's data type will now allow a maximum of 20 characters instead of 40. This modifies the column's size limit.

---

### 3. Drop the COURSE Column from the Student Table

To remove the `COURSE` column completely from the Student table, you can use the DROP COLUMN clause.

**Query:**

```sql
ALTER TABLE Student 
DROP COLUMN COURSE;
```

**Output:**

| ROLL\_NO | NAME  |
| -------- | ----- |
| 1        | Ram   |
| 2        | Abhi  |
| 3        | Rahul |
| 4        | Tanu  |

**Explanation:** After executing this query, the `COURSE` column is permanently removed from the table, leaving just the `ROLL_NO`, `NAME`, and `AGE` columns.

---

## Conclusion

The SQL ALTER TABLE statement is an essential tool for modifying the structure of an existing table. Whether you need to add, delete, or modify columns, or even rename the table or columns, ALTER TABLE provides the flexibility needed to manage your database schema efficiently. By following best practices and using this command wisely, we can maintain the integrity and performance of your database while making necessary structural changes.

---
