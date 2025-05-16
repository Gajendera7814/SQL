
---

# SQL | DEFAULT Constraint

In SQL, maintaining data integrity and ensuring consistency across tables is important for effective database management. One way to achieve this is by using constraints. Among the many types of constraints, the **DEFAULT** constraint plays an important role in automating data insertion and ensuring that missing or null values in certain columns are handled efficiently.

In this article, we will explore the SQL DEFAULT constraint in detail, covering its purpose, syntax, practical use cases, and examples. We’ll also explain how it can help you maintain consistency in your database without requiring explicit values for every column in your insert statements.

---

## What is the SQL DEFAULT Constraint?

The DEFAULT constraint in SQL is used to provide a default value for a column when no value is specified during an `INSERT` operation. If a column has a DEFAULT constraint and no value is explicitly provided during the insertion of a record, the database will automatically insert the default value defined for that column.

---

## Syntax :

```sql
CREATE TABLE table_name (
    column1 datatype DEFAULT default_value,
    column2 datatype DEFAULT default_value,
    ...
);
````

---

## Key Points About the DEFAULT Constraint

* **Automatic Value Insertion**: The DEFAULT constraint ensures that if a value is not supplied during insertion, a pre-defined default value is used.
* **Simplifies Data Entry**: It simplifies data entry when certain fields often have common or default values.
* **Optional in SQL**: The DEFAULT constraint is optional. Not all columns require a default value.
* **Can Be Applied to Any Data Type**: It can be applied to any data type, including numbers, dates, and strings.
* **Not Applicable to NULL**: You cannot use the DEFAULT constraint to assign `NULL` as a default value. For null values, you can either omit the value or explicitly specify `NULL`.

---

## Using the DEFAULT Constraint during Table Creation

Let’s create a table and use the DEFAULT constraint for the `Location` column, ensuring that a default value of `'Noida'` is inserted when no value is provided.

### Query:

```sql
CREATE TABLE Geeks (
    ID INT NOT NULL,
    Name VARCHAR(255),
    Age INT,
    Location VARCHAR(255) DEFAULT 'Noida'
);
```

```sql
-- Explicit value
INSERT INTO Geeks (ID, Name, Age, Location) VALUES (4, 'Mira', 23, 'Delhi');

-- Using the DEFAULT constraint
INSERT INTO Geeks (ID, Name, Age, Location) VALUES (5, 'Hema', 27);

-- Explicit value again
INSERT INTO Geeks (ID, Name, Age, Location) VALUES (6, 'Neha', 25, 'Delhi');

-- Using DEFAULT constraint again
INSERT INTO Geeks (ID, Name, Age, Location) VALUES (7, 'Khushi', 26, DEFAULT);
```

**Output:**

*(This would show the data with 'Noida' as the default Location where not specified)*

---

## Dropping the DEFAULT Constraint

If you no longer want a column to use a default value, you can drop the DEFAULT constraint. This will only apply to new rows and will not affect existing data in the table.

### Syntax:

```sql
ALTER TABLE tablename
ALTER COLUMN columnname 
DROP DEFAULT;
```

### Query:

```sql
ALTER TABLE Geeks
ALTER COLUMN Location
DROP DEFAULT;
```

Let us add 2 new rows in the Geeks table:

### Query:

```sql
INSERT INTO Geeks VALUES (8, 'Komal', 24, 'Delhi');
INSERT INTO Geeks VALUES (9, 'Payal', 26, NULL);
```

> **Note** - Dropping the default constraint will not affect the current data in the table, it will only apply to new rows.

```sql
SELECT * FROM Geeks;
```

**Output:**

*(This would show that new entries do not use the default value and instead store the explicitly provided values including NULL)*

---
