
---

# How to Compare Two Queries in SQL

## Introduction to Queries in SQL

A query in SQL can be either a request for data results from your database or an action on the data, or both. A query may answer a straightforward question, perform calculations, combine data from multiple tables, or add, modify, or delete data from the database.

---

## Creating a Database

You can create a new SQL database using the `CREATE DATABASE` command.

**Syntax:**

```sql
CREATE DATABASE db_name;
```

---

## Creating a Table in a Database

Use the `CREATE TABLE` command to create a new table in a database.

**Syntax:**

```sql
CREATE TABLE table_name (
   col1 datatype,
   col2 datatype, 
   col3 datatype
);
```

---

## Inserting Values into a Table

Use the `INSERT INTO` command to insert data into a table.

**Syntax:**

```sql
INSERT INTO table_name
VALUES (value1, value2, value3);
```

---

## Example: Create Database, Table, and Insert Data

```sql
CREATE DATABASE myDatabase;

CREATE TABLE myTable
(
  Pid int,
  FName varchar(255),
  LName varchar(255),
  Adrs varchar(255),
  District varchar(255)
);

INSERT INTO myTable (Pid, FName, LName, Adrs, District)
VALUES ('1', 'Krishna', 'Kripa', 'Jansa', 'Varanasi');
```

**Output:**

| Pid | FName   | LName | Adrs  | District |
| --- | ------- | ----- | ----- | -------- |
| 1   | Krishna | Kripa | Jansa | Varanasi |

---

## Comparison of Queries

Suppose you have two similar tables in different databases and want to find the differences. Below is a script to create two sample databases with tables and data:

```sql
CREATE DATABASE myDatabase1;
GO
USE myDatabase1;
GO

CREATE TABLE myTable
(
  Aid int,
  Atype varchar(10),
  Acost varchar(10)
);
GO

INSERT INTO myTable (Aid, Atype, Acost)
VALUES ('001', '1', '40'),
       ('002', '2', '80'),
       ('003', '3', '120');
GO


CREATE DATABASE myDatabase2;
GO
USE myDatabase2;
GO

CREATE TABLE myTable
(
  Aid int,
  Atype varchar(10),
  Acost varchar(10)
);
GO

INSERT INTO myTable (Aid, Atype, Acost)
VALUES ('001', '1', '40'),
       ('002', '2', '80'),
       ('003', '3', '120'),
       ('004', '4', '160');
GO
```

---

## Output of the Databases

### `myDatabase1.myTable`

| Aid | Atype | Acost |
| --- | ----- | ----- |
| 001 | 1     | 40    |
| 002 | 2     | 80    |
| 003 | 3     | 120   |

### `myDatabase2.myTable`

| Aid | Atype | Acost |
| --- | ----- | ----- |
| 001 | 1     | 40    |
| 002 | 2     | 80    |
| 003 | 3     | 120   |
| 004 | 4     | 160   |

---

## Compare SQL Queries Using the EXCEPT Keyword

The `EXCEPT` keyword is used to show the difference between two tables. It returns rows from the first query that are not present in the second query.

Run the following query to find rows in `myDatabase2.myTable` that are not in `myDatabase1.myTable`:

```sql
SELECT * FROM myDatabase2.myTable
EXCEPT
SELECT * FROM myDatabase1.myTable;
```

**Output:**

| Aid | Atype | Acost |
| --- | ----- | ----- |
| 004 | 4     | 160   |

---

# Summary

* Use `CREATE DATABASE` and `CREATE TABLE` to set up your databases and tables.
* Insert data with `INSERT INTO`.
* Use the `EXCEPT` keyword to compare two queries and find differences between tables.
* This is useful for data auditing, ensuring data consistency across databases, or troubleshooting.

---
