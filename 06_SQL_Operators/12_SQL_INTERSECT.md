
---

## What is SQL INTERSECT?

The INTERSECT clause in SQL is used to combine two SELECT statements but the dataset returned by the INTERSECT statement will be the intersection of the data sets of the two SELECT statements. In simple words, the INTERSECT statement will return only those rows that will be common to both of the SELECT statements.

The INTERSECT operator is a set operation in SQL, similar to UNION and EXCEPT. While UNION combines results from two queries and removes duplicates, INTERSECT returns only the records that exist in both queries, ensuring uniqueness.

---

## Key Characteristics of SQL INTERSECT:

- Returns only the common rows between two result sets.  
- Ensures uniqueness by automatically removing duplicate rows.  
- Requires that both SELECT statements have the same number of columns.  
- The data types of corresponding columns in both queries must be compatible.  

---

## Syntax:

```sql
SELECT column1, column2, ....
FROM table1
WHERE condition
INTERSECT
SELECT column1, column2, ....
FROM table2
WHERE condition;
````

---

## Examples of SQL INTERSECT

Let’s consider two tables: the Customers table, which holds customer details, and the Orders table, which contains information about customer purchases. By applying the INTERSECT operator, we can retrieve customers who exist in both tables, meaning those who have made purchases.

---

### Customers Table

*(Customers table details not provided)*

### Orders Table

*(Orders table details not provided)*

---

### Example 1: Basic INTERSECT Query

In this example, we retrieve customers who exist in both the Customers and Orders tables. The INTERSECT operator ensures that only those customers who have placed an order appear in the result.

**Query:**

```sql
SELECT CustomerID
FROM Customers
INTERSECT
SELECT CustomerID
FROM Orders;
```

**Output:**

| CustomerID |
| ---------- |
| 2          |
| 3          |
| 5          |
| 6          |
| 7          |
| 8          |

**Explanation:**

* The query returns only those customers who appear in both the Customers and Orders tables.
* If a customer exists in Customers but has never placed an order, they won’t appear in the result.
* Customer IDs 2, 3, 5, 6, 7, and 8 appear in both the Customers and Orders tables.

---

### Example 2: Using INTERSECT with BETWEEN Operator

In this example, we apply the INTERSECT operator along with the BETWEEN condition to filter records based on a specified range. The query retrieves customers whose CustomerID falls between 3 and 8 and who have placed an order. The result contains only the common CustomerID values that meet both conditions.

**Query:**

```sql
SELECT CustomerID
FROM Customers
WHERE CustomerID BETWEEN 3 AND 8
INTERSECT
SELECT CustomerID
FROM Orders;
```

**Output:**

| CustomerID |
| ---------- |
| 3          |
| 5          |
| 6          |
| 7          |
| 8          |

**Explanation:**

* The first SELECT statement filters customers with CustomerID between 3 and 8.
* The INTERSECT operator ensures that only customers from this filtered set who have placed an order are included in the result.
* Customers 3, 5, 6, 7, and 8 fall within the specified range (3 to 8).

---

### Example 3: Using INTERSECT with LIKE Operator

In this example, we use the INTERSECT operator along with the LIKE operator to find common customers whose FirstName starts with the letter 'J' in both the Customers and Orders tables.

**Query:**

```sql
SELECT CustomerID
FROM Customers
WHERE FirstName LIKE 'J%'
INTERSECT
SELECT CustomerID
FROM Orders;
```

**Output:**

| CustomerID |
| ---------- |
| 2          |

**Explanation:**

* The query finds customers whose first name starts with 'J' in both the Customers and Orders tables.
* The INTERSECT operator ensures that only those customers who have placed an order are included in the result.
* The final output includes Customer 2 (Jane) only, as per the given example.

---

## Important Notes About SQL INTERSECT

* **Column Count & Data Types:** Both SELECT statements must have the same number of columns with compatible data types.
* **Performance Considerations:** INTERSECT can be slower on large datasets as it performs row-by-row comparison. Indexing can help optimize performance.
* **NULL Handling:** Unlike comparison operators, INTERSECT treats NULL values as equal, meaning if both queries return a row with NULL, it will be included in the result.
* **Alternative Approach:** In cases where INTERSECT is not supported (e.g., MySQL), you can achieve the same result using INNER JOIN.

---
