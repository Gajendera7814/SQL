
---

# SQL Outer Join

SQL Outer Joins allow retrieval of rows from two or more tables based on a related column. Unlike inner Joins, they also include rows that do not have a corresponding match in one or both of the tables. This capability makes Outer Joins extremely useful for comprehensive data analysis and reporting, especially when dealing with incomplete data or wanting to show all records regardless of matching conditions.

## What is an SQL Outer Join?

Outer Join ensures that all rows from one or both tables are included in the result, even if there is no match in the other table. It is particularly useful when you need to show all records from one table, including those that don't have a match in the other table.

## Types of Outer Joins

There are three main types of Outer Joins in SQL:

- **LEFT OUTER JOIN** (or LEFT JOIN)
- **RIGHT OUTER JOIN** (or RIGHT JOIN)
- **FULL OUTER JOIN**

Each of these join types handles unmatched rows differently, and understanding how they work will help you use them effectively in your SQL queries.

### Let's Consider the two tables, Employees and Departments for understanding all the above outer join with examples

#### Employees Table:

| EmployeeID | Name    | DepartmentID |
|------------|---------|---------------|
| 1          | John    | 101           |
| 2          | Sarah   | 102           |
| 3          | Michael | -             |
| 4          | Emma    | 103           |

#### Departments Table:

| DepartmentID | DepartmentName |
|--------------|----------------|
| 101          | HR             |
| 102          | IT             |
| 103          | Marketing      |

---

## LEFT OUTER JOIN (or LEFT JOIN)

The LEFT OUTER JOIN (referred to as LEFT JOIN) returns all rows from the left table, and the matching rows from the right table. If there is no match, the result will include NULL values for columns from the right table.

### Syntax:

```sql
SELECT table1.column1, table1.column2, table2.column1, ...
FROM table1
LEFT JOIN table2
ON table1.matching_column = table2.matching_column;
```

### Example:

To retrieve all employees along with their respective departments, even if they don't belong to any department (i.e., the department is NULL), we can use the LEFT OUTER JOIN.

```sql
SELECT Employees.Name, Employees.DepartmentID, Departments.DepartmentName
FROM Employees
LEFT JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

### Output:

| Name    | DepartmentID | DepartmentName |
|---------|--------------|----------------|
| John    | 101          | HR             |
| Sarah   | 102          | IT             |
| Michael | -            | -              |
| Emma    | 103          | Marketing      |

In this example, Michael does not belong to any department, so the DepartmentName for Michael is NULL.

---

## RIGHT OUTER JOIN (RIGHT JOIN)

The RIGHT OUTER JOIN (often called RIGHT JOIN) returns all rows from the right table, and the matching rows from the left table. If there is no match, the result will include NULL values for columns from the left table.

### Syntax:

```sql
SELECT table1.column1, table1.column2, table2.column1, ...
FROM table1
RIGHT JOIN table2
ON table1.matching_column = table2.matching_column;
```

### Example:

Let’s now look at a RIGHT OUTER JOIN on the Employees and Departments tables. Suppose we want to retrieve all departments, even if no employees belong to a specific department.

```sql
SELECT Employees.Name, Employees.DepartmentID, Departments.DepartmentName
FROM Employees
RIGHT JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

### Output:

| Name    | DepartmentID | DepartmentName |
|---------|--------------|----------------|
| John    | 101          | HR             |
| Sarah   | 102          | IT             |
| Emma    | 103          | Marketing      |

---

## FULL OUTER JOIN

The FULL OUTER JOIN returns all rows when there is a match in either the left or right table. If there is no match, the result will include NULL for the missing side of the table. Essentially, it combines the results of both LEFT JOIN and RIGHT JOIN.

### Syntax:

```sql
SELECT table1.column1, table1.column2, table2.column1, ...
FROM table1
FULL JOIN table2
ON table1.matching_column = table2.matching_column;
```

### Example:

Let’s now use a FULL OUTER JOIN to get all employees and all departments, regardless of whether an employee belongs to a department or a department has employees.

```sql
SELECT Employees.Name, Employees.DepartmentID, Departments.DepartmentName
FROM Employees
FULL JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

### Output:

| Name    | DepartmentID | DepartmentName |
|---------|--------------|----------------|
| John    | 101          | HR             |
| Sarah   | 102          | IT             |
| Michael | -            | -              |
| Emma    | 103          | Marketing      |

In this example, Michael has no department so his department name is NULL.

---

## When to Use SQL Outer Joins?

Outer joins are particularly useful in the following situations:

- **Incomplete Data**: When you need to include all records from one table even if there is no match in the other table.
- **Data Integrity Issues**: When working with datasets that might have missing or incomplete relationships.
- **Reporting and Analysis**: When generating reports that need to show all records, regardless of matching conditions.
- **Data Merging**: When merging datasets from different sources where some records might not have corresponding matches.

---