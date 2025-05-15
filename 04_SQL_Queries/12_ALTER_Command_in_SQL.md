
---

## What is ALTER Command in SQL?

The ALTER TABLE command in SQL allows us to modify the structure of an existing table. Whether we need to rename a table, rename a column, add a new column, or change the data type of a column, this command makes it easy to apply changes without affecting the data already stored. The ALTER command is fundamental for database management and is often used by developers to keep schemas aligned with evolving application needs.

Here are some common tasks you can achieve using the ALTER command:

- Renaming a table.  
- Changing a column name.  
- Adding or deleting columns.  
- Modifying the data type of a column.  

---

## Syntax for ALTER Command

### 1. Renaming a Table
```sql
ALTER TABLE table_name
RENAME TO new_table_name;
````

### 2. Renaming a Column

```sql
ALTER TABLE table_name
RENAME COLUMN old_column_name TO new_column_name;
```

### 3. Adding a New Column

```sql
ALTER TABLE table_name
ADD column_name datatype;
```

### 4. Modifying a Column Data Type

```sql
ALTER TABLE table_name
MODIFY COLUMN column_name new_datatype;
```

---

## Examples of ALTER Command in SQL

Below are practical examples to help us understand how to use the ALTER command effectively in various scenarios. These examples includes renaming tables or columns, adding new columns, or changing column data types.

### 1. Create a Sample Table

First, let's create a sample Student table to demonstrate the ALTER command:

```sql
CREATE TABLE Student (
  id INT PRIMARY KEY,
  name VARCHAR(50),
  age INT,
  email VARCHAR(50),
  phone VARCHAR(20)
);
```

---

### 2. Insert Sample Data into the Table

Let's insert some data and then perform ALTER operation to understand better about alter command.

```sql
INSERT INTO Student (id, name, age, email, phone) 
VALUES 
(1, 'Amit', 20, 'amit@gmail.com', '9999999999'),
(2, 'Rahul', 22, 'rahul@yahoo.com', '8888888888'),
(3, 'Priya', 21, 'priya@hotmail.com', '7777777777'),
(4, 'Sonia', 23, 'sonia@gmail.com', '6666666666'),
(5, 'Kiran', 19, 'kiran@yahoo.com', '5555555555');
```

#### Output

```
Student Table
Student Table
```

---

### Example 1: Rename a Column

Change the name of column `name` to `FIRST_NAME` in table `Student`. To change the column name of the existing table we have to use `COLUMN` keyword before writing the existing column name to change.

#### Syntax

```sql
ALTER TABLE Student RENAME COLUMN Column_NAME TO FIRST_NAME;
```

#### Query

```sql
ALTER TABLE Student RENAME Column name TO FIRST_NAME;
```

#### Output

```
Output
```

---

### Example 2: Rename a Table

In this example, we want to rename the table from `Student` to `Student_Details` using the ALTER TABLE command, making the name more descriptive and relevant to its content.

#### Query

```sql
ALTER TABLE Student RENAME TO Student_Details;
```

#### Output

```
Student_Details table
Student_Details table
```

---

### Example 3: Add a New Column

To add a new column to the existing table, we first need to select the table with ALTER TABLE command `table_name`, and then we will write the name of the new column and its datatype with `ADD column_name datatype`. Let's have a look below to understand better.

#### Syntax

```sql
ALTER TABLE table_name
ADD column_name datatype;
```

#### Query

```sql
ALTER TABLE Student ADD marks INT;
```

#### Output

```
output
output
```

---

### 5. Modify a Column Data Type

In the example, the `phone` column is updated from `VARCHAR(20)` to `BIGINT` to store numerical data more efficiently and ensure data integrity for phone numbers without unnecessary characters.

#### Syntax

```sql
ALTER TABLE table_name
MODIFY COLUMN column_name new_datatype;
```

#### Query

```sql
ALTER TABLE Student_Details
MODIFY COLUMN phone BIGINT;
```

#### Output

| id | name  | age | email                                         | phone      |
| -- | ----- | --- | --------------------------------------------- | ---------- |
| 1  | Amit  | 20  | [amit@gmail.com](mailto:amit@gmail.com)       | 9999999999 |
| 2  | Rahul | 22  | [rahul@yahoo.com](mailto:rahul@yahoo.com)     | 8888888888 |
| 3  | Priya | 21  | [priya@hotmail.com](mailto:priya@hotmail.com) | 7777777777 |
| 4  | Sonia | 23  | [sonia@gmail.com](mailto:sonia@gmail.com)     | 6666666666 |
| 5  | Kiran | 19  | [kiran@yahoo.com](mailto:kiran@yahoo.com)     | 5555555555 |

**Explanation:**

* The `phone` column now has a `BIGINT` data type, suitable for storing large numeric values.
* Existing data remains unchanged but is stored as integers instead of strings.

---

## Additional ALTER Command Use Cases

### 1. Removing a Column

In some cases, we might need to remove a column. To do that, you can use the `DROP COLUMN` syntax:

```sql
ALTER TABLE Student_Details
DROP COLUMN marks;
```

This command deletes the `marks` column entirely from the table.

---

### 2. Changing a Column's Default Value

We can also modify a column’s default value using the `SET DEFAULT` clause:

```sql
ALTER TABLE Student_Details
ALTER COLUMN age SET DEFAULT 18;
```

---

### 3. Renaming a Table or Column in Different Databases

> Note: SQL syntax can vary across different database systems. Here’s how we would rename a table or column in MySQL, MariaDB, and Oracle:

#### MySQL / MariaDB:

The syntax for renaming a column is similar, but you must also use the `CHANGE COLUMN` command to rename a column:

```sql
ALTER TABLE Student
CHANGE COLUMN old_column_name new_column_name datatype;
```

#### Oracle:

Oracle supports the `RENAME COLUMN` syntax but requires different syntax for renaming a table:

```sql
ALTER TABLE Student RENAME COLUMN old_column_name TO new_column_name;
```

---

## Conclusion

The SQL ALTER TABLE command is an effective way to modify the structure of an already-existing tables in a database. When necessary, we can use ALTER TABLE to rename the entire table, rename a specific column in SQL, or change a column name to something more descriptive. This command is important for database administration since it also enables the addition of new columns and the modification of data types.

---
