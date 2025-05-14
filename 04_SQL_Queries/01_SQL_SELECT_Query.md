
---

# SQL SELECT Query


The `SELECT` query in SQL is one of the most commonly used SQL commands to retrieve data from a database. With the `SELECT` command in SQL, users can access data and retrieve specific records based on various conditions, making it an essential tool for managing and analyzing data.

---

## What is the SQL SELECT Statement?

The `SELECT` clause is the first clause and is one of the last clauses of the `SELECT` statement that the database server evaluates. The reason for this is that before we can determine what to include in the final result set, we need to know all of the possible columns that could be included in the final result set.

The `SELECT` statement in SQL is used to fetch or retrieve data from a database. It allows users to access the data and retrieve specific data based on specific conditions. We can fetch either the entire table or according to some specified rules. The data returned is stored in a result table. With the `SELECT` clause of a `SELECT` command statement, we specify the columns that we want to be displayed in the query result.

### Syntax:

```sql
SELECT column1, column2, … FROM table_name;
````

---

## Examples of SELECT Statement

Let’s look at some examples of the SQL `SELECT` statement to understand it better. To demonstrate the examples, let’s create a table that will be used in the examples:

### Create Table:

```sql
CREATE TABLE Customer(
    CustomerID INT PRIMARY KEY,
    CustomerName VARCHAR(50),
    LastName VARCHAR(50),
    Country VARCHAR(50),
    Age INT(2),
    Phone INT(10)
);
```

### Insert Sample Data into the `Customer` Table:

```sql
INSERT INTO Customer (CustomerID, CustomerName, LastName, Country, Age, Phone)
VALUES 
(1, 'Shubham', 'Thakur', 'India', 23, 'xxxxxxxxxx'),
(2, 'Aman', 'Chopra', 'Australia', 21, 'xxxxxxxxxx'),
(3, 'Naveen', 'Tulasi', 'Sri Lanka', 24, 'xxxxxxxxxx'),
(4, 'Aditya', 'Arpan', 'Austria', 21, 'xxxxxxxxxx'),
(5, 'Nishant Salchichas S.A.', 'Jain', 'Spain', 22, 'xxxxxxxxxx');
```

### Output:

```
create table
```

---

### Example 1: Select Specific Columns

In this example, we will fetch only the `CustomerName` and `LastName` from the table `Customer`:

#### Query:

```sql
SELECT CustomerName, LastName 
FROM Customer;
```

### Output:

| CustomerName | LastName |
| ------------ | -------- |
| Shubham      | Thakur   |
| Aman         | Chopra   |
| Naveen       | Tulasi   |
| Aditya       | Arpan    |
| Nishant      | Jain     |

---

### Example 2: Select All Columns

In this example, we will fetch all the fields from the table `Customer`:

#### Query:

```sql
SELECT * FROM Customer;
```

### Output:

| CustomerID | CustomerName | LastName | Country   | Age | Phone      |
| ---------- | ------------ | -------- | --------- | --- | ---------- |
| 1          | Shubham      | Thakur   | India     | 23  | xxxxxxxxxx |
| 2          | Aman         | Chopra   | Australia | 21  | xxxxxxxxxx |
| 3          | Naveen       | Tulasi   | Sri Lanka | 24  | xxxxxxxxxx |
| 4          | Aditya       | Arpan    | Austria   | 21  | xxxxxxxxxx |
| 5          | Nishant      | Jain     | Spain     | 22  | xxxxxxxxxx |

---

### Example 3: SELECT Statement with WHERE Clause

Suppose we want to see table values with specific conditions. The `WHERE` Clause is used with the `SELECT` statement. In this example, we filter customers who are 21 years old.

#### Query:

```sql
SELECT CustomerName 
FROM Customer 
WHERE Age = 21; 
```

### Output:

| CustomerName |
| ------------ |
| Aman         |
| Aditya       |

---

### Example 4: SELECT with GROUP BY Clause

In this example, we will use the `SELECT` statement with the `GROUP BY` clause to group rows and perform aggregation. Here, we count orders per customer.

#### Query:

```sql
SELECT Customer_id, COUNT(*) AS order_count
FROM Orders
GROUP BY Customer_id;
```

### Output:

| Customer\_id | order\_count |
| ------------ | ------------ |
| 1            | 5            |
| 2            | 3            |

---

### Example 5: SELECT Statement with HAVING Clause

Use `HAVING` to filter results after grouping. Consider the following database for fetching departments with a total salary above 50,000. Use `WHERE` for row-level filtering, and `HAVING` for group-level filtering.

#### Query:

```sql
SELECT Department, SUM(Salary) AS Salary
FROM employee
GROUP BY Department
HAVING SUM(Salary) >= 50000;
```

### Output:

| Department | Salary |
| ---------- | ------ |
| Sales      | 75000  |
| Marketing  | 60000  |

---

### Example 6: SELECT Statement with ORDER BY Clause in SQL

In this example, we will use the `SELECT` statement with the `ORDER BY` clause. Here, we sort the results by `Age` in descending order.

#### Query:

```sql
SELECT * FROM Customer ORDER BY Age DESC;
```

### Output:

| CustomerID | CustomerName | LastName | Country   | Age | Phone      |
| ---------- | ------------ | -------- | --------- | --- | ---------- |
| 3          | Naveen       | Tulasi   | Sri Lanka | 24  | xxxxxxxxxx |
| 1          | Shubham      | Thakur   | India     | 23  | xxxxxxxxxx |
| 5          | Nishant      | Jain     | Spain     | 22  | xxxxxxxxxx |
| 2          | Aman         | Chopra   | Australia | 21  | xxxxxxxxxx |
| 4          | Aditya       | Arpan    | Austria   | 21  | xxxxxxxxxx |

---

## Tips to Master SELECT

| Goal                | Technique                                                     |
| ------------------- | ------------------------------------------------------------- |
| Fetch unique values | `SELECT DISTINCT column FROM table;`                          |
| Limit result rows   | `SELECT * FROM table LIMIT 10;` (MySQL/PostgreSQL)            |
| Aliases for clarity | `SELECT CustomerName AS Name FROM Customer;`                  |
| Join tables         | `SELECT a.*, b.* FROM TableA a JOIN TableB b ON a.id = b.id;` |

---

## Conclusion

The SQL `SELECT` statement is an essential tool for retrieving and analyzing data from relational databases. Whether we’re fetching specific columns or using advanced clauses like `WHERE`, `GROUP BY`, and `ORDER BY`, the `SELECT` query provides flexibility for efficient data retrieval. By understanding how to use the `SELECT` statement and combining it with various clauses, we can efficiently filter, aggregate, and sort data to meet our needs.

---
