
---

# 📥 SQL Query to Insert Multiple Rows

In SQL, the `INSERT` statement is used to **add new records** to a database table. When you need to insert **multiple rows in a single query**, the `INSERT` statement becomes efficient.

In this article, we will learn different methods such as:

- Using basic `INSERT` statements
- Utilizing `INSERT INTO ... SELECT` for bulk inserts
- Handling transactions for larger datasets
- Advanced techniques like bulk inserts
- Optimization tips for efficiency

---

## 🧾 How to Insert Multiple Rows in SQL

Insertion in a table is a **DML (Data Manipulation Language)** operation in SQL.

To store data, we use the `INSERT` statement.

Inserting multiple rows can be done in **several ways**:

- Basic `INSERT` with multiple `VALUES`
- `INSERT INTO ... SELECT`
- Using **transactions** for batch inserts

---

## 🏗️ Creating a Table

We will create a table `Employees` with 4 columns.

### 🛠️ Query:

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    EmployeeName VARCHAR(100),
    Age INT,
    Department VARCHAR(50)
);
````

This table, `Employees`, includes:

* `EmployeeID`
* `EmployeeName`
* `Age`
* `Department`

It will be used in all examples below.

---

## 🧱 Basic INSERT for Multiple Rows

The simplest way to insert multiple rows is using one `INSERT INTO` statement with **multiple sets of values**.

### 🛠️ Query:

```sql
INSERT INTO Employees (EmployeeID, EmployeeName, Age, Department)
VALUES
    (1, 'John Doe', 30, 'Engineering'),
    (2, 'Jane Smith', 28, 'Marketing'),
    (3, 'Sam Brown', 35, 'Sales'),
    (4, 'Lucy Green', 25, 'Human Resources');
```

### 🖥️ Output:

```text
INSERT_Multiple_Rows
Insert Multiple Rows
```

This query inserts **four rows** into the `Employees` table efficiently.

---

## 🔄 Using INSERT INTO ... SELECT for Inserting Multiple Rows

The `INSERT INTO ... SELECT` method is helpful when you insert data from another **query or table**.

Often used for:

* **Data transfers**
* **Derived data inserts**

### 🧾 Creating NewEmployees Table

```sql
CREATE TABLE NewEmployees (
    EmployeeID INT PRIMARY KEY,
    EmployeeName VARCHAR(100),
    Age INT,
    Department VARCHAR(50)
);
```

### 🧾 Inserting Sample Data into NewEmployees

```sql
INSERT INTO NewEmployees (EmployeeID, EmployeeName, Age, Department)
VALUES
    (5, 'Alice Johnson', 29, 'HR'),
    (6, 'Bob Martin', 32, 'Finance'),
    (7, 'Charlie Baker', 28, 'Marketing'),
    (8, 'David Lee', 40, 'Engineering'),
    (9, 'Eva Davis', 22, 'Sales');
```

### 🖥️ Output:

| EmployeeID | EmployeeName  | Age | Department  |
| ---------- | ------------- | --- | ----------- |
| 5          | Alice Johnson | 29  | HR          |
| 6          | Bob Martin    | 32  | Finance     |
| 7          | Charlie Baker | 28  | Marketing   |
| 8          | David Lee     | 40  | Engineering |
| 9          | Eva Davis     | 22  | Sales       |

---

## 🔎 Insert From NewEmployees Where Age > 30

### 🛠️ Query:

```sql
INSERT INTO Employees (EmployeeID, EmployeeName, Age, Department)
SELECT EmployeeID, EmployeeName, Age, Department
FROM NewEmployees
WHERE Age > 30;
```

### 🖥️ Output:

| EmployeeID | EmployeeName | Age | Department      |
| ---------- | ------------ | --- | --------------- |
| 1          | John Doe     | 30  | Engineering     |
| 2          | Jane Smith   | 28  | Marketing       |
| 3          | Sam Brown    | 35  | Sales           |
| 4          | Lucy Green   | 25  | Human Resources |
| 6          | Bob Martin   | 32  | Finance         |
| 8          | David Lee    | 40  | Engineering     |

---

## 🔐 Inserting Data Using Transactions

When inserting **large amounts of data**, use **SQL transactions** to ensure reliability.

A **transaction** groups multiple SQL operations. If one fails, the **entire transaction is rolled back**.

---

### 🛠️ Query:

```sql
BEGIN TRANSACTION;

    INSERT INTO Customers (CustomerID, CustomerName, ContactName, Country)
    VALUES (5, 'Sarah White', 'John White', 'Canada');
    
    INSERT INTO Customers (CustomerID, CustomerName, ContactName, Country)
    VALUES (6, 'Mohamed Ibrahim', 'Ahmed Ibrahim', 'UAE');
    
    -- If any error occurs, the transaction will be rolled back

COMMIT;
```

> ⚠️ If any `INSERT` inside the block fails, use `ROLLBACK` to cancel the entire transaction.

---

### 🖥️ Sample Output (Employees Table after all inserts):

| EmployeeID | EmployeeName | Age | Department      |
| ---------- | ------------ | --- | --------------- |
| 1          | John Doe     | 30  | Engineering     |
| 2          | Jane Smith   | 28  | Marketing       |
| 3          | Sam Brown    | 35  | Sales           |
| 4          | Lucy Green   | 25  | Human Resources |
| 6          | Bob Martin   | 32  | Finance         |
| 8          | David Lee    | 40  | Engineering     |
| 35         | Carlos Diaz  | 40  | Engineering     |
| 36         | Mia Clark    | 33  | Sales           |

---

## ✅ Conclusion

Inserting multiple rows in SQL can be performed using:

* Basic `INSERT INTO ... VALUES`
* `INSERT INTO ... SELECT`
* `TRANSACTIONS` for batch reliability

For more advanced scenarios, consider:

* **Bulk insert tools**
* **MERGE** statements
* **Stored procedures** with loops or batch commits

SQL provides powerful and **efficient tools** for inserting large volumes of data while maintaining **data integrity**.

---
