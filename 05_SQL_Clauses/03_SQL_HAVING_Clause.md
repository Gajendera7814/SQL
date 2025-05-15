
---

# SQL HAVING Clause with Examples

---

## 📌 Introduction

The `HAVING` clause in SQL is used to **filter query results based on aggregate functions**. Unlike the `WHERE` clause, which filters **individual rows before grouping**, the `HAVING` clause filters **groups of data after aggregation**. It is commonly used with functions like `SUM()`, `AVG()`, `COUNT()`, `MAX()`, and `MIN()`.

---

## 📘 What is the SQL HAVING Clause?

The `HAVING` clause is used to **filter the result of the `GROUP BY` statement** based on specified conditions. It allows filtering **grouped data using Boolean conditions** (`AND`, `OR`). It was introduced because the `WHERE` clause **cannot be used with aggregate functions**.

Similar to `WHERE`, it applies conditions—but specifically **after aggregation**. When we need to **filter aggregated results**, the `HAVING` clause is the correct tool.

---

## ✨ Key Features of the HAVING Clause

* ✅ Used to filter grouped data based on aggregate functions.
* ✅ Works with Boolean conditions (`AND`, `OR`).
* ✅ Cannot be used without `GROUP BY` unless an aggregate function is present.
* ✅ Must be placed **after the `GROUP BY` clause** and **before the `ORDER BY` clause** (if used).
* ✅ Helps generate summary reports from large datasets.

---

## 🧾 Syntax

```sql
SELECT column_name, AGGREGATE_FUNCTION(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

Here, `AGGREGATE_FUNCTION` could be `SUM()`, `AVG()`, etc.

---

## 🧪 SQL HAVING Clause Examples

---

### ✅ Setup

First, create a database called `Company`, then create a table named `Employee` and insert the sample data.

```sql
-- Create the Employee table with appropriate data types
CREATE TABLE Employee (
  EmployeeId int,
  Name varchar(50),
  Gender varchar(10),
  Salary int,
  Department varchar(20),
  Experience int -- Changed to int for years of experience
);

-- Insert multiple rows into the Employee table in a single query
INSERT INTO Employee (EmployeeId, Name, Gender, Salary, Department, Experience)
VALUES 
  (5, 'Priya Sharma', 'Female', 45000, 'IT', 2),
  (6, 'Rahul Patel', 'Male', 65000, 'Sales', 5),
  (7, 'Nisha Gupta', 'Female', 55000, 'Marketing', 4),
  (8, 'Vikram Singh', 'Male', 75000, 'Finance', 7),
  (9, 'Aarti Desai', 'Female', 50000, 'IT', 3);

-- View the data
SELECT * FROM Employee;
```

---

### 🔹 Example 1: Using HAVING to Filter Aggregated Results

This query will return the **sum of salaries** for each department.

```sql
SELECT Department, SUM(Salary) AS Salary
FROM Employee
GROUP BY Department;
```

To display only departments where the **sum of salaries is ≥ 50,000**, use `HAVING`:

```sql
SELECT Department, SUM(Salary) AS Salary
FROM Employee
GROUP BY Department
HAVING SUM(Salary) >= 50000;
```

---

### 🔹 Example 2: Using HAVING with Multiple Conditions

Get departments where:

* Total salary is ≥ 50,000
* AND average salary is > 55,000

```sql
SELECT Department, SUM(Salary) AS Total_Salary, AVG(Salary) AS Average_Salary
FROM Employee
GROUP BY Department
HAVING SUM(Salary) >= 50000 AND AVG(Salary) > 55000;
```

#### Output:

| Department | Total\_Salary | Average\_Salary |
| ---------- | ------------- | --------------- |
| Finance    | 75000         | 75000           |
| Sales      | 65000         | 65000           |

---

### 🔹 Example 3: Using HAVING with COUNT()

Find departments that have **more than two employees**:

```sql
SELECT Department, COUNT(EmployeeId) AS Employee_Count
FROM Employee
GROUP BY Department
HAVING COUNT(EmployeeId) >= 2;
```

#### Output:

| Department | Employee\_Count |
| ---------- | --------------- |
| IT         | 2               |

---

### 🔹 Example 4: Using HAVING with AVG()

Display departments where the **average salary** is **greater than 50,000**:

```sql
SELECT Department, AVG(Salary) AS Average_Salary
FROM Employee
GROUP BY Department
HAVING AVG(Salary) > 50000;
```

#### Output:

| Department | Average\_Salary |
| ---------- | --------------- |
| Finance    | 75000           |
| Marketing  | 55000           |
| Sales      | 65000           |

---

## ⚖️ HAVING vs WHERE

| Feature         | HAVING Clause                              | WHERE Clause                         |
| --------------- | ------------------------------------------ | ------------------------------------ |
| Execution       | Applies **after** aggregation (`GROUP BY`) | Applies **before** grouping          |
| Usage           | Used **with aggregate functions**          | Used **without aggregate functions** |
| Filter Type     | Filters **groups of rows**                 | Filters **individual rows**          |
| Execution Order | Executed **after `GROUP BY`**              | Executed **before `GROUP BY`**       |

---

## 🧠 Conclusion

The **HAVING clause** is an essential SQL tool for **filtering grouped results based on aggregated data**. While the `WHERE` clause filters individual rows, the `HAVING` clause lets us apply conditions to **aggregated/grouped data**, making it crucial for **advanced analytics** and **summary reporting**.

---
