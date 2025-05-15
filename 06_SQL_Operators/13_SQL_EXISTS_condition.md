
---

## What is SQL EXISTS?

The EXISTS condition is primarily used to check the existence of rows returned by a subquery. It’s commonly used in scenarios where you need to check if a record exists in a related table, and you want to perform an action based on that result.

---

## Syntax:

```sql
SELECT column_name(s)
FROM table_name
WHERE EXISTS (
    SELECT column_name(s)
    FROM subquery_table
    WHERE condition
);
````

* **EXISTS:** The boolean operator that checks if a subquery returns rows.
* **Subquery:** A nested SELECT query that returns data for evaluation.
* **Condition:** The condition applied to the subquery.

---

## Examples of SQL EXISTS

Consider the following two relation "Customers" and "Orders".

### Customers Table

*(Details not provided)*

### Orders Table

*(Details not provided)*

---

### Example 1 : Using EXISTS with SELECT

To fetch the first and last name of the customers who placed at least one order.

**Query:**

```sql
SELECT fname, lname 
FROM Customers 
WHERE EXISTS (SELECT * 
              FROM Orders 
              WHERE Customers.customer_id = Orders.c_id);
```

**Output:**

*(Output not provided)*

---

### Example 2 : Using NOT with EXISTS

Fetch last and first name of the customers who has not placed any order.

**Query:**

```sql
SELECT lname, fname
FROM Customers
WHERE NOT EXISTS (SELECT * 
                  FROM Orders 
                  WHERE Customers.customer_id = Orders.c_id);
```

**Output:**

*(Output not provided)*

---

### Example 3 : Using EXISTS condition with DELETE statement

Delete the record of all the customer from Order Table whose last name is 'Mehra'.

**Query:**

```sql
DELETE 
FROM Orders
WHERE EXISTS (SELECT *
              FROM customers
              WHERE Customers.customer_id = Orders.c_id
              AND Customers.lname = 'Mehra');
SELECT * FROM Orders;
```

**Output:**

*(Output not provided)*

---

### Example 4 : Using EXISTS condition with UPDATE statement

Update the lname as 'Kumari' of customer in Customer Table whose customer\_id is 401.

**Query:**

```sql
UPDATE Customers
SET lname = 'Kumari'
WHERE EXISTS (SELECT *
              FROM Customers
              WHERE customer_id = 401);
SELECT * FROM Customers;
```

**Output:**

*(Output not provided)*

---

## When to Use SQL EXISTS

The EXISTS condition is particularly useful in the following scenarios:

* **Checking Data Existence:** You can use EXISTS to check if related data exists in another table before performing an action (e.g., selecting, updating, deleting).
* **Performance:** EXISTS is often more efficient than using IN when dealing with large datasets, as it stops searching once a match is found.
* **Correlated Subqueries:** EXISTS is ideal for correlated subqueries, where the subquery refers to the outer query’s values.

---

## Differences Between EXISTS and IN

* EXISTS is used for checking the existence of rows, while IN checks if a value matches any value from a list or subquery result.
* EXISTS is more efficient when the subquery results in a large number of rows.
* IN works well for small datasets or static lists of values.

---
