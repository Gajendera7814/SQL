
---

## SQL BETWEEN Operator

The SQL BETWEEN operator is used to filter the result set within a specified range.  
It can be applied to numeric, date, and text columns.  
The BETWEEN operator is inclusive, meaning it includes the start and end values in the result set.

---

## Syntax:

The basic syntax of the 'BETWEEN' operator is as follows:

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
````

---

## Parameters:

* **column\_name(s):** The name of the column(s) you want to retrieve data from.
* **table\_name:** The name of the table containing the data.
* **column\_name:** The name of the column you want to apply the BETWEEN filter to.
* **value1:** The starting value of the range.
* **value2:** The ending value of the range.

---

## Examples of BETWEEN Operator

To understand the SQL BETWEEN Operator we will use the below employees table with the various examples and their output.

| EmployeeID | FirstName | LastName | Age | Salary | HireDate   |
| ---------- | --------- | -------- | --- | ------ | ---------- |
| 1          | John      | Doe      | 28  | 50000  | 2021-01-15 |
| 2          | Jane      | Smith    | 34  | 60000  | 2020-03-22 |
| 3          | Sam       | Brown    | 45  | 75000  | 2018-07-10 |
| 4          | Sue       | Wilson   | 25  | 48000  | 2021-10-01 |
| 5          | Tom       | Harris   | 38  | 68000  | 2019-05-12 |

---

### Example 1: NOT BETWEEN Text Values

Find employees whose last names are not alphabetically between 'B' and 'S'.

```sql
SELECT FirstName, LastName 
FROM Employees 
WHERE LastName NOT BETWEEN 'B' AND 'S';
```

---

### Output:

| FirstName | LastName |
| --------- | -------- |
| Jane      | Smith    |
| Sue       | Wilson   |

**Explanation:**
The query retrieves employees whose last names fall outside the alphabetical range of 'B' to 'S'. Only Tom Harris qualifies, as 'Harris' comes after 'B' but before 'S'.

---

### Example 2: BETWEEN Dates

Find employees hired between January 1, 2020 and December 31, 2021.

```sql
SELECT FirstName, LastName, HireDate 
FROM Employees 
WHERE HireDate BETWEEN '2020-01-01' AND '2021-12-31';
```

---

### Output:

| FirstName | LastName | HireDate   |
| --------- | -------- | ---------- |
| Jane      | Smith    | 2020-03-22 |
| John      | Doe      | 2021-01-15 |
| Sue       | Wilson   | 2021-10-01 |

**Explanation:**
This query returns employees who were hired during the years 2020 and 2021. The BETWEEN operator is used to filter the HireDate field, returning records within the specified date range.

---

### Example 3: NOT BETWEEN

Find employees whose age is not between 30 and 40.

```sql
SELECT FirstName, LastName, Age 
FROM Employees 
WHERE Age NOT BETWEEN 30 AND 40;
```

---

### Output:

| FirstName | LastName | Age |
| --------- | -------- | --- |
| John      | Doe      | 28  |
| Sam       | Brown    | 45  |
| Sue       | Wilson   | 25  |

**Explanation:**
This query retrieves employees whose age does not fall between 30 and 40. The NOT BETWEEN operator is used here to exclude employees within that age range. John, Sam, and Sue meet this condition, as their ages are outside the 30-40 range.

---

### Example 4: BETWEEN with IN

Find employees whose salaries are between 50,000 and 70,000 and whose first names are either 'John', 'Sue', or 'Tom'.

```sql
SELECT FirstName, LastName, Salary 
FROM Employees 
WHERE Salary BETWEEN 50000 AND 70000 
  AND FirstName IN ('John', 'Sue', 'Tom');
```

---

### Output:

| FirstName | LastName | Salary |
| --------- | -------- | ------ |
| John      | Doe      | 50000  |
| Sue       | Wilson   | 48000  |

**Explanation:**
This query filters employees with salaries between 50,000 and 70,000 and also checks if their first names are in the list ('John', 'Sue', 'Tom'). Only John and Sue satisfy both conditions.

---
