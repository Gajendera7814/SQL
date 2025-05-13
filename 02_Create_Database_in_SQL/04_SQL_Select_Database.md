
---

## 📘 SQL Select Database

In SQL, selecting a database means choosing which database to use for your subsequent queries. The `USE` statement is used to specify the database in which you will perform your queries.

### ✅ Syntax

```sql
USE database_name;
````

This command selects the specified database for the current session.

### 💡 Example

```sql
USE company_db;
```

This command selects the `company_db` database to perform queries on it.

---

## 🔄 The USE DATABASE Statement

The `USE` statement is a simple command that allows you to switch to the specified database. It is essential to execute the `USE` statement before performing any query or operation in a database.

### ✅ Syntax

```sql
USE database_name;
```

This sets the specified database as the active database for the session.

---

## 💪 Example of SQL Select Database

### Example 1: Selecting a Database

```sql
USE employees_db;
```

This selects the `employees_db` database to be used for subsequent queries.

### Example 2: Using `USE` to Change Databases

```sql
USE school_db;
```

This changes the current active database to `school_db` for the next operations.

---

## 📊 How to Query Data from the Selected Database

Once the database is selected, you can query data from the tables within it. Below are some common SQL operations for querying data, using the `employees` table as an example.

### Table: employees

Assume the `employees` table has the following structure:

* `id` (INTEGER)
* `name` (VARCHAR)
* `position` (VARCHAR)
* `salary` (DECIMAL)
* `department` (VARCHAR)

---

### SQL Code to Create the `employees` Table and Insert Data

```sql
-- Creating the employees table
CREATE TABLE employees (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    position VARCHAR(100),
    salary DECIMAL(10, 2),
    department VARCHAR(100)
);

-- Inserting dummy data into the employees table
INSERT INTO employees (name, position, salary, department) VALUES
('John Doe', 'Manager', 75000.00, 'HR'),
('Jane Smith', 'Developer', 85000.00, 'Engineering'),
('Mary Johnson', 'Designer', 65000.00, 'Marketing'),
('James Brown', 'Developer', 90000.00, 'Engineering'),
('Patricia Williams', 'Sales', 55000.00, 'Sales'),
('Michael Taylor', 'Manager', 95000.00, 'HR'),
('Linda Anderson', 'Developer', 80000.00, 'Engineering'),
('David Thomas', 'Designer', 60000.00, 'Marketing'),
('Jessica Lee', 'HR Specialist', 70000.00, 'HR'),
('Daniel Walker', 'Sales', 57000.00, 'Sales');
```

This code creates the `employees` table and populates it with some example employee data.

---

### 1. **Basic SELECT Statement**

To retrieve all columns from the `employees` table, use the `SELECT` statement.

```sql
SELECT * FROM employees;
```

This query will return all rows and columns from the `employees` table.

---

### 2. **Selecting Specific Columns**

If you only need specific columns, you can specify them by name.

```sql
SELECT name, position, salary FROM employees;
```

This query returns the `name`, `position`, and `salary` columns from the `employees` table.

---

### 3. **Filtering Results with WHERE**

You can filter the data using the `WHERE` clause. For example, to find all employees in the 'Engineering' department:

```sql
SELECT * FROM employees WHERE department = 'Engineering';
```

This query returns all columns for employees who work in the `Engineering` department.

---

### 4. **Sorting Results with ORDER BY**

To sort the results, use the `ORDER BY` clause. For example, to sort the employees by salary in descending order:

```sql
SELECT * FROM employees ORDER BY salary DESC;
```

This query sorts employees by their `salary` in descending order.

---

### 5. **Limiting Results with LIMIT Clause**

To restrict the number of rows returned, use the `LIMIT` clause. For example, to get only the first 3 employees:

```sql
SELECT * FROM employees LIMIT 3;
```

This query returns only the first 3 rows from the `employees` table.

---

### 6. **Aggregating Data with GROUP BY and Aggregation Functions**

You can aggregate data using functions like `AVG()`, `SUM()`, `COUNT()`, etc., along with the `GROUP BY` clause. For example, to calculate the average salary per department:

```sql
SELECT department, AVG(salary) AS avg_salary FROM employees GROUP BY department;
```

This query calculates the average salary (`AVG(salary)`) for each department in the `employees` table.

---

## ✅ Summary

* Use the `USE` statement to select the database for your session.
* The `SELECT` statement retrieves data from tables.
* Use the `WHERE` clause to filter data, the `ORDER BY` clause to sort, and the `LIMIT` clause to restrict results.
* Aggregation functions like `AVG()`, `SUM()`, and `COUNT()` can be used with the `GROUP BY` clause to summarize data.

These are the basic SQL operations for querying and manipulating data from a selected database.

````