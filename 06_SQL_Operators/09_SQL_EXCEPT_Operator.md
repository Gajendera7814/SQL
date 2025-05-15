
---

## What is SQL EXCEPT?

The SQL EXCEPT operator allows you to return the rows that exist in the first result set but not in the second. It is useful for finding records in one table that do not have corresponding records in another table.

---

## Syntax:

```sql
SELECT column_name(s) 
FROM table1
EXCEPT
SELECT column_name(s) 
FROM table2;
````

**Note:** The two SELECT queries must return the same number of columns and the data types must be compatible.

---

## Examples of SQL EXCEPT

Let’s consider two tables, Students and Teaching Assistant. We will perform all the examples based on these two tables.

---

### Students Table

```sql
-- Create Students Table
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100),
    Course VARCHAR(100)
);

-- Insert Data into Students Table
INSERT INTO Students (StudentID, Name, Course) VALUES
(1, 'Rohan', 'DBMS'),
(2, 'Kevin', 'OS'),
(3, 'Mansi', 'DBMS'),
(4, 'Mansi', 'ADA'),
(5, 'Rekha', 'ADA'),
(6, 'Megha', 'OS');
```

---

### Output:

| StudentID | Name  | Course |
| --------- | ----- | ------ |
| 1         | Rohan | DBMS   |
| 2         | Kevin | OS     |
| 3         | Mansi | DBMS   |
| 4         | Mansi | ADA    |
| 5         | Rekha | ADA    |
| 6         | Megha | OS     |

---

### Teaching Assistant Table

```sql
-- Create Teaching Assistant Table
CREATE TABLE TA (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100),
    Course VARCHAR(100)
);

-- Insert Data into TA Table
INSERT INTO TA (StudentID, Name, Course) VALUES
(1, 'Kevin', 'TOC'),
(2, 'Sita', 'IP'),
(3, 'Manik', 'AP'),
(4, 'Rekha', 'SNS');
```

---

### Output:

| StudentID | Name  | Course |
| --------- | ----- | ------ |
| 1         | Kevin | TOC    |
| 2         | Sita  | IP     |
| 3         | Manik | AP     |
| 4         | Rekha | SNS    |

---

## Example 1: Filter Student

We want to find all the students who are not teaching assistants.

```sql
SELECT Name
FROM Students
EXCEPT
SELECT Name
FROM TA;
```

---

### Output:

| Name  |
| ----- |
| Mansi |
| Megha |
| Rohan |

**Explanation:** The EXCEPT operator returns the names that are present in the Students table but not in the TA table. Notice that "Rohan", "Mansi", and "Megha" are returned, as these students are not listed in the TA table.

---

## Example 2: Retaining Duplicates with EXCEPT ALL

By default, EXCEPT removes duplicates from the result set. To retain duplicates, you can use EXCEPT ALL instead.

```sql
SELECT Name FROM Students
EXCEPT ALL
SELECT Name FROM TA;
```

---

### Output:

| Name  |
| ----- |
| Rohan |
| Mansi |
| Mansi |
| Megha |

**Explanation:** In this case, "Mansi" appears twice in the output because it appears twice in the Students table and is not in the TA table. EXCEPT ALL retains duplicates from the first result set.

---

## SQL EXCEPT vs. SQL NOT IN

While both EXCEPT and NOT IN are used to exclude certain records, there are important differences between them.

| Feature            | EXCEPT                                                                             | NOT IN                                                                         |
| ------------------ | ---------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| Duplicate Handling | Removes duplicates from the result                                                 | Retains duplicates in the result                                               |
| Performance        | Generally more efficient for large datasets as it processes only the required rows | May be slower for large datasets, especially when checking multiple conditions |
| Use Case           | When you need to find rows that exist in one result set but not the other          | When you need to check a specific column’s values against a list               |
| SQL Support        | Not supported by MySQL                                                             | Supported by most SQL databases                                                |

---

## Key Points to Remember

* EXCEPT returns rows from the first result set that are not in the second result set.
* EXCEPT automatically removes duplicates, while EXCEPT ALL retains duplicates.
* EXCEPT requires both queries to have the same number of columns and compatible data types.
* EXCEPT is not supported in MySQL, while NOT IN can be used as an alternative.
* Use EXCEPT when you need to exclude certain rows efficiently from the first result set, especially in larger datasets.

---
