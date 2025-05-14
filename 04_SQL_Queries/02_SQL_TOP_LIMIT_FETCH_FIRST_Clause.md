
---

````markdown
# SQL TOP, LIMIT, FETCH FIRST Clause

The `TOP`, `LIMIT`, and `FETCH FIRST` clauses in SQL are used to retrieve a specific number of records from a table. These are especially useful when working with large datasets to enhance performance and manageability.

---

## 📌 Overview

These clauses limit the number of rows returned by a query and are supported by different SQL database systems:

- **TOP**: SQL Server, MS Access
- **LIMIT**: MySQL, PostgreSQL, SQLite
- **FETCH FIRST**: Oracle, DB2, PostgreSQL, SQL Server (via OFFSET-FETCH)

---

## 🔹 SQL SELECT TOP Clause

### ✅ Syntax
```sql
SELECT column1, column2, ... TOP count
FROM table_name
[WHERE conditions]
[ORDER BY expression [ASC | DESC]];
````

### ✅ Example Table

```sql
CREATE TABLE Employee (
   EmpId INTEGER PRIMARY KEY, 
   EmpName VARCHAR(225) NOT NULL,  
   Email VARCHAR(225) NOT NULL,   
   Address VARCHAR(225) NOT NULL,
   Age INT NOT NULL,
   Salary MONEY NOT NULL
);

INSERT INTO Employee (EmpId, EmpName, Email, Address, Age, Salary)
VALUES 
(1, 'Shubham', 'shubham@example.com', 'India', 23, 50000.00),
(2, 'Aman', 'aman@example.com', 'Australia', 21, 45000.00),
(3, 'Naveen', 'naveen@example.com', 'Sri Lanka', 24, 55000.00),
(4, 'Aditya', 'aditya@example.com', 'Austria', 21, 42000.00),
(5, 'Nishant Saluja', 'nishant@example.com', 'Spain', 22, 48000.00);
```

### 📘 Example 1: Basic TOP Clause

```sql
SELECT TOP 4 * FROM Employee;
```

### 📘 Example 2: TOP with ORDER BY

```sql
SELECT TOP 4 * FROM Employee ORDER BY Salary DESC;
```

### 📘 Example 3: TOP with WHERE

```sql
SELECT TOP 2 * FROM Employee WHERE Salary > 2000 ORDER BY Salary;
```

### 📘 Example 4: TOP PERCENT

```sql
SELECT TOP 50 PERCENT * FROM Employee;
```

### 📘 Example 5: TOP PERCENT with WHERE

```sql
SELECT TOP 50 PERCENT * FROM Employee WHERE Salary < 50000;
```

---

## 🔹 SQL LIMIT Clause

Supported in MySQL, PostgreSQL, and SQLite.

### ✅ Example Table (Same as above)

### 📘 Example 1: Basic LIMIT

```sql
SELECT * FROM Employee WHERE Salary = 45000 LIMIT 2;
```

### 📘 Example 2: LIMIT with WHERE

```sql
SELECT * FROM Employee WHERE Salary = 45000 LIMIT 2;
```

### 📘 Example 3: LIMIT with OFFSET

```sql
SELECT * FROM Employee LIMIT 2 OFFSET 2;
```

---

## 🔹 SQL FETCH FIRST Clause

Supported in DB2, Oracle, PostgreSQL, and SQL Server (OFFSET-FETCH).

### ✅ Syntax

```sql
SELECT columns FROM table WHERE condition FETCH FIRST n ROWS ONLY;
```

### 📘 Example 1: Basic FETCH FIRST

```sql
SELECT * FROM Employee FETCH FIRST 3 ROWS ONLY;
```

### 📘 Example 2: FETCH FIRST PERCENT (Workaround)

```sql
SELECT * 
FROM Employee 
FETCH FIRST (SELECT CEIL(COUNT(*) / 2) FROM Employee) ROWS ONLY;
```

### 📘 Example 3: FETCH FIRST with WHERE

```sql
SELECT * 
FROM Employee 
WHERE Salary = 45000 
FETCH FIRST 1 ROW ONLY;
```

---

## 🧠 Conclusion

* **TOP**, **LIMIT**, and **FETCH FIRST** serve the same purpose: limiting result rows.
* Not all clauses are supported across all SQL database systems.
* Always verify DBMS compatibility before using these clauses.

| Clause      | Supported By                        |
| ----------- | ----------------------------------- |
| TOP         | SQL Server, MS Access               |
| LIMIT       | MySQL, PostgreSQL, SQLite           |
| FETCH FIRST | Oracle, DB2, PostgreSQL, SQL Server |

---

## 📚 Related Topics

* SQL `ORDER BY` Clause
* SQL `WHERE` Clause
* SQL `OFFSET`
* SQL `GROUP BY`, `HAVING`

---
