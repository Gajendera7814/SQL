
---

## 🔍 ORDER BY Clause in SQL

The `ORDER BY` statement in SQL is used to **sort the fetched data** in either **ascending** or **descending** order according to one or more columns. It is very useful to present data in a structured manner.

* Default sorting mode is **ascending**.
* To sort in **descending** order, use the `DESC` keyword.

---

## 🧾 Syntax

```sql
SELECT * FROM table_name ORDER BY column_name ASC | DESC;
```

### 🔑 Key Terms

* **table\_name**: name of the table.
* **column\_name**: name of the column according to which the data is needed to be arranged.
* **ASC**: to sort the data in ascending order.
* **DESC**: to sort the data in descending order.

---

## 📋 SQL ORDER BY Clause Examples

We have created a `Student` table that stores student data including their `roll_no`, `name`, `age`, `address`, and `phone`.

We will use the following table in examples.

### 🧮 Table: Student\_Table

```
| Roll_no | Name     | Age | Address     | ContactNo   |
|---------|----------|-----|-------------|-------------|
| 7       | ROHIT    | 18  | GHAZIABAD   | 9193458625  |
| 4       | DEEP     | 18  | RAMNAGAR    | 9193458546  |
| 1       | HARSH    | 18  | DELHI       | 9193342625  |
| 8       | NIRAJ    | 19  | ALIPUR      | 9193678625  |
| 5       | SAPTARHI | 19  | KOLKATA     | 9193789625  |
| 2       | PRATIK   | 19  | BIHAR       | 9193457825  |
| 6       | DHANRAJ  | 20  | BARABAJAR   | 9193358625  |
| 3       | RIYANKA  | 20  | SILIGURI    | 9193218625  |
```

---

### ✅ Example 1: Sort According To a Single Column Using ORDER BY

In this example, we will fetch all data from the table `students` and sort the result in **descending** order according to the column `ROLL_NO`.

```sql
SELECT * FROM students ORDER BY ROLL_NO DESC;
```

📌 In the above example, to sort in ascending order, use `ASC` in place of `DESC`.

---

### ✅ Example 2: Sort According To Multiple Columns Using ORDER BY

In this example, we sort first by **`age` in descending order**, and then by **`name` in ascending order**.

```sql
SELECT * FROM students ORDER BY age DESC, name ASC;
```

📌 In the result:

* Rows are first sorted by `age` descending.
* Ties in age are sorted by `name` ascending.

**Note**: `ASC` is the **default** sorting order. If nothing is specified, the result is sorted in ascending order by default.

---

### ✅ Sorting By Column Number (Instead of Name)

You can also sort by the **column number** in the `SELECT` list. This makes the query shorter but less readable. Use this method carefully.

📌 The column number must:

* Be greater than 0.
* Not exceed the number of columns in the result.
* Refer to columns listed in the `SELECT` clause.

---

### 🧾 Syntax

```sql
SELECT column1, column2 FROM table_name ORDER BY Column_Number ASC | DESC;
```

---

### ✅ Example: Sorting By Column Number

Here we sort the results by **column 1** i.e., `Roll_no`.

```sql
CREATE TABLE studentinfo (
  Roll_no INT,
  NAME VARCHAR(25),
  Address VARCHAR(20),
  CONTACTNO BIGINT NOT NULL,
  Age INT
);

INSERT INTO studentinfo
VALUES 
  (7, 'ROHIT', 'GHAZIABAD', 9193458625, 18),
  (4, 'DEEP', 'RAMNAGAR', 9193458546, 18),
  (1, 'HARSH', 'DELHI', 9193342625, 18),
  (8, 'NIRAJ', 'ALIPUR', 9193678625, 19),
  (5, 'SAPTARHI', 'KOLKATA', 9193789625, 19),
  (2, 'PRATIK', 'BIHAR', 9193457825, 19),
  (6, 'DHANRAJ', 'BARABAJAR', 9193358625, 20),
  (3, 'RIYANKA', 'SILIGURI', 9193218625, 20);

SELECT Roll_no, Name, Address
FROM studentinfo
ORDER BY 1;
```

📌 `ORDER BY 1` means sort by the **first column** in the `SELECT` clause (`Roll_no` in this case).

---

## 📌 Important Points About ORDER BY Clause in SQL

* The `ORDER BY` clause is used to **sort** the result set of a `SELECT` query.
* It helps in **presenting data in a structured format**.
* You can sort results by one or more columns using **ASC** or **DESC**.
* Useful in combination with `WHERE`, `GROUP BY`, and `HAVING` clauses.
* Sorting by column **names** is preferred for **readability** over sorting by column numbers.

---

## 🧠 Conclusion

The `ORDER BY` clause is a **fundamental tool** in SQL for **organizing query results**. Whether you’re sorting by a single column, multiple columns, or using column numbers, `ORDER BY` enhances data analysis and presentation.

By understanding and using `ORDER BY`, you can:

* Improve the **structure** and **clarity** of your results.
* Create better **reports** and **dashboards**.
* Write **more readable** and **efficient** SQL queries.

---
