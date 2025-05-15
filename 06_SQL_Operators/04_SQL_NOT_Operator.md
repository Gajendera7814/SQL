
---

## What is the SQL NOT Operator?

The SQL `NOT` operator is used to **reverse the boolean result** of a condition in SQL. It helps in retrieving records that **do not match a specific condition**. It is mostly used to specify what should **not be included** in the results table.

---

## Syntax

```sql
SELECT column1, column2, …
FROM table_name
WHERE NOT condition;
````

---

## Examples of SQL NOT Operator

### Table: `Customers`

```sql
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    CustomerName VARCHAR(50),
    City VARCHAR(50),
    PostalCode VARCHAR(10),
    Country VARCHAR(50)
);

INSERT INTO Customers (CustomerID, CustomerName, City, PostalCode, Country)
VALUES
    (1, 'John Wick', 'New York', '1248', 'USA'),
    (2, 'Around the Horn', 'London', 'WA1 1DP', 'UK'),
    (3, 'Rohan', 'New Delhi', '100084', 'India');
```

**Table Data:**

| CustomerID | CustomerName    | City      | PostalCode | Country |
| ---------- | --------------- | --------- | ---------- | ------- |
| 1          | John Wick       | New York  | 1248       | USA     |
| 2          | Around the Horn | London    | WA1 1DP    | UK      |
| 3          | Rohan           | New Delhi | 100084     | India   |

---

### Example 1: Using SQL NOT to Exclude a Specific Value

**Query:**

```sql
SELECT * 
FROM Customers
WHERE NOT Country = 'UK';
```

**Output:**

| CustomerID | CustomerName | City      | PostalCode | Country |
| ---------- | ------------ | --------- | ---------- | ------- |
| 1          | John Wick    | New York  | 1248       | USA     |
| 3          | Rohan        | New Delhi | 100084     | India   |

In this example, the `NOT` operator filters out customers from the **UK** and returns all other customers.

---

### Example 2: Using SQL NOT with IN Operator

**Query:**

```sql
SELECT * 
FROM Customers
WHERE NOT Country IN ('USA', 'UK');
```

**Output:**

| CustomerID | CustomerName | City      | PostalCode | Country |
| ---------- | ------------ | --------- | ---------- | ------- |
| 3          | Rohan        | New Delhi | 100084     | India   |

Here, the `NOT IN` condition filters out customers from both **USA** and **UK**, and returns only customers from other countries.

---

### Example 3: Using SQL NOT with LIKE Operator

**Query:**

```sql
SELECT * 
FROM Customers
WHERE NOT CustomerName LIKE 'R%';
```

**Output:**

| CustomerID | CustomerName    | City     | PostalCode | Country |
| ---------- | --------------- | -------- | ---------- | ------- |
| 1          | John Wick       | New York | 1248       | USA     |
| 2          | Around the Horn | London   | WA1 1DP    | UK      |

In this query, the `NOT LIKE` condition filters out customers whose name **starts with the letter 'R'**, returning all others.

---

### Example 4: Using SQL NOT with NULL Values

**Query:**

```sql
SELECT * 
FROM Customers
WHERE NOT PostalCode IS NULL;
```

**Output:**

| CustomerID | CustomerName    | City      | PostalCode | Country |
| ---------- | --------------- | --------- | ---------- | ------- |
| 1          | John Wick       | New York  | 1248       | USA     |
| 2          | Around the Horn | London    | WA1 1DP    | UK      |
| 3          | Rohan           | New Delhi | 100084     | India   |

This query excludes customers who have a **NULL value** for `PostalCode`.

---

### Example 5: Using NOT with AND Operator

**Query:**

```sql
SELECT * 
FROM Customers
WHERE NOT Country = 'USA' AND NOT Country = 'UK';
```

**Output:**

| CustomerID | CustomerName | City      | PostalCode | Country |
| ---------- | ------------ | --------- | ---------- | ------- |
| 3          | Rohan        | New Delhi | 100084     | India   |

---

## 🔑 Key Takeaways About NOT Operator

* `NOT` operator returns **opposite results** or **negative results**.
* It **negates boolean conditions** in the `WHERE` clause.
* It is used to **exclude specific data** from the result set.
* It can also be **combined with other operators** like `LIKE`, `BETWEEN`, and `IN`.

---

## 📌 Conclusion

The **SQL NOT** operator is an essential tool for SQL developers. Whether you’re excluding specific records, filtering null values, or creating more complex logical conditions, the `NOT` operator helps you fine-tune your queries.

---
