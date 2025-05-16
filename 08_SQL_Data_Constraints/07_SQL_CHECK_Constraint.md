
---

# SQL | CHECK Constraint

In SQL, one such constraint is the **CHECK** constraint, which allows enforcement of domain integrity by limiting the values that can be inserted or updated in a column. By using CHECK, we can define conditions on a column’s values and ensure that they adhere to specific rules.

In this article, we will explore the SQL CHECK constraint in detail, discussing its purpose, syntax, examples, and best practices.

---

## What is the SQL CHECK Constraint?

The CHECK constraint in SQL is used to limit the range or set of values that can be inserted into a column. It ensures that the data entered into a column meets a certain condition or rule. The CHECK constraint can be applied to a column when the table is created or altered. If any data being inserted or updated violates the CHECK condition, the database will return an error and the operation will be prevented.

---

## Syntax:

```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype CHECK (condition),
    ...
);
````

---

## Key Points About the CHECK Constraint

* **Domain Integrity**: It ensures that the values in a column meet specified conditions, thus helping maintain valid data in the database.
* **Used with CREATE or ALTER**: The CHECK constraint can be defined when creating a table or added to an existing table.
* **Can Be Combined with Other Constraints**: You can use CHECK along with other constraints like PRIMARY KEY, FOREIGN KEY, and NOT NULL to define more comprehensive rules for the table data.
* **Row-level Constraints**: Unlike column-level constraints that affect individual columns, a CHECK constraint can apply to multiple columns at once if needed.

---

## Examples of Using the CHECK Constraint

Let’s look at some practical examples to better understand how the CHECK constraint works in SQL.

---

### Example 1: Applying CHECK on a Single Column

In this example, we create a `Customers` table with an `Age` column that must contain values between 18 and 120. The CHECK constraint ensures that no invalid age is inserted into the table.

**Query:**

```sql
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    Name VARCHAR(50),
    Age INT CHECK (Age >= 18 AND Age <= 120)
);
```

```sql
-- Valid insert
INSERT INTO Customers (CustomerID, Name, Age)
VALUES (1, 'John Doe', 25);

-- Invalid insert
INSERT INTO Customers (CustomerID, Name, Age)
VALUES (2, 'Jane Smith', 15);  -- This will fail due to the CHECK constraint
```

The `Age` column has a CHECK constraint that ensures the value must be between 18 and 120. If you attempt to insert an age outside this range, the database will throw an error.

---

### Example 2: CHECK Constraint with Multiple Columns

We can also use the CHECK constraint across multiple columns. For instance, let's say we have an `Employee` table, and we want to ensure that the `Salary` is positive and the `Age` is greater than or equal to 18.

**Query:**

```sql
CREATE TABLE Employee (
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(50),
    Age INT,
    Salary DECIMAL(10, 2),
    CHECK (Age >= 18 AND Salary > 0)
);
```

```sql
-- Valid insert
INSERT INTO Employee (EmployeeID, Name, Age, Salary)
VALUES (1, 'Alice Johnson', 30, 50000);

-- Invalid insert (age < 18)
INSERT INTO Employee (EmployeeID, Name, Age, Salary)
VALUES (2, 'Bob Lee', 16, 45000);  -- This will fail due to the CHECK constraint
```

The CHECK constraint ensures that both conditions are satisfied: the employee must be at least 18 years old, and the salary must be greater than 0. This kind of constraint is useful when multiple columns are involved in the rule.

---

### Example 3: Adding a CHECK Constraint with ALTER TABLE

We can add a CHECK constraint to an existing table using the `ALTER TABLE` statement.

**Query:**

```sql
ALTER TABLE Employee
ADD CONSTRAINT chk_salary CHECK (Salary >= 30000);
```

This adds a CHECK constraint named `chk_salary` to the `Employee` table, ensuring that the `Salary` column has a minimum value of 30,000. If you attempt to insert or update a record with a salary lower than 30,000, the operation will fail.

---

## Best Practices for Using SQL CHECK Constraint

* **Be Specific with Conditions**: Make sure the conditions in your CHECK constraint are clear and specific to avoid errors during data insertion. For instance, if you’re applying a constraint on an age column, ensure that the range is reasonable.
* **Use Logical Operators**: Use logical operators like `AND`, `OR`, and `NOT` to combine multiple conditions within a CHECK constraint. This allows you to create more complex rules and maintain data integrity.
* **Test Constraints Before Applying**: Before applying a CHECK constraint to an existing table, test it in a development environment to ensure it does not unintentionally block valid data operations.
* **Be Aware of Database Support**: While most relational database systems (like MySQL, SQL Server, PostgreSQL, and Oracle) support the CHECK constraint, some older versions may have limitations or quirks. Always check the documentation for your specific database version.

---
