
---

# SQL | UNIQUE Constraint

In SQL, constraints play a vital role in maintaining the integrity and accuracy of the data stored in a database. One such constraint is the **UNIQUE constraint**, which ensures that all values in a column (or a combination of columns) are distinct, preventing duplicate entries.

---

## What is the SQL UNIQUE Constraint?

The SQL UNIQUE constraint ensures that all values in a column or a set of columns are different from one another. It can be applied to one or more columns in a table. When applied, the database will reject any insert or update operation that would create a duplicate value in the specified column(s).

The UNIQUE constraint allows **NULL** values, and multiple NULL values are allowed in a column with a UNIQUE constraint because NULL is considered a distinct value in SQL. However, this behavior is different from the PRIMARY KEY constraint, where NULL values are not allowed, as a primary key must uniquely identify each row and cannot have missing or undefined values.

---

## Important Points

- Evaluates to true on an empty subquery.
- Returns true only if there are unique tuples present as the output of the sub-query (two tuples are unique if the value of any attribute of the two tuples differs).
- Returns true if the sub-query has two duplicate rows with at least one attribute as NULL.

---

## Syntax:

```sql
CREATE TABLE table_name (
  column1 datatype UNIQUE,
  column2 datatype,
  ...
);
````

---

## Example of Using the SQL UNIQUE Constraint

### Example 1: Creating a Table with UNIQUE Constraints

Let's create a `Customers` table where the `Email` column must be unique.

```sql
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    Name VARCHAR(100),
    Email VARCHAR(100) UNIQUE,
    Country VARCHAR(50)
);
```

In this case, each customer must have a unique email address. If you try to insert a duplicate email, SQL will raise an error.

```sql
INSERT INTO Customers (CustomerID, Name, Email, Country)
VALUES (1, 'John Doe', 'john.doe@example.com', 'USA');

INSERT INTO Customers (CustomerID, Name, Email, Country)
VALUES (2, 'Jane Smith', 'jane.smith@example.com', 'Canada');

-- This will fail because 'john.doe@example.com' already exists
INSERT INTO Customers (CustomerID, Name, Email, Country)
VALUES (3, 'Alice Johnson', 'john.doe@example.com', 'UK');
```

The third insert will fail because the Email `john.doe@example.com` already exists in the Customers table.

---

### Example 2: Using UNIQUE with Multiple Columns

We can also apply the UNIQUE constraint to multiple columns to ensure that the combination of those columns is unique.

```sql
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    ProductID INT,
    OrderDate DATE,
    UNIQUE (CustomerID, ProductID)
);
```

In this example, the combination of `CustomerID` and `ProductID` must be unique, meaning a customer cannot order the same product more than once.

---

### Example 3: Checking for Unique Values Using Subqueries

SQL allows you to check for uniqueness in subqueries. You can use the UNIQUE keyword in a subquery to ensure that the results do not contain duplicate values.

```sql
SELECT CustomerID
FROM Orders
WHERE UNIQUE (
    SELECT OrderID
    FROM OrderDetails
    WHERE Orders.CustomerID = OrderDetails.CustomerID
);
```

In this example, we check if there are any duplicate `OrderID` values for each customer in the `Orders` table. If the subquery returns unique values, the `CustomerID` will be selected.

---

## Important Points About SQL UNIQUE Constraint

* **Prevents Duplicate Values:** The UNIQUE constraint ensures that no two rows have the same value in the specified column(s).
* **Works with NULL Values:** Unlike the PRIMARY KEY, the UNIQUE constraint allows multiple NULL values, as SQL treats NULL as a distinct value.
* **Can Be Applied to One or More Columns:** The UNIQUE constraint can be applied to a single column or a combination of columns.
* **Does Not Automatically Create an Index:** Although UNIQUE guarantees no duplicate values, it doesn't automatically create an index (but most databases create an index behind the scenes for performance reasons).
* **Can Be Applied Using ALTER TABLE:** You can add or remove the UNIQUE constraint on an existing table using ALTER TABLE.

---
