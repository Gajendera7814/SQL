
---

# SQL SELECT FIRST, TOP, LIMIT, and FETCH FIRST Clauses

---

## 📌 Overview

The `SQL SELECT FIRST`, `TOP`, `LIMIT`, and `FETCH FIRST` clauses are used to retrieve a specific number of rows from a table. These are extremely useful when working with large datasets to make queries more efficient and manageable. However, **each clause is supported by different database management systems (DBMS)**.

---

## 🧠 What You’ll Learn

- Purpose of each clause
- Syntax and examples
- Differences in support across SQL databases
- Use-cases and implementation scenarios

---

## 🏷️ Clause Summary

| Clause        | Supported DBMS                           | Description                                             |
|---------------|------------------------------------------|---------------------------------------------------------|
| `SELECT TOP`  | SQL Server, MS Access                    | Returns a fixed number or percentage of rows            |
| `LIMIT`       | MySQL, PostgreSQL, SQLite                | Limits the number of results returned                   |
| `FETCH FIRST` | Oracle, DB2, PostgreSQL, SQL Server (2012+) | Standard SQL, retrieves first n rows                  |
| `SELECT FIRST`| MS Access                                | Returns the first row from the table                    |

---

## 🔸 SELECT TOP Clause

Used to limit the number of records returned in **SQL Server** and **MS Access**.

### 🔹 Syntax

```sql
SELECT TOP (number) column1, column2, ...
FROM table_name
[WHERE conditions]
[ORDER BY expression [ASC|DESC]];
````

### 🔹 Example Table

```sql
CREATE TABLE Employee (
   EmpId INTEGER PRIMARY KEY, 
   EmpName VARCHAR(225) NOT NULL,  
   Email VARCHAR(225) NOT NULL,   
   Address VARCHAR(225) NOT NULL,
   Age INT NOT NULL,
   Salary MONEY NOT NULL
);
```

### 🔹 Insert Data

```sql
INSERT INTO Employee (EmpId, EmpName, Email, Address, Age, Salary)
VALUES 
(1, 'Shubham', 'shubham@example.com', 'India', 23, 50000.00),
(2, 'Aman', 'aman@example.com', 'Australia', 21, 45000.00),
(3, 'Naveen', 'naveen@example.com', 'Sri Lanka', 24, 55000.00),
(4, 'Aditya', 'aditya@example.com', 'Austria', 21, 42000.00),
(5, 'Nishant Saluja', 'nishant@example.com', 'Spain', 22, 48000.00);
```

### 🔹 Examples

* **TOP N Records**

```sql
SELECT TOP 4 * FROM Employee;
```

* **TOP N with ORDER BY**

```sql
SELECT TOP 4 * FROM Employee ORDER BY Salary DESC;
```

* **TOP N with WHERE**

```sql
SELECT TOP 2 * FROM Employee WHERE Salary > 2000 ORDER BY Salary;
```

* **TOP PERCENT**

```sql
SELECT TOP 50 PERCENT * FROM Employee;
```

* **TOP PERCENT with WHERE**

```sql
SELECT TOP 50 PERCENT * FROM Employee WHERE Salary < 50000;
```

---

## 🔸 SQL LIMIT Clause

Used in **MySQL**, **PostgreSQL**, and **SQLite** to restrict the number of rows returned.

### 🔹 Syntax

```sql
SELECT column1, column2
FROM table
WHERE condition
LIMIT number
[OFFSET offset];
```

### 🔹 Examples

* **LIMIT with WHERE**

```sql
SELECT * FROM Employee WHERE Salary = 45000 LIMIT 2;
```

* **LIMIT with OFFSET**

```sql
SELECT * FROM Employee LIMIT 2 OFFSET 2;
```

---

## 🔸 SQL FETCH FIRST Clause

Used to fetch the first `n` rows from a result set. Supported in **DB2**, **Oracle**, **PostgreSQL**, **SQL Server 2012+**.

### 🔹 Syntax

```sql
SELECT column1, column2
FROM table
[WHERE condition]
ORDER BY column
FETCH FIRST n ROWS ONLY;
```

### 🔹 Examples

* **Basic FETCH FIRST**

```sql
SELECT * FROM Employee FETCH FIRST 3 ROWS ONLY;
```

* **FETCH FIRST with Percentage Logic**

```sql
SELECT *
FROM Employee
FETCH FIRST (SELECT CEIL(COUNT(*) / 2) FROM Employee) ROWS ONLY;
```

* **FETCH FIRST with WHERE**

```sql
SELECT * FROM Employee WHERE Salary = 45000 FETCH FIRST 1 ROW ONLY;
```

---

## 🔸 SQL SELECT FIRST Clause

Primarily used in **MS Access** to retrieve the first row of a result set.

### 🔹 Syntax

```sql
SELECT FIRST(columnName) FROM tableName;
```

### 🔹 Example Table: Stationary

| Name     | Price | Quantity |
| -------- | ----- | -------- |
| Pen      | 1.5   | 100      |
| Pencil   | 1.0   | 150      |
| Notebook | 3.0   | 200      |

### 🔹 Example Queries

* **Basic SELECT FIRST**

```sql
SELECT FIRST(Name) AS First_name FROM Stationary;
```

* **With ORDER BY**

```sql
SELECT FIRST(Name) AS First_name 
FROM Stationary 
ORDER BY Price ASC;
```

---

## 🛠️ Implementation Steps for MS Access

1. **Create Database**

```sql
CREATE DATABASE GFG;
```

2. **Use Database**

```sql
USE GFG;
```

3. **Create Table**

```sql
CREATE TABLE first (
  ID INT PRIMARY KEY IDENTITY(1,1),
  Name VARCHAR(20) NOT NULL,
  Age INT NOT NULL,
  Dept VARCHAR(20) NOT NULL
);
```

4. **Insert Records**

```sql
INSERT INTO [dbo].[first] (Name, Age, Dept) VALUES ('Devesh', 20, 'CSE');
INSERT INTO [dbo].[first] (Name, Age, Dept) VALUES ('Aditya', 19, 'BT');
INSERT INTO [dbo].[first] (Name, Age, Dept) VALUES ('Megha', 20, 'CSE');
```

5. **Query Using SELECT FIRST Alternative**

```sql
SELECT TOP 1 Name FROM first;
```

---

## ✅ Key Points

* `SELECT FIRST` is **not standard SQL** and is **only supported in MS Access**.
* For most modern DBMS, use `TOP`, `LIMIT`, or `FETCH FIRST`.
* These clauses improve performance and manageability on large datasets.
* Always check DBMS documentation before using these clauses.

---

## 🧾 Conclusion

`SQL SELECT FIRST`, `TOP`, `LIMIT`, and `FETCH FIRST` clauses serve the same general purpose: to **limit the number of rows** returned in a query. However, each has its own syntax and is supported by different SQL database systems.

---
