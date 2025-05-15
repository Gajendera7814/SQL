
---

# 📅 SQL - SELECT DATE

SQL (Structured Query Language) can work with **datetime data types**.  
`SELECT DATE` is an important concept when retrieving records that filter data based on **date**.

Whether you work with:

- Employee records  
- Transaction logs  
- Product sales  

...retrieving and modifying date data is often crucial for your SQL queries.

---

## 🎯 Purpose

This article explains how to **retrieve and manipulate date values** using SQL queries — including:

- `DATE`
- `DATETIME`
- `TIMESTAMP`
- Related SQL functions

---

## 🧾 SQL SELECT DATE

In SQL, date and time values are stored using various types:

- `DATE`
- `DATETIME`
- `TIME`
- `TIMESTAMP`
- `YEAR`

These vary based on use case and database system (MySQL, PostgreSQL, etc.).

To retrieve records by date, we use the `SELECT` statement.

### ✅ Syntax

```sql
SELECT column_name
FROM table_name
WHERE date_column = 'YYYY-MM-DD';
````

**Parameters:**

* `column_name`: The column to retrieve
* `table_name`: The table containing the date
* `date_column`: The column that holds date values
* `'YYYY-MM-DD'`: Date to filter in standard format

---

## 🧪 Example: SQL SELECT DATE

Let’s create a sample table with a `DATE` column.

### 👨‍💼 Employee Table

```sql
CREATE TABLE Employee (
    EmpID INT,
    FirstName VARCHAR(255),
    LastName VARCHAR(255),
    HireDate DATE
);
```

### 📝 Inserting Data

```sql
INSERT INTO Employee (EmpID, FirstName, LastName, HireDate)
VALUES
(1, 'John', 'Doe', '2022-01-15'),
(2, 'Jane', 'Smith', '2021-06-30'),
(3, 'Alice', 'Johnson', '2020-08-25');
```

**Resulting Table:**

| EmpID | FirstName | LastName | HireDate   |
| ----- | --------- | -------- | ---------- |
| 1     | John      | Doe      | 2022-01-15 |
| 2     | Jane      | Smith    | 2021-06-30 |
| 3     | Alice     | Johnson  | 2020-08-25 |

---

## 📅 Example: Select Employees Hired on a Specific Date

```sql
SELECT FirstName, LastName, HireDate
FROM Employee
WHERE HireDate = '2022-01-15';
```

**Output:**

| FirstName | LastName | HireDate   |
| --------- | -------- | ---------- |
| John      | Doe      | 2022-01-15 |

This query retrieves employees who were hired on **2022-01-15**.

---

## 🛠️ Using SQL Date Functions

SQL offers functions to extract parts of date values:

* `YEAR()`: Extracts the year
* `MONTH()`: Extracts the month
* `DAY()`: Extracts the day

---

### 📘 Example 1: Select Employees Hired in a Specific Year

```sql
SELECT FirstName, LastName, HireDate
FROM Employee
WHERE YEAR(HireDate) = 2022;
```

**Output:**

| FirstName | LastName | HireDate   |
| --------- | -------- | ---------- |
| John      | Doe      | 2022-01-15 |

This retrieves all employees hired in the year **2022**.

---

### 📘 Example 2: Select Employees Hired in a Specific Month

```sql
SELECT FirstName, LastName, HireDate
FROM Employee
WHERE MONTH(HireDate) = 6;
```

**Output:**

| FirstName | LastName | HireDate   |
| --------- | -------- | ---------- |
| Jane      | Smith    | 2021-06-30 |

---

## 🧠 Advanced Date Functions

SQL also provides **advanced functions**:

* `CURDATE()` → Current date (no time)
* `NOW()` → Current date **and** time

---

### 📘 Example: Employees Hired Before Today

```sql
SELECT FirstName, LastName, HireDate
FROM Employee
WHERE HireDate < CURDATE();
```

This query retrieves all employees hired **before today’s date**.

---

## 🔄 Using BETWEEN for Date Ranges

The `BETWEEN` operator allows filtering **within a date range**.
This is useful for:

* Quarterly reports
* Monthly logs
* Seasonal trends

---

### 📘 Example: Employees Hired Between Two Dates

```sql
SELECT FirstName, LastName, HireDate
FROM Employee
WHERE HireDate BETWEEN '2021-01-01' AND '2022-01-01';
```

**Output:**

| FirstName | LastName | HireDate   |
| --------- | -------- | ---------- |
| Jane      | Smith    | 2021-06-30 |

---

## ✅ Conclusion

The `SELECT DATE` feature in SQL is essential for working with **time-sensitive data**.

By learning how to use:

* `DATE`, `DATETIME`, `TIMESTAMP`
* Date functions like `YEAR()`, `MONTH()`, `DAY()`
* `CURDATE()`, `NOW()`, `BETWEEN`

...you can write efficient and flexible queries.

Whether you're managing **sales**, **employees**, or **events**, mastering SQL date functions helps you extract the exact data you need.

---
