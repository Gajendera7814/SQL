
---

# Composite Key in SQL

A **composite key** is a primary key that is made up of more than one column to uniquely identify records in a table. Unlike a single-column primary key, a composite key combines **two or more columns** to ensure uniqueness. While any of the individual columns in a composite key might **not be unique** on their own, together they form a unique combination that can uniquely identify each row in the table.

---

## 📌 Key Points to Remember

- A **composite key** is formed from **multiple columns**.
- It ensures **uniqueness** when the **combined values** of the columns are considered together.
- **None** of the columns involved in a composite key can be **NULL**.
- Composite keys help in tables where **single columns cannot guarantee uniqueness**, but a **combination of columns can**.

---

## 🧪 Composite Key Example

### ✅ Creating a database:

```sql
CREATE DATABASE School;
````

### ✅ Using the database:

```sql
USE School;
```

---

### 🏗️ Creating a table with a composite key:

```sql
CREATE TABLE student (
  rollNumber INT, 
  name VARCHAR(30), 
  class VARCHAR(30), 
  section VARCHAR(1), 
  mobile VARCHAR(10),
  PRIMARY KEY (rollNumber, mobile)
);
```

> In this example, the composite key is made up of two columns: `rollNumber` and `mobile`, because all the rows in the `student` table can be uniquely identified by this combination.

---

### 📥 Inserting records into the table:

```sql
INSERT INTO student (rollNumber, name, class, section, mobile) 
VALUES (1, "AMAN", "FOURTH", "B", "9988774455");

INSERT INTO student (rollNumber, name, class, section, mobile) 
VALUES (2, "JOHN", "FIRST", "A", "9988112233");

INSERT INTO student (rollNumber, name, class, section, mobile) 
VALUES (3, "TOM", "FOURTH", "B", "9988777755");

INSERT INTO student (rollNumber, name, class, section, mobile) 
VALUES (4, "RICHARD", "SECOND", "C", "9955663322");
```

---

### 🔍 Querying the records:

```sql
SELECT * FROM student;
```

**Output:**

| rollNumber | name    | class  | section | mobile     |
| ---------- | ------- | ------ | ------- | ---------- |
| 1          | AMAN    | FOURTH | B       | 9988774455 |
| 2          | JOHN    | FIRST  | A       | 9988112233 |
| 3          | TOM     | FOURTH | B       | 9988777755 |
| 4          | RICHARD | SECOND | C       | 9955663322 |

---

## 🤔 When to Use a Composite Key?

A **composite key** is useful in situations where:

* A **single column cannot uniquely identify** a row, but a **combination of columns can**.
* You need to **enforce a relationship** between two or more attributes.
* You want to **maintain data integrity** by ensuring that the **combination of columns remains unique**.

---

## ✅ Conclusion

A **composite key** is a powerful tool in SQL, allowing you to create **unique constraints across multiple columns**. This can be especially helpful in situations where **individual columns do not provide sufficient uniqueness**.

By combining multiple attributes into one **primary key**, you can ensure that each row in a table is **uniquely identifiable**.

> Composite keys are typically used when there's a **natural relationship** between the columns and are often employed in **many-to-many relationships**, where a single column is insufficient for uniqueness.

---
