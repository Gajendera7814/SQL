
---

# 📘 SQL SELECT IN Statement

The `IN` operator in SQL is used to compare a column's value against a **set of values**.  
It returns:

- ✅ `TRUE` → if the column's value matches **any** of the values in the list  
- ❌ `FALSE` → if there is **no match**

This article explains how the `IN` operator works with **examples**, **syntax**, and **tables**.

---

## ❓ What is the SQL SELECT IN Statement?

The `SELECT IN` statement allows you to specify **multiple values** in the `WHERE` clause.  
It is similar to using multiple `OR` conditions and is particularly useful for:

- Filtering records based on a list of values
- Filtering based on results from a subquery

---

## 🧾 Syntax

### ✅ Syntax 1: SELECT IN with a List of Values

```sql
SELECT column1, column2, ..., columnN
FROM table_name
WHERE column_name IN (val-1, val-2, ..., val-N);
````

### Parameters:

* `column1, column2, ..., columnN`: Columns to retrieve
* `table_name`: Table name
* `column_name`: Column to filter
* `val-1, val-2, ..., val-N`: List of values to match

---

### ✅ Syntax 2: SELECT IN with a Subquery

```sql
SELECT column1, column2, ..., columnN
FROM table_name1
WHERE column_name IN (
  SELECT column_name
  FROM table_name2
);
```

### Parameters:

* `table_name1`: Main table to query
* `table_name2`: Table used in the subquery to return values

---

## 📊 SQL SELECT IN Example

Let’s create a sample database to demonstrate:

---

### 🏫 Course Table

```sql
CREATE TABLE COURSE(
    course_id INT,
    course_name VARCHAR(20),
    duration_of_course INT,
    PRIMARY KEY(course_id)
); 

INSERT INTO COURSE(course_id, course_name, duration_of_course) 
VALUES
    (1, 'BCA', 3),
    (2, 'MCA', 3),
    (3, 'B.E.', 4),
    (4, 'M.E.', 2),
    (5, 'Integrated BE and ME', 5);
```

**Table: COURSE**

---

### 👨‍🎓 Student Table

```sql
CREATE TABLE STUDENT(
    roll_no INT,
    student_name VARCHAR(20),
    course_id INT,
    PRIMARY KEY(roll_no)
); 

INSERT INTO STUDENT(roll_no, student_name, course_id) 
VALUES
    (1, 'ANDREW', 1),
    (2, 'BOB', 1),
    (3, 'CHARLES', 1),
    (4, 'DAIZY', 3),
    (5, 'EMMANUEL', 2),
    (6, 'FAIZAL', 2),
    (7, 'GEORGE', 4),
    (8, 'HARSH', 5),
    (9, 'ISHA', 2),
    (10, 'JULIAN', 2),
    (11, 'KAILASH', 3),
    (12, 'LAIBA', 5),
    (13, 'MICHAEL', 3);
```

```sql
SELECT * FROM STUDENT;
```

---

## 🧪 Example 1: Using SELECT IN with a List of Values

```sql
SELECT * 
FROM STUDENT
WHERE course_id IN (1, 2, 3);
```

**Output:**

| roll\_no | student\_name | course\_id |
| -------- | ------------- | ---------- |
| 1        | ANDREW        | 1          |
| 2        | BOB           | 1          |
| 3        | CHARLES       | 1          |
| 4        | DAIZY         | 3          |
| 5        | EMMANUEL      | 2          |
| 6        | FAIZAL        | 2          |
| 9        | ISHA          | 2          |
| 10       | JULIAN        | 2          |
| 11       | KAILASH       | 3          |
| 13       | MICHAEL       | 3          |

---

## 🧪 Example 2: SELECT IN with a Subquery

```sql
SELECT * 
FROM STUDENT
WHERE course_id IN (
    SELECT course_id 
    FROM COURSE
    WHERE duration_of_course = 3
);
```

**Output:**

| roll\_no | student\_name | course\_id |
| -------- | ------------- | ---------- |
| 1        | ANDREW        | 1          |
| 2        | BOB           | 1          |
| 3        | CHARLES       | 1          |
| 5        | EMMANUEL      | 2          |
| 6        | FAIZAL        | 2          |
| 9        | ISHA          | 2          |
| 10       | JULIAN        | 2          |

---

## 📌 Important Points

* `SELECT IN` is used in the `WHERE` clause to **match multiple values**
* It is equivalent to multiple `OR` conditions:

```sql
WHERE column_name IN (val-1, val-2, val-3)
-- is same as
WHERE column_name = val-1 OR column_name = val-2 OR column_name = val-3
```

* The `IN` operator works with:

  * ✅ Static value lists
  * ✅ Subqueries

---

## ✅ Conclusion

The `SQL SELECT IN` statement is a **powerful tool** for filtering records against **multiple values or subqueries**.
It improves **readability** and **efficiency** compared to multiple OR conditions.

Whether you're filtering data using a **static list** or dynamically with a **subquery**, `IN` simplifies your SQL queries and makes them easier to manage.

---
