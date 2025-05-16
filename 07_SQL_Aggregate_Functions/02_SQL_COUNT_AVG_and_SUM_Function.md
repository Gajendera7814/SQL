
---

# SQL COUNT(), AVG(), and SUM() Function

SQL aggregate functions, such as `COUNT()`, `AVG()`, and `SUM()`, are essential tools for performing mathematical analysis on data. These functions allow you to gather valuable insights from your database, such as calculating totals, and averages, and counting specific rows.

---

## SQL COUNT() Function

The `COUNT()` function provides the number of rows that match a specified condition. This function is particularly useful for understanding the volume of data entries and identifying trends based on countable metrics.

**Syntax**:

```sql
SELECT COUNT(column_name)
FROM table_name
WHERE condition;
````

---

## SQL AVG() Function

The `AVG()` function provides the average value of a numeric column, helping you determine central tendencies in your data. This is useful for understanding the mean value of a set of numbers, such as salaries, prices, or scores.

**Syntax**:

```sql
SELECT AVG(column_name) 
FROM table_name 
WHERE condition;
```

---

## SQL SUM() Function

The `SUM()` function provides the total sum of a numeric column. This function is ideal for calculating totals such as sales, revenue, or any other cumulative numeric value.

**Syntax**:

```sql
SELECT SUM(column_name)
FROM table_name
WHERE condition;
```

---

## Examples of SQL COUNT(), AVG(), and SUM() Functions

Let's look at some examples of the `COUNT()`, `AVG()` and `SUM()` functions in SQL to understand them better.

To demonstrate this, let us create a table **"GeeksTab"**.

```sql
CREATE TABLE GeeksTab (
    Name VARCHAR(50),
    City VARCHAR(50),
    Salary INT,
    ID INT,
    DOJ VARCHAR(50)
);
```

```sql
INSERT INTO GeeksTab (Name, City, Salary, ID, DOJ) VALUES
('Abc', 'Delhi', 4500, 134, '6-Aug'),
('Dfe', 'Noida', 6500, 245, '4-March'),
('Def', 'Jaipur', 5400, 546, '2-July'),
('Mno', 'Noida', 7800, 432, '7-June'),
('Jkl', 'Jaipur', 5400, 768, '9-July'),
('Lmn', 'Delhi', 7800, 987, '8-June'),
('Ijk', 'Jaipur', 6700, 654, '5-June');
```

### Table GeeksTab:

| Name | City   | Salary | ID  | DOJ     |
| ---- | ------ | ------ | --- | ------- |
| Abc  | Delhi  | 4500   | 134 | 6-Aug   |
| Dfe  | Noida  | 6500   | 245 | 4-March |
| Def  | Jaipur | 5400   | 546 | 2-July  |
| Mno  | Noida  | 7800   | 432 | 7-June  |
| Jkl  | Jaipur | 5400   | 768 | 9-July  |
| Lmn  | Delhi  | 7800   | 987 | 8-June  |
| Ijk  | Jaipur | 6700   | 654 | 5-June  |

---

### Example 1: COUNT() Function

The following SQL statement finds the number of Names in the "GeeksTab" table.

**Query**:

```sql
SELECT COUNT(Name)
FROM GeeksTab; 
```

**Output**:

```
7
```

---

### Example 2: AVG() Function

The following SQL statement finds the average price of salary in the "GeeksTab" table.

**Query**:

```sql
SELECT AVG(Salary)
FROM GeeksTab; 
```

**Output**:

```
6300
```

---

### Example 3: SUM() Function

The following SQL statement will find the sum of the Salary in the "GeeksTab" table.

**Query**:

```sql
SELECT SUM(Salary)
FROM GeeksTab; 
```

**Output**:

```
44100
```

---

## Important Points About SQL COUNT(), AVG(), and SUM() Functions

1. The SQL `COUNT()`, `AVG()`, and `SUM()` functions are essential aggregate functions used in SQL for data analysis and reporting.

2. The `COUNT()` function provides the number of rows that match a specified condition, while the `AVG()` function calculates the average value of a numeric column, and the `SUM()` function returns the total sum of a numeric column.

3. These functions are commonly used in SQL queries to perform calculations on data sets, enabling users to count rows, calculate averages, and sum values efficiently.

4. These functions can be used in combination with other SQL clauses, such as `WHERE`, `GROUP BY`, and `HAVING`, to perform more complex data analysis tasks.

5. It's important to consider how these functions handle `NULL` values, as they can affect the final results.

---
