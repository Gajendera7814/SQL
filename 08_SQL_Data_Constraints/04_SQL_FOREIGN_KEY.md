
---

# SQL FOREIGN KEY Constraint

A `FOREIGN KEY` constraint is a fundamental concept in relational databases, ensuring data integrity by enforcing relationships between tables. By linking a child table to a parent table, the foreign key establishes referential integrity. This constraint ensures that the values in the foreign key column match the primary key values in the referenced table, thereby maintaining consistent and valid data across the database.

---

## 🔗 SQL FOREIGN KEY

A `FOREIGN KEY` is a column or set of columns in one table that references the primary key columns of another table. This creates a relationship between the two tables, ensuring that the **child table** (which contains the foreign key) can only have values that exist in the **parent table's primary key column(s)**.

- The table containing the foreign key is called the **foreign table** (or **child table**).
- The table that the foreign key references is called the **primary table** (or **parent table**).

> The primary purpose of a foreign key is to maintain referential integrity.

---

## 🧾 Syntax

A foreign key can be created:

- During table creation using `CREATE TABLE`
- Or later using `ALTER TABLE`

---

### SQL FOREIGN KEY on `CREATE TABLE`

```sql
CREATE TABLE table_name (
  column1 datatype,
  column2 datatype,
  ...,
  CONSTRAINT fk_constraint_name FOREIGN KEY (column1, column2, ...)
    REFERENCES parent_table(column1, column2, ...)
);
````

---

### SQL FOREIGN KEY on `ALTER TABLE`

```sql
ALTER TABLE table_name
ADD CONSTRAINT fk_constraint_name FOREIGN KEY (column1, column2, ...)
REFERENCES parent_table(column1, column2, ...);
```

---

## ⚙️ Implementing Foreign Key

To implement foreign keys in a column of a table, follow the steps below. Make sure to have **MySQL Workbench** or **MySQL command-line client** installed on your system.

---

### 🧱 Step 1: Create a Database

```sql
CREATE DATABASE GEEKSFORGEEKS;
```

---

### 📥 Step 2: Select the Database

```sql
USE GEEKSFORGEEKS;
```

---

### 📋 Step 3: Create Tables and Define Foreign Key

We’ll create `STUDENT` and `COURSES` tables and then link them using a foreign key.

```sql
CREATE TABLE STUDENT (
  STUDENT_ID INT PRIMARY KEY,
  NAME VARCHAR(20),
  ADDRESS VARCHAR(20),
  AGE INT,
  DOB DATE
);
```

**Check table structure:**

```sql
DESC STUDENTS;
```

*Output: Creating table Student*

---

```sql
CREATE TABLE COURSES (
  COURSE_NAME VARCHAR(20),
  INSTRUCTOR VARCHAR(20),
  REFERENCE_ID INT,
  CONSTRAINT FK_REFER FOREIGN KEY (REFERENCE_ID)
    REFERENCES STUDENT(STUDENT_ID)
);
```

**Check table structure:**

```sql
DESC COURSES;
```

*Output: Creating courses table*

> ✅ We have successfully implemented a foreign key from `COURSES.REFERENCE_ID` to `STUDENT.STUDENT_ID`.

---

## 📚 SQL Foreign Key Constraint Example

In this example, we create a foreign key during table creation.

```sql
CREATE TABLE Customers (
  CustomerID INT PRIMARY KEY,
  CustomerName VARCHAR(50) NOT NULL
);

CREATE TABLE Orders (
  OrderID INT PRIMARY KEY,
  OrderNumber INT NOT NULL,
  CustomerID INT,
  FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```

**Insert Data:**

```sql
INSERT INTO Customers (CustomerID, CustomerName)
VALUES (1, 'John'), (2, 'Jane'), (3, 'Bob');

INSERT INTO Orders (OrderID, OrderNumber, CustomerID)
VALUES (1, 101, 1), (2, 102, 2), (3, 103, 3);
```

### 📊 Data Preview

**Customers Table:**

| CustomerID (Primary Key) | CustomerName |
| ------------------------ | ------------ |
| 1                        | John         |
| 2                        | Jane         |
| 3                        | Bob          |

**Orders Table:**

| OrderID (Primary Key) | OrderNumber | CustomerID (Foreign Key) |
| --------------------- | ----------- | ------------------------ |
| 1                     | 101         | 1                        |
| 2                     | 102         | 2                        |
| 3                     | 103         | 3                        |

---

## 🧪 Example 1: Insert Value in Foreign Key Table

If a corresponding value in the foreign table doesn't exist, the insert will fail.

```sql
INSERT INTO Orders (OrderID, OrderNumber, CustomerID)
VALUES (4, 104, 4);
```

**Output:**

```
Error: FOREIGN KEY constraint failed.
```

---

## 🧪 Example 2: Delete a Value in Foreign Key Table

Trying to delete a referenced record in the parent table will fail if child records exist.

```sql
DELETE FROM Customers 
WHERE CustomerID = "3";
```

**Output:**

```
Error: FOREIGN KEY constraint failed
```

---

## 🔍 Important Points About SQL FOREIGN KEY Constraint

* A `FOREIGN KEY` is a field (or collection of fields) in one table that refers to the `PRIMARY KEY` in another table.
* The table with the foreign key is the **child table**, and the table with the referenced key is the **parent table**.
* A table can have **multiple FOREIGN KEY constraints**.
* You can control behavior on updates and deletes in the parent table using:

  * `ON DELETE CASCADE`
  * `ON DELETE SET NULL`
  * `ON DELETE NO ACTION`
* Foreign keys **maintain referential integrity** in relational databases.

---

## ✅ Conclusion

The `FOREIGN KEY` constraint is an essential tool for ensuring **referential integrity** between related tables in a relational database.

By enforcing relationships between tables, it ensures:

* ✅ Data remains **consistent**
* ✅ Prevents **invalid or orphaned** records
* ✅ Builds a **robust and relational** structure

Whether you're designing tables from scratch or adding foreign keys to an existing schema, understanding how to use foreign keys properly will help you manage your data more effectively and **prevent common data-related errors**.

---
