
---

## What is SQL INSERT INTO Statement?

The SQL `INSERT INTO` statement is used to add new rows of data to a table in a database. It's one of the core commands in SQL and is commonly used to populate tables with data. There are two main ways to use the `INSERT INTO` statement:

- By specifying the columns and values explicitly.
- By inserting values for all columns without specifying them.

The method you choose depends on whether you want to insert data into every column or just a subset of columns in the table.

---

## 1. Inserting Data into All Columns (Simple Method)

This method is used when you want to insert data into all columns of a table without specifying column names. We simply provide the values for each column, in the same order that the columns are defined in the table.

### Syntax

```sql
INSERT INTO table_name 
VALUES (value1, value2, value); 
````

### Parameters

* `table_name`: The name of the table where the data will be inserted.
* `value1`, `value2`: The values you want to insert into the respective columns of the table.

### Example

For better understanding, let's look at the SQL `INSERT INTO` statement with examples. Let us first create a table named `Student`.

```sql
CREATE DATABASE StudentDB;
USE StudentDB;

CREATE TABLE Student (
    ROLL_NO INT PRIMARY KEY,
    NAME VARCHAR(50),
    ADDRESS VARCHAR(100),
    PHONE VARCHAR(15),
    AGE INT
);

INSERT INTO Student (ROLL_NO, NAME, ADDRESS, PHONE, AGE) VALUES
(1, 'Ram', 'Delhi', 'XXXXXXXXXX', 18),
(2, 'Ramesh', 'Gurgaon', 'XXXXXXXXXX', 18),
(3, 'Sujit', 'Rohtak', 'XXXXXXXXXX', 20),
(4, 'Suresh', 'Rohtak', 'XXXXXXXXXX', 18);
```

### Output

| ROLL\_NO | NAME   | ADDRESS | PHONE        | AGE |
| -------- | ------ | ------- | ------------ | --- |
| 1        | Ram    | Delhi   | XXXXXXXXXXXX | 18  |
| 2        | RAMESH | GURGAON | XXXXXXXXXXXX | 18  |
| 3        | SUJIT  | ROHTAK  | XXXXXXXXXXXX | 20  |
| 4        | SURESH | ROHTAK  | XXXXXXXXXXXX | 18  |
| 3        | SUJIT  | ROHTAK  | XXXXXXXXXXXX | 20  |
| 2        | RAMESH | GURGAON | XXXXXXXXXXXX | 18  |

If we don’t want to specify the column names (and you’re inserting data into all columns), we can directly insert values in the order they appear in the table structure.

```sql
INSERT INTO Student 
VALUES ('5','HARSH','WEST BENGAL', 'XXXXXXXXXX','19');
```

### Output

| ROLL\_NO | NAME   | ADDRESS     | PHONE        | AGE |
| -------- | ------ | ----------- | ------------ | --- |
| 1        | Ram    | Delhi       | XXXXXXXXXXXX | 18  |
| 2        | RAMESH | GURGAON     | XXXXXXXXXXXX | 18  |
| 3        | SUJIT  | ROHTAK      | XXXXXXXXXXXX | 20  |
| 4        | SURESH | Delhi       | XXXXXXXXXXXX | 18  |
| 3        | SUJIT  | ROHTAK      | XXXXXXXXXXXX | 20  |
| 2        | RAMESH | GURGAON     | XXXXXXXXXXXX | 18  |
| 5        | HARSH  | WEST BENGAL | XXXXXXXXXXXX | 19  |

---

## 2. Inserting Data into Specific Columns (Flexible Method)

In some cases, you might want to insert data into only certain columns, leaving the others empty or with default values. In such cases, we can specify the column names explicitly.

### Syntax

```sql
INSERT INTO table_name (column1, column2, column3) 
VALUES (value1, value2, value); 
```

### Parameters

* `table_name`: Name of the table.
* `column1`, `column2`, ...: Names of the columns.
* `value1`, `value2`, ...: The values for each specified column of the new record.

### Example

Let’s say we only want to insert the student's ID, name, and age into the `Student` table, and leave the address and phone number as `NULL`:

```sql
INSERT INTO Student (ROLL_NO, NAME, Age) 
VALUES ('5', 'PRATIK', 19);
```

### Output

| ROLL\_NO | NAME   | ADDRESS | PHONE | AGE |
| -------- | ------ | ------- | ----- | --- |
| 1        | Ram    | Delhi   | XXXX  | 18  |
| 2        | RAMESH | GURGAON | XXXX  | 18  |
| 3        | SUJIT  | ROHTAK  | XXXX  | 20  |
| 4        | SURESH | Delhi   | XXXX  | 18  |
| 3        | SUJIT  | ROHTAK  | XXXX  | 20  |
| 2        | RAMESH | GURGAON | XXXX  | 18  |
| 5        | PRATIK | NULL    | NULL  | 19  |

> **Note**: Columns not included in the `INSERT` statement are filled with default values (typically `NULL`).

---

## Inserting Multiple Rows at Once

Instead of running multiple `INSERT INTO` commands, you can insert multiple rows into a table in a single query. This is more efficient and reduces the number of database operations.

### Syntax

```sql
INSERT INTO table_name (column1, column2, ...)
VALUES
(value1, value2, ...),
(value1, value2, ...),
(value1, value2, ...);
```

### Example

```sql
INSERT INTO Student (ROLL_NO, NAME, AGE, ADDRESS, PHONE) 
VALUES
(6, 'Amit Kumar', 15, 'Delhi', 'XXXXXXXXXX'),
(7, 'Gauri Rao', 18, 'Bangalore', 'XXXXXXXXXX'),
(8, 'Manav Bhatt', 17, 'New Delhi', 'XXXXXXXXXX'),
(9, 'Riya Kapoor', 10, 'Udaipur', 'XXXXXXXXXX');
```

### Output

| ROLL\_NO | NAME        | ADDRESS   | PHONE        | AGE |
| -------- | ----------- | --------- | ------------ | --- |
| ...      | ...         | ...       | ...          | ... |
| 6        | Amit Kumar  | Delhi     | XXXXXXXXXXXX | 15  |
| 7        | Gauri Rao   | Bangalore | XXXXXXXXXXXX | 18  |
| 8        | Manav Bhatt | New Delhi | XXXXXXXXXXXX | 17  |
| 9        | Riya Kapoor | Udaipur   | XXXXXXXXXXXX | 10  |

> **Explanation**: This method is faster than running multiple individual `INSERT INTO` commands.
> If you're inserting more than 1000 rows, consider using **bulk insert** or multiple insert statements for efficiency.

---

## Inserting Data from One Table into Another Table

We can also copy data from one table into another table using the `INSERT INTO SELECT` statement.

### Syntax 1: Insert All Columns from Another Table

```sql
INSERT INTO target_table
SELECT * FROM source_table;
```

### Example

```sql
INSERT INTO Students
SELECT * FROM OldStudents;
```

---

### Syntax 2: Insert Specific Columns from Another Table

```sql
INSERT INTO target_table (col1, col2, ...)
SELECT col1, col2, ...
FROM source_table;
```

### Example

```sql
INSERT INTO Students (Name, Age)
SELECT Name, Age
FROM OldStudents;
```

---

### Syntax 3: Insert Specific Rows Based on Condition

```sql
INSERT INTO target_table
SELECT * FROM source_table
WHERE condition;
```

### Example

```sql
INSERT INTO Students
SELECT * FROM OldStudents
WHERE Age > 20;
```

---

## Important Points About SQL INSERT INTO Statement

* **Multiple Inserts**: You can insert multiple rows at once by separating each set of values with commas.
* **NULL Values**: If you don't insert data into a column, it will typically be set to `NULL` unless the column has a default value.
* **Order of Columns**: When using the simple `INSERT INTO` syntax without specifying column names, the values must be in the exact same order as the columns are defined in the table.
* **Default Values**: Columns not mentioned in the `INSERT INTO` statement will be filled with their default values (often `NULL`).
* **Efficiency**: Inserting multiple rows at once is much more efficient than doing it one by one.

---

## Conclusion

Overall, `INSERT INTO` statement is an essential feature in SQL for adding new data to tables. Whether you're adding a single row or multiple rows, specifying column names or copying data from another table, `INSERT INTO` provides the necessary flexibility. Understanding its syntax and usage is crucial for efficient database management and data manipulation.

---

