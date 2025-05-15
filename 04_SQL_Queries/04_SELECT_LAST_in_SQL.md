
---

# 📘 SQL - SELECT LAST

`SELECT LAST` is a concept used to retrieve the **last record** from a table in SQL. While MS Access supports the `LAST()` function directly, most SQL databases such as MySQL, PostgreSQL, Oracle, and SQL Server **do not support** it. Therefore, alternative methods must be used.

This guide covers **4 different ways** to get the last record from a table across various SQL environments.

---

## 📂 Table Structure & Sample Data

We will use a sample table called `Student_Information`:

```sql
CREATE TABLE Student_Information (
    ID INT PRIMARY KEY,
    Age INT,
    Student_Name VARCHAR(50),
    Sex VARCHAR(10)
);
````

### Sample Data:

```sql
INSERT INTO Student_Information (ID, Age, Student_Name, Sex)
VALUES
    (1, 22, 'Harry', 'Male'),
    (2, 23, 'Vishal', 'Male'),
    (3, 20, 'Snehal', 'Female'),
    (4, 25, 'Ram', 'Male'),
    (5, 24, 'Hina', 'Female');
```

### Current Table View:

| ID | Age | Student\_Name | Sex    |
| -- | --- | ------------- | ------ |
| 1  | 22  | Harry         | Male   |
| 2  | 23  | Vishal        | Male   |
| 3  | 20  | Snehal        | Female |
| 4  | 25  | Ram           | Male   |
| 5  | 24  | Hina          | Female |

---

## 🧪 Method 1: Using `LAST()` Function (MS Access Only)

In MS Access, `LAST()` can be used to retrieve the last record from a column.

### Syntax:

```sql
SELECT LAST(Student_Name) AS Stud_Name
FROM Student_Information;
```

### ✅ Output:

| Last Student Name |
| ----------------- |
| Hina              |

⚠️ Note: This method **only works in MS Access**, not in MySQL, PostgreSQL, or Oracle.

---

## 📊 Method 2: Using `ORDER BY` and `LIMIT` (MySQL / PostgreSQL / SQLite)

### ✅ MySQL / PostgreSQL Syntax:

```sql
SELECT Student_Name
FROM Student_Information
ORDER BY ID DESC
LIMIT 1;
```

### ✅ Oracle Syntax:

```sql
SELECT Student_Name
FROM (
    SELECT Student_Name
    FROM Student_Information
    ORDER BY ID DESC
)
WHERE ROWNUM = 1;
```

### ⚠️ Important:

Make sure to order by a **sequential and unique column** like `ID`.
Do **not** use `Student_Name` or `Age` for ordering.

### ❌ Incorrect Ordering Examples:

```sql
ORDER BY Student_Name DESC -- Sorts alphabetically, not row order
ORDER BY Age DESC           -- May not reflect the last inserted record
```

---

## 📐 Method 3: Using Subquery + `MAX()` (Any SQL Engine)

Use a subquery to fetch the maximum ID, then retrieve the corresponding row.

```sql
SELECT Student_Name
FROM Student_Information
WHERE ID = (
    SELECT MAX(ID)
    FROM Student_Information
);
```

### ✅ Output:

| Last Student Name |
| ----------------- |
| Hina              |

---

## 🧮 Method 4: Using `NOT EXISTS` (Relative/Comparative)

This is a more complex subquery approach using `NOT EXISTS`.

```sql
SELECT Student_Name
FROM Student_Information t1
WHERE NOT EXISTS (
    SELECT *
    FROM Student_Information t2
    WHERE t2.ID > t1.ID
);
```

### ✅ Output:

| Last Student Name |
| ----------------- |
| Hina              |

⚠️ This query checks that **no other row exists with a higher ID**.
⏱️ Might be **slower** for large datasets.

---

## 📝 Comparison Table

| Method             | Syntax Example Used           | Supported In              | Performance | Simplicity |
| ------------------ | ----------------------------- | ------------------------- | ----------- | ---------- |
| `LAST()`           | `SELECT LAST(col)`            | MS Access only            | ✅ Fast      | ✅ Easy     |
| `ORDER BY + LIMIT` | `ORDER BY ID DESC LIMIT 1`    | MySQL, PostgreSQL, SQLite | ✅ Fast      | ✅ Easy     |
| `MAX()` Subquery   | `WHERE ID = (SELECT MAX(ID))` | All SQL Databases         | ✅ Fast      | ✅ Easy     |
| `NOT EXISTS`       | `WHERE NOT EXISTS (...)`      | All SQL Databases         | ❌ Slower    | ❌ Complex  |

---

## 🧾 Conclusion

Retrieving the **last record** from a table is a frequent task in real-world databases.

* ✅ Use `LAST()` if you’re using **MS Access**
* ✅ Use `ORDER BY ... LIMIT 1` for **MySQL / PostgreSQL / Oracle**
* ✅ Use `MAX()` with a subquery for **simple & readable logic**
* ❌ Use `NOT EXISTS` only when required — it’s **slower for big tables**

Choose the method based on your database system and data size.

---

## 🧠 Related Topics

* `SELECT FIRST()` – Get the first record
* `ROWNUM` and `TOP` clauses
* `OFFSET` for pagination
* Aggregate functions (`MAX()`, `MIN()`, etc.)

---
