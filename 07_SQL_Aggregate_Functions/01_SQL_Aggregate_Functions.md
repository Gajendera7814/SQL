
---

# SQL Aggregate Functions

SQL Aggregate Functions are used to perform calculations on a set of rows and return a single value. These functions are particularly useful when we need to summarize, analyze, or group large datasets in SQL databases. Whether you're working with sales data, employee records, or product inventories, aggregate functions help us derive meaningful insights.

They are often used with the `GROUP BY` clause in SQL to summarize data for each group. Commonly used aggregate functions include `COUNT()`, `SUM()`, `AVG()`, `MIN()`, and `MAX()`.

---

## What Are SQL Aggregate Functions?

SQL Aggregate Functions are used to perform calculations on multiple rows of data and return a single summarized result. These functions are typically used with the `GROUP BY` clause to organize data into groups, where we can then perform calculations like summing, averaging, or counting. Aggregate functions allow you to make sense of large datasets by collapsing them into meaningful summaries.

### Key Features of SQL Aggregate Functions:

- **Operate on groups of rows**: They work on a set of rows and return a single value.  
- **Ignore NULLs**: Most aggregate functions ignore NULL values, except for `COUNT(*)`.  
- **Used with GROUP BY**: To perform calculations on grouped data, you often use aggregate functions with `GROUP BY`.  
- **Can be combined with other SQL clauses**: Aggregate functions can be used alongside `HAVING`, `ORDER BY`, and other SQL clauses to filter or sort results.

---

## Commonly Used SQL Aggregate Functions

### 1. `COUNT()`

The `COUNT()` function returns the number of rows that match a given condition or are present in a column.

- `COUNT(*)`: Counts all rows.  
- `COUNT(column_name)`: Counts non-NULL values in the specified column.  
- `COUNT(DISTINCT column_name)`: Counts unique non-NULL values in the column.

**Examples:**

```sql
-- Total number of records in the table
SELECT COUNT(*) AS TotalRecords FROM Employee;

-- Count of non-NULL salaries
SELECT COUNT(Salary) AS NonNullSalaries FROM Employee;

-- Count of unique non-NULL salaries
SELECT COUNT(DISTINCT Salary) AS UniqueSalaries FROM Employee;
````

---

### 2. `SUM()`

The `SUM()` function calculates the total sum of a numeric column.

* `SUM(column_name)`: Returns the total sum of all non-NULL values in a column.

**Examples:**

```sql
-- Calculate the total salary
SELECT SUM(Salary) AS TotalSalary FROM Employee;

-- Calculate the sum of unique salaries
SELECT SUM(DISTINCT Salary) AS DistinctSalarySum FROM Employee;
```

---

### 3. `AVG()`

The `AVG()` function calculates the average of a numeric column. It divides the sum of the column by the number of non-NULL rows.

* `AVG(column_name)`: Returns the average of the non-NULL values in the column.

**Examples:**

```sql
-- Calculate the average salary
SELECT AVG(Salary) AS AverageSalary FROM Employee;

-- Average of distinct salaries
SELECT AVG(DISTINCT Salary) AS DistinctAvgSalary FROM Employee;
```

---

### 4. `MIN()` and `MAX()`

The `MIN()` and `MAX()` functions return the smallest and largest values, respectively, from a column.

* `MIN(column_name)`: Returns the minimum value.
* `MAX(column_name)`: Returns the maximum value.

**Examples:**

```sql
-- Find the highest salary
SELECT MAX(Salary) AS HighestSalary FROM Employee;

-- Find the lowest salary
SELECT MIN(Salary) AS LowestSalary FROM Employee;
```

---

## Examples of SQL Aggregate Functions

Let's consider a demo `Employee` table to demonstrate SQL aggregate functions. This table contains employee details such as their ID, Name, and Salary.

| Id | Name | Salary |
| -- | ---- | ------ |
| 1  | A    | 802    |
| 2  | B    | 403    |
| 3  | C    | 604    |
| 4  | D    | 705    |
| 5  | E    | 606    |
| 6  | F    | NULL   |

---

### 1. Count the Total Number of Employees

```sql
SELECT COUNT(*) AS TotalEmployees FROM Employee;
```

**Output:**

| TotalEmployees |
| -------------- |
| 6              |

---

### 2. Calculate the Total Salary

```sql
SELECT SUM(Salary) AS TotalSalary FROM Employee;
```

**Output:**

| TotalSalary |
| ----------- |
| 3120        |

---

### 3. Find the Average Salary

```sql
SELECT AVG(Salary) AS AverageSalary FROM Employee;
```

**Output:**

| AverageSalary |
| ------------- |
| 624           |

---

### 4. Find the Highest and Lowest Salary

```sql
SELECT MAX(Salary) AS HighestSalary FROM Employee;
```

**Output:**

| HighestSalary |
| ------------- |
| 802           |

```sql
SELECT MIN(Salary) AS LowestSalary FROM Employee;
```

**Output:**

| LowestSalary |
| ------------ |
| 403          |

---

## Using Aggregate Functions with `GROUP BY`

SQL `GROUP BY` allows us to group rows that have the same values in specific columns. We can then apply aggregate functions to these groups, which helps us summarize data for each group. This is commonly used with the `COUNT()`, `SUM()`, `AVG()`, `MIN()`, and `MAX()` functions.

**Example: Total Salary by Each Employee**

```sql
SELECT Name, SUM(Salary) AS TotalSalary
FROM Employee
GROUP BY Name;
```

**Output:**

| Name | TotalSalary |
| ---- | ----------- |
| A    | 802         |
| B    | 403         |
| C    | 604         |
| D    | 705         |
| E    | 606         |
| F    | -           |

---

## Using `HAVING` with Aggregate Functions

The `HAVING` clause is used to filter results after applying aggregate functions, unlike `WHERE`, which filters rows before aggregation. `HAVING` is essential when we want to filter based on the result of an aggregate function.

**Example: Find Employees with Salary Greater Than 600**

```sql
SELECT Name, SUM(Salary) AS TotalSalary
FROM Employee
GROUP BY Name
HAVING SUM(Salary) > 600;
```

**Output:**

| Name | TotalSalary |
| ---- | ----------- |
| A    | 802         |
| C    | 604         |
| D    | 705         |
| E    | 606         |

---

## Key Takeaways about SQL Aggregate Functions

* Aggregate functions in SQL operate on a group of values and return a single result.
* They are often used with the `GROUP BY` clause to summarize the grouped data.
* Aggregate functions operate on non-NULL values only (except `COUNT(*)`).
* Commonly used aggregate functions are - `MIN()`, `MAX()`, `COUNT()`, `AVG()`, and `SUM()`.

---
