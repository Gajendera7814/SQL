
---

# SQL | ALL and ANY


In SQL, the ALL and ANY operators are logical operators used to compare a value with a set of values returned by a subquery. These operators provide powerful ways to filter results based on a range of conditions.

---

## What is the SQL ALL Operator?

The ALL operator is used to compare a value with all the values returned by a subquery. The condition will be evaluated to TRUE if the value meets the specified condition for every value in the result set of the subquery.

- The ALL must be preceded by comparison operators and evaluates true if all of the subqueries values meet the condition.  
- ALL is used with SELECT, WHERE, and HAVING statements.

---

## Syntax:

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name comparison_operator ALL
  (SELECT column_name
   FROM table_name
   WHERE condition(s));
````

* **comparison\_operator:** This is the comparison operator that can be one of =, >, <, >=, <=, <>, etc.
* **subquery:** A query that returns the set of values to be compared with the column in the outer query.

---

## How to Use SQL ALL with SELECT, WHERE, and HAVING

The ALL operator can be used in conjunction with SELECT, WHERE, and HAVING statements to refine your data filtering.

---

### Let's Consider the following Products Table and OrderDetails Table for explaining the examples.

*Products Table*

*(No table data provided)*

*OrderDetails Table*

*(No table data provided)*

---

## Queries

### Example 1 : Retrieve all product names from the Products table.

```sql
SELECT ALL ProductName 
FROM Products
WHERE TRUE;
```

**Output:**

This query retrieves all product names from the Products table because TRUE always evaluates as true for every row.

---

### Example 2: Retrieve product names if all records in the OrderDetails table have a quantity of 6 or 2.

```sql
SELECT ProductName
FROM Products
WHERE ProductID = ALL (SELECT ProductID
                       FROM OrderDetails
                       WHERE Quantity = 6 OR Quantity = 2);
```

**Output:**

This query ensures that the product names returned have ALL quantities of 6 or 2 in the OrderDetails table.

---

### Example 3 : Find the OrderIDs where the maximum quantity in the order exceeds the average quantity of all orders.

```sql
SELECT OrderID
FROM OrderDetails
GROUP BY OrderID
HAVING MAX(Quantity) > ALL (SELECT AVG(Quantity) 
                            FROM OrderDetails 
                            GROUP BY OrderID);
```

**Output:**

ANY

This query filters out OrderIDs where the maximum quantity is greater than the average quantity of the orders.

---

## What is the SQL ANY Operator?

ANY compares a value to each value in a list or results from a query and evaluates to true if the result of an inner query contains at least one row.

* ANY returns true if any of the subqueries values meet the condition.
* ANY must be preceded by comparison operators.

---

## Syntax:

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name comparison_operator ANY
  (SELECT column_name
   FROM table_name
   WHERE condition(s));
```

---

## How to Use SQL ANY with SELECT, WHERE, and HAVING

---

### Example 1 : Find distinct category IDs of products that appear in the OrderDetails table.

```sql
SELECT DISTINCT CategoryID
FROM Products 
WHERE ProductID = ANY (SELECT ProductID 
                       FROM OrderDetails);
```

**Output:**

This query finds the distinct CategoryIDs of products that exist in the OrderDetails table.

---

### Example 2 : Find product names with a quantity of 9 in the OrderDetails table.

```sql
SELECT ProductName
FROM Products
WHERE ProductID = ANY (SELECT ProductID
                       FROM OrderDetails
                       WHERE Quantity = 9);
```

**Output:**

*OrderDetails*
*product names*

This query retrieves product names where at least one record in the OrderDetails table has a quantity of 9.

---

## Differences Between SQL ALL and ANY

* ALL requires that the condition be true for every value in the subquery result, while ANY only needs the condition to be true for at least one value in the subquery.
* ALL is used when you want to compare a value against all values in the subquery, while ANY is useful when you want to compare a value against any one of the values.

---
