
---

# SQL | GROUP BY

The SQL `GROUP BY` clause is a powerful tool used to organize data into groups based on shared values in one or more columns. It's most often used with aggregate functions like `SUM`, `COUNT`, `AVG`, `MIN`, and `MAX` to perform summary operations on each group, helping us extract meaningful insights from large datasets.

---

## 📌 What is GROUP BY Clause in SQL?

The `GROUP BY` statement in SQL is used to arrange identical data into groups based on specified columns. If a particular column has the same values in multiple rows, the `GROUP BY` clause will group these rows together. It’s commonly used with aggregate functions to calculate totals or averages per group.

### ✅ Key Points About GROUP BY:
- `GROUP BY` clause is used with the `SELECT` statement.
- In the query, the `GROUP BY` clause is placed **after the WHERE** clause.
- It is placed **before the ORDER BY** clause if used.
- It is also placed **before the HAVING** clause.
- Place conditions on aggregated data using the **HAVING** clause.

---

## 📚 Syntax

```sql
SELECT column1, function_name(column2)
FROM table_name
GROUP BY column1, column2;
````

### 🔑 Key Terms

* `function_name`: Name of the function used (e.g., `SUM()`, `AVG()`).
* `table_name`: Name of the table.
* `condition`: Filtering condition (used in `WHERE` or `HAVING` clause).

---

## 🧪 Examples of GROUP BY in SQL

### 👨‍💼 Employee Table

```sql
CREATE TABLE emp (
  emp_no INT PRIMARY KEY,
  name VARCHAR(50),
  sal DECIMAL(10,2),
  age INT
);

INSERT INTO emp (emp_no, name, sal, age) VALUES
(1, 'Aarav', 50000.00, 25),
(2, 'Aditi', 60000.50, 30),
(3, 'Aarav', 75000.75, 35),
(4, 'Anjali', 45000.25, 28),
(5, 'Chetan', 80000.00, 32),
(6, 'Divya', 65000.00, 27),
(7, 'Gaurav', 55000.50, 29),
(8, 'Divya', 72000.75, 31),
(9, 'Gaurav', 48000.25, 26),
(10, 'Divya', 83000.00, 33);
```

### 👩‍🎓 Student Table

```sql
CREATE TABLE student (
  name VARCHAR(50),
  year INT,
  subject VARCHAR(50)
);

INSERT INTO student (name, year, subject) VALUES
('Alice', 1, 'Mathematics'),
('Bob', 2, 'English'),
('Charlie', 3, 'Science'),
('David', 1, 'Mathematics'),
('Emily', 2, 'English'),
('Frank', 3, 'Science');
```

---

### 🧩 Example 1: Group By Single Column

**Query** – Calculating the Total Salary of each Employee by their name:

```sql
SELECT name, SUM(sal) 
FROM emp 
GROUP BY name;
```

**Explanation**:
This groups all records with the same name and calculates the total salary per group using `SUM()`.
Names like **Aarav**, **Divya**, and **Gaurav** appear more than once and are grouped accordingly.

---

### 🧩 Example 2: Group By Multiple Columns

**Query** – Count the number of students by both subject and year:

```sql
SELECT subject, year, COUNT(*) 
FROM student 
GROUP BY subject, year;
```

**Explanation**:
This groups records that share the same combination of **subject** and **year**, then counts how many students fall into each group.
Groups: `(English, 2)`, `(Mathematics, 1)`, `(Science, 3)`.

---

## 🔍 HAVING Clause in GROUP BY Clause

The `WHERE` clause cannot be used to filter groups, as it works on individual rows. To apply a condition **after grouping**, use the `HAVING` clause.

### 💡 Syntax:

```sql
SELECT column1, function_name(column2)
FROM table_name
WHERE condition
GROUP BY column1, column2
HAVING condition
ORDER BY column1, column2;
```

### 🧩 Example: Filter Groups Using HAVING

**Query** – Show only employees whose total salary is greater than 50,000:

```sql
SELECT name, SUM(sal) 
FROM emp 
GROUP BY name 
HAVING SUM(sal) > 50000;
```

**Explanation**:
Only names with total salaries exceeding 50,000 will appear in the result set. For instance, **Anjali** (if her total is below 50,000) will be excluded.

---

## 🧠 Conclusion

The `GROUP BY` function in SQL organizes identical data into groups, enabling aggregate analysis on each group. It is commonly used with functions like `SUM()`, `COUNT()`, `AVG()`, etc., to summarize data efficiently.

* Use `GROUP BY` for grouped analysis.
* Use `HAVING` to filter results after aggregation.
* Works with single or multiple columns.

**GROUP BY** is a versatile and essential SQL tool for data summarization and reporting.

---
