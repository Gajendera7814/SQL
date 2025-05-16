
---

# SQL Joins (Inner, Left, Right and Full Join)

SQL joins are fundamental tools for combining data from multiple tables in relational databases. Joins allow efficient data retrieval, which is essential for generating meaningful observations and solving complex business queries. Understanding SQL join types, such as INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL JOIN, and NATURAL JOIN, is critical for working with relational databases.

## What is SQL Join?

An SQL JOIN clause is used to query and access data from multiple tables by establishing logical relationships between them. It can access data from multiple tables simultaneously using common key values shared across different tables. We can use SQL JOIN with multiple tables. It can also be paired with other clauses, the most popular use will be using JOIN with WHERE clause to filter data retrieval.

### Before diving into the specifics, let's visualize how each join type operates:

* **INNER JOIN**: Returns only the rows where there is a match in both tables.
* **LEFT JOIN (LEFT OUTER JOIN)**: Returns all rows from the left table, and the matched rows from the right table. If there's no match, NULL values are returned for columns from the right table.
* **RIGHT JOIN (RIGHT OUTER JOIN)**: Returns all rows from the right table, and the matched rows from the left table. If there's no match, NULL values are returned for columns from the left table.
* **FULL JOIN (FULL OUTER JOIN)**: Returns all rows when there is a match in one of the tables. If there's no match, NULL values are returned for columns from the table without a match.

## 1. SQL INNER JOIN

The `INNER JOIN` keyword selects all rows from both the tables as long as the condition is satisfied. This keyword will create the result-set by combining all rows from both the tables where the condition satisfies i.e. value of the common field will be the same.

### Syntax

```sql
SELECT table1.column1, table1.column2, table2.column1, ...
FROM table1
INNER JOIN table2
ON table1.matching_column = table2.matching_column;
```

> Note: We can also write `JOIN` instead of `INNER JOIN`. JOIN is same as INNER JOIN.

### Example of INNER JOIN

Consider the two tables, `Student` and `StudentCourse`, which share a common column `ROLL_NO`. Using SQL JOINS, we can combine data from these tables based on their relationship.

#### Query:

```sql
SELECT StudentCourse.COURSE_ID, Student.NAME, Student.AGE
FROM Student
INNER JOIN StudentCourse
ON Student.ROLL_NO = StudentCourse.ROLL_NO;
```

---

## 2. SQL LEFT JOIN

A `LEFT JOIN` returns all rows from the left table, along with matching rows from the right table. If there is no match, NULL values are returned for columns from the right table. LEFT JOIN is also known as LEFT OUTER JOIN.

### Syntax

```sql
SELECT table1.column1, table1.column2, table2.column1, ...
FROM table1
LEFT JOIN table2
ON table1.matching_column = table2.matching_column;
```

> Note: We can also use `LEFT OUTER JOIN` instead of `LEFT JOIN`, both are the same.

### LEFT JOIN Example

#### Query:

```sql
SELECT Student.NAME, StudentCourse.COURSE_ID
FROM Student
LEFT JOIN StudentCourse
ON StudentCourse.ROLL_NO = Student.ROLL_NO;
```

---

## 3. SQL RIGHT JOIN

`RIGHT JOIN` returns all the rows of the table on the right side of the join and matching rows for the table on the left side of the join. For rows for which there is no matching row on the left side, the result-set will contain NULL. RIGHT JOIN is also known as RIGHT OUTER JOIN.

### Syntax

```sql
SELECT table1.column1, table1.column2, table2.column1, ...
FROM table1
RIGHT JOIN table2
ON table1.matching_column = table2.matching_column;
```

**Key Terms:**

* `table1`: First table.
* `table2`: Second table
* `matching_column`: Column common to both the tables.

> Note: We can also use `RIGHT OUTER JOIN` instead of `RIGHT JOIN`, both are the same.

### RIGHT JOIN Example

#### Query:

```sql
SELECT Student.NAME, StudentCourse.COURSE_ID
FROM Student
RIGHT JOIN StudentCourse
ON StudentCourse.ROLL_NO = Student.ROLL_NO;
```

---

## 4. SQL FULL JOIN

`FULL JOIN` creates the result-set by combining results of both LEFT JOIN and RIGHT JOIN. The result-set will contain all the rows from both tables. For the rows for which there is no matching, the result-set will contain NULL values.

### Syntax

```sql
SELECT table1.column1, table1.column2, table2.column1, ...
FROM table1
FULL JOIN table2
ON table1.matching_column = table2.matching_column;
```

**Key Terms:**

* `table1`: First table.
* `table2`: Second table
* `matching_column`: Column common to both the tables.

### FULL JOIN Example

#### Query:

```sql
SELECT Student.NAME, StudentCourse.COURSE_ID
FROM Student
FULL JOIN StudentCourse
ON StudentCourse.ROLL_NO = Student.ROLL_NO;
```

#### Output:

```
NAME       | COURSE_ID
-----------|----------
HARSH      | 1
PRATIK     | 2
RIYANKA    | 2
DEEP       | 3
SAPTARHI   | 1
DHANRAJ    | NULL
ROHIT      | NULL
NIRAJ      | NULL
NULL       | 4
NULL       | 5
NULL       | 4
```

---

## 5. SQL Natural Join

Natural join can join tables based on the common columns in the tables being joined. A natural join returns all rows by matching values in common columns having same name and data type of columns and that column should be present in both tables.

* Both tables must have at least one common column with same column name and same data type.
* The two tables are joined using cross join internally.
* DBMS will look for a common column with same name and data type.

### Natural Join Example

**Employee Table**

```
Emp_id | Emp_name | Dept_id
-------|----------|--------
1      | Ram      | 10
2      | Jon      | 30
3      | Bob      | 50
```

**Department Table**

```
Dept_id | Dept_name
--------|-----------
10      | IT
30      | HR
40      | TIS
```

**Problem**: Find all Employees and their respective departments.

**Solution Query**:

```
(Employee) NATURAL JOIN (Department)
```

**Output**:

```
Emp_id | Emp_name | Dept_id | Dept_name
-------|----------|---------|----------
1      | Ram      | 10      | IT
2      | Jon      | 30      | HR
```

---

## 🧱 1. Tables and Sample Data

### 🔹 `Student` Table

```sql
CREATE TABLE Student (
    ROLL_NO INT PRIMARY KEY,
    NAME VARCHAR(50),
    AGE INT
);

INSERT INTO Student (ROLL_NO, NAME, AGE) VALUES
(1, 'Harsh', 21),
(2, 'Pratik', 22),
(3, 'Riyanka', 20),
(4, 'Deep', 23),
(5, 'Saptarhi', 22),
(6, 'Dhanraj', 24),
(7, 'Rohit', 21),
(8, 'Niraj', 20);
```

### 🔹 `StudentCourse` Table

```sql
CREATE TABLE StudentCourse (
    COURSE_ID INT,
    ROLL_NO INT,
    FOREIGN KEY (ROLL_NO) REFERENCES Student(ROLL_NO)
);

INSERT INTO StudentCourse (COURSE_ID, ROLL_NO) VALUES
(1, 1),
(2, 2),
(2, 3),
(3, 4),
(1, 5),
(4, NULL),
(5, NULL),
(4, NULL);
```

---

## 🔗 1. INNER JOIN

### 🔍 Query:

```sql
SELECT StudentCourse.COURSE_ID, Student.NAME, Student.AGE
FROM Student
INNER JOIN StudentCourse
ON Student.ROLL_NO = StudentCourse.ROLL_NO;
```

### 📤 Output:

| COURSE\_ID | NAME     | AGE |
| ---------- | -------- | --- |
| 1          | Harsh    | 21  |
| 2          | Pratik   | 22  |
| 2          | Riyanka  | 20  |
| 3          | Deep     | 23  |
| 1          | Saptarhi | 22  |

✅ **Only matched rows** from both tables are returned.

---

## 🔗 2. LEFT JOIN

### 🔍 Query:

```sql
SELECT Student.NAME, StudentCourse.COURSE_ID
FROM Student
LEFT JOIN StudentCourse
ON Student.ROLL_NO = StudentCourse.ROLL_NO;
```

### 📤 Output:

| NAME     | COURSE\_ID |
| -------- | ---------- |
| Harsh    | 1          |
| Pratik   | 2          |
| Riyanka  | 2          |
| Deep     | 3          |
| Saptarhi | 1          |
| Dhanraj  | NULL       |
| Rohit    | NULL       |
| Niraj    | NULL       |

✅ **All students** are listed, including those **not enrolled** in a course.

---

## 🔗 3. RIGHT JOIN

### 🔍 Query:

```sql
SELECT Student.NAME, StudentCourse.COURSE_ID
FROM Student
RIGHT JOIN StudentCourse
ON Student.ROLL_NO = StudentCourse.ROLL_NO;
```

### 📤 Output:

| NAME     | COURSE\_ID |
| -------- | ---------- |
| Harsh    | 1          |
| Pratik   | 2          |
| Riyanka  | 2          |
| Deep     | 3          |
| Saptarhi | 1          |
| NULL     | 4          |
| NULL     | 5          |
| NULL     | 4          |

✅ All `StudentCourse` rows are shown, even if there is **no matching student** (`NULL` for `NAME`).

---

## 🔗 4. FULL JOIN

> Not supported in all databases like MySQL. You can simulate using `UNION`.

### 🔍 Query:

```sql
SELECT Student.NAME, StudentCourse.COURSE_ID
FROM Student
FULL JOIN StudentCourse
ON Student.ROLL_NO = StudentCourse.ROLL_NO;
```

### 📤 Output:

| NAME     | COURSE\_ID |
| -------- | ---------- |
| Harsh    | 1          |
| Pratik   | 2          |
| Riyanka  | 2          |
| Deep     | 3          |
| Saptarhi | 1          |
| Dhanraj  | NULL       |
| Rohit    | NULL       |
| Niraj    | NULL       |
| NULL     | 4          |
| NULL     | 5          |
| NULL     | 4          |

✅ **All records from both tables**, matched and unmatched.

---

## 🔗 5. NATURAL JOIN

### 👇 New Tables

#### 🔹 `Employee`

```sql
CREATE TABLE Employee (
    Emp_id INT PRIMARY KEY,
    Emp_name VARCHAR(50),
    Dept_id INT
);

INSERT INTO Employee VALUES
(1, 'Ram', 10),
(2, 'Jon', 30),
(3, 'Bob', 50);
```

#### 🔹 `Department`

```sql
CREATE TABLE Department (
    Dept_id INT PRIMARY KEY,
    Dept_name VARCHAR(50)
);

INSERT INTO Department VALUES
(10, 'IT'),
(30, 'HR'),
(40, 'TIS');
```

### 🔍 Query:

```sql
SELECT *
FROM Employee
NATURAL JOIN Department;
```

### 📤 Output:

| Emp\_id | Emp\_name | Dept\_id | Dept\_name |
| ------- | --------- | -------- | ---------- |
| 1       | Ram       | 10       | IT         |
| 2       | Jon       | 30       | HR         |

✅ **Automatically joins** using `Dept_id` (same column name in both tables).

---
