
---

# SQL MIN() and MAX() Functions

The SQL `MIN()` and `MAX()` functions are essential aggregate functions used for data analysis. They allow you to extract the minimum and maximum values from a specified column, respectively. These functions are invaluable when working with numerical, string, or date-based data.

---

## 📌 SQL MIN() Function

The `MIN()` function returns the **smallest** value in a column. It works with numbers, strings, and date data types.

It can also be used with the `DISTINCT` keyword to find the minimum value among unique values.

### ✅ Syntax:
```sql
SELECT MIN(column_name)
FROM table_name
WHERE condition;
````

---

## 📌 SQL MAX() Function

The `MAX()` function returns the **largest** value in a column. It supports numeric, string, and date types.

It can be used alongside other SQL clauses such as `GROUP BY`, `HAVING`, and subqueries for advanced analysis.

### ✅ Syntax:

```sql
SELECT MAX(column_name)
FROM table_name
WHERE condition;
```

---

## 💡 Sample Table

We will use the following `Customer` table in the examples.

### 🛠️ Create Table:

```sql
CREATE TABLE Customer (
    CustomerID INT PRIMARY KEY,
    CustomerName VARCHAR(50),
    LastName VARCHAR(50),
    Country VARCHAR(50),
    Age INT(2),
    Phone INT(10)
);
```

### 📥 Insert Sample Data:

```sql
INSERT INTO Customer (CustomerID, CustomerName, LastName, Country, Age, Phone)
VALUES 
(1, 'Shubham', 'Thakur', 'India', 23, 'xxxxxxxxxx'),
(2, 'Aman', 'Chopra', 'Australia', 21, 'xxxxxxxxxx'),
(3, 'Naveen', 'Tulasi', 'Sri Lanka', 24, 'xxxxxxxxxx'),
(4, 'Aditya', 'Arpan', 'Austria', 21, 'xxxxxxxxxx'),
(5, 'Nishant. Salchichas S.A.', 'Jain', 'Spain', 22, 'xxxxxxxxxx');
```

---

## 📘 Examples

### 📍 Example 1: Using `MIN()` Function

Get the minimum age from the `Customer` table.

```sql
SELECT MIN(Age) FROM Customer;
```

**Output:**

```
21
```

---

### 📍 Example 2: Using `MAX()` Function

Get the maximum age from the `Customer` table.

```sql
SELECT MAX(Age) FROM Customer;
```

**Output:**

```
24
```

---

### 📍 Example 3: Use MIN() or MAX() with Other Columns

Fetch customer name with minimum age.

```sql
SELECT CustomerName, MIN(Age) AS min_age 
FROM Customer;
```

**Output:**

```
CustomerName | min_age
-------------|---------
Shubham      |   21
```

> Note: Since MIN is applied across the whole table, `CustomerName` in SELECT is not grouped, so actual DBs may throw error or pick a random row. Use GROUP BY for accurate results.

---

### 📍 Example 4: Use MIN() or MAX() in the HAVING Clause

Fetch maximum age but only if the minimum age is greater than 22.

```sql
SELECT CustomerName, MAX(Age) AS max_age 
FROM Customer
HAVING MIN(Age) > 22;
```

**Output:**

```
CustomerName | max_age
-------------|---------
Naveen       |   24
```

> Note: For correct behavior, you often need `GROUP BY` when combining `HAVING` with aggregates.

---

## 🧠 Important Notes

* `MIN()` returns the **minimum** value, `MAX()` returns the **maximum** value in a column.
* Both work with numbers, strings, and date types.
* They are **aggregate functions**, meaning they operate on sets of rows.
* Often used with `GROUP BY`, `HAVING`, and **subqueries** for advanced reporting.
* They are powerful tools for **data manipulation and analysis**.

---
