
---

## 📘 What is the SQL CREATE TABLE Statement?

The `CREATE TABLE` command in SQL is used to define a **new table** in a database. It specifies:

- Column names
- Data types
- Constraints such as `NOT NULL`, `PRIMARY KEY`, and `CHECK`

This command is foundational in database design and is used to structure data for everything from customer info to product inventories.

---

## 🧾 Syntax

```sql
CREATE TABLE table_name (
    column1 datatype(size),
    column2 datatype(size),
    ...
    columnN datatype(size)
);
````

### 🔑 Key Terms

* `table_name`: The name of the new table.
* `column1, column2, …`: Column names in the table.
* `datatype(size)`: Defines the data type and size for each column.

---

## 💡 Practical Example: Creating a Customer Table

Let’s create a table to store customer information.

```sql
CREATE TABLE Customer (
    CustomerID INT PRIMARY KEY,
    CustomerName VARCHAR(50),
    LastName VARCHAR(50),
    Country VARCHAR(50),
    Age INT CHECK (Age >= 0 AND Age <= 99),
    Phone INT(10)
);
```

### ✅ Output

```
Table created
```

### 📌 Explanation

* `CustomerID` is the **primary key**.
* `CustomerName`, `LastName`, and `Country` are `VARCHAR` fields.
* `Age` has a `CHECK` constraint to allow values only between 0 and 99.
* `Phone` is defined as an integer, though in real-world cases, `VARCHAR` is often better.

---

## 🧩 Inserting Data into the Newly Created Table

Use the `INSERT INTO` statement to add records.

```sql
INSERT INTO Customer (CustomerID, CustomerName, LastName, Country, Age, Phone)
VALUES 
(1, 'Shubham', 'Thakur', 'India', 23, 'xxxxxxxxxx'),
(2, 'Aman', 'Chopra', 'Australia', 21, 'xxxxxxxxxx'),
(3, 'Naveen', 'Tulasi', 'Sri Lanka', 24, 'xxxxxxxxxx'),
(4, 'Aditya', 'Arpan', 'Austria', 21, 'xxxxxxxxxx'),
(5, 'Nishant. Salchichas S.A.', 'Jain', 'Spain', 22, 'xxxxxxxxxx');
```

### ✅ Output

```
Data inserted
```

> ℹ️ **Note**: For large datasets, consider using bulk inserts or data import tools for efficiency.

---

## 🔁 Creating Table from Another Table

SQL also allows creating a new table from an existing one using `CREATE TABLE AS SELECT`.

### 🧾 Syntax

```sql
CREATE TABLE new_table_name AS
SELECT column1, column2, ...
FROM existing_table
WHERE ...;
```

### 💡 Example

```sql
CREATE TABLE SubTable AS
SELECT CustomerID, CustomerName
FROM Customer;
```

### ✅ Output

```
Table created from another table
```

> 📝 **Tip**: Use `SELECT *` to copy all columns.

---

## 🚨 Important Points About SQL CREATE TABLE

1. **Adding Constraints**

   * Define `NOT NULL`, `UNIQUE`, `DEFAULT`, etc.
   * Example:

     ```sql
     Age INT NOT NULL
     ```

2. **Avoiding Errors for Existing Tables**

   * Use `IF NOT EXISTS`:

     ```sql
     CREATE TABLE IF NOT EXISTS Customer (...);
     ```

3. **Choosing the Right Data Types**

   * Example: Use `VARCHAR(50)` for names, `INT` for numeric IDs.

4. **Viewing Table Structure**

   * Use:

     ```sql
     DESC Customer;
     ```

5. **Modifying Table Structure**

   * Use `ALTER TABLE` to add/remove columns, rename fields, etc.

---

## ✅ Summary

* `CREATE TABLE` is essential for database design.
* It allows defining table structure, constraints, and relationships.
* Use `INSERT INTO` to populate tables with data.
* Duplicate structures/data using `CREATE TABLE AS SELECT`.
* Manage and modify tables easily using `DESC` and `ALTER TABLE`.

---

