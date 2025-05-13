
---
# 🛠️ SQL ALTER TABLE Command

The `ALTER TABLE` command in SQL allows modification of the structure of an existing table. Whether renaming a table or column, adding new columns, or changing data types, `ALTER TABLE` enables schema changes **without affecting existing data**.

This command is **essential for database management** and is widely used to ensure that schemas evolve alongside application requirements.

---

## 🎯 What You Can Do With `ALTER TABLE`

- ✅ Rename a table
- ✅ Rename a column
- ✅ Add a new column
- ✅ Modify the data type of an existing column
- ✅ Delete a column
- ✅ Change default values for columns

---

## 🔧 Syntax for ALTER TABLE

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

### 4. Modifying a Column’s Data Type

```sql
ALTER TABLE table_name
MODIFY COLUMN column_name new_datatype;
```

---

## 💡 Examples of Using ALTER TABLE

### 1. Create a Sample Table

```sql
CREATE TABLE Student (
  id INT PRIMARY KEY,
  name VARCHAR(50),
  age INT,
  email VARCHAR(50),
  phone VARCHAR(20)
);
```

### 2. Insert Sample Data

```sql
INSERT INTO Student (id, name, age, email, phone) 
VALUES 
(1, 'Amit', 20, 'amit@gmail.com', '9999999999'),
(2, 'Rahul', 22, 'rahul@yahoo.com', '8888888888'),
(3, 'Priya', 21, 'priya@hotmail.com', '7777777777'),
(4, 'Sonia', 23, 'sonia@gmail.com', '6666666666'),
(5, 'Kiran', 19, 'kiran@yahoo.com', '5555555555');
```

---

## 📝 Practical ALTER TABLE Operations

### ✅ Example 1: Rename a Column

```sql
ALTER TABLE Student 
RENAME COLUMN name TO FIRST_NAME;
```

✔️ Renames the `name` column to `FIRST_NAME`.

---

### ✅ Example 2: Rename the Table

```sql
ALTER TABLE Student 
RENAME TO Student_Details;
```

✔️ Renames the table from `Student` to `Student_Details`.

---

### ✅ Example 3: Add a New Column

```sql
ALTER TABLE Student 
ADD marks INT;
```

✔️ Adds a new column `marks` of type `INT`.

---

### ✅ Example 4: Modify Column Data Type

Convert `phone` column from `VARCHAR(20)` to `BIGINT`:

```sql
ALTER TABLE Student_Details
MODIFY COLUMN phone BIGINT;
```

✔️ Ensures phone numbers are stored as integers.

---

### ✅ Example 5: Remove a Column

```sql
ALTER TABLE Student_Details
DROP COLUMN marks;
```

✔️ Deletes the `marks` column permanently.

---

### ✅ Example 6: Set a Default Value for a Column

```sql
ALTER TABLE Student_Details
ALTER COLUMN age SET DEFAULT 18;
```

✔️ Sets the default value for `age` to `18`.

---

## 🔄 Variations Across SQL Dialects

### 📌 MySQL / MariaDB

To rename a column:

```sql
ALTER TABLE Student
CHANGE COLUMN old_column_name new_column_name datatype;
```

### 📌 Oracle

To rename a column:

```sql
ALTER TABLE Student
RENAME COLUMN old_column_name TO new_column_name;
```

To rename a table:

```sql
RENAME Student TO Student_Details;
```

---

## 🧠 Conclusion

The `ALTER TABLE` command in SQL is a **powerful tool for schema evolution**:

* It helps adapt the structure of tables without losing existing data.
* You can rename tables and columns, add or remove columns, and change data types.
* Proper use of this command ensures that your database remains flexible, maintainable, and aligned with changing application requirements.

> ✅ Use `ALTER TABLE` with care, especially when modifying column types or dropping columns, as it may affect existing application logic and data integrity.

```