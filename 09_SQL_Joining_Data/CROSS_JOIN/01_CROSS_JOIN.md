
---
# SQL CROSS JOIN

In SQL, the **CROSS JOIN** is a unique join operation that returns the **Cartesian product** of two or more tables. This means it matches each row from the left table with every row from the right table, resulting in a combination of all possible pairs of records.

---

## What is SQL CROSS JOIN?

Cross Join in SQL produces a result set that contains the **Cartesian product** of two or more tables. Cross join is also called a **Cartesian Join**. When `CROSS JOIN` is used with a `WHERE` clause, it behaves like an `INNER JOIN`, filtering the results based on specific conditions.

**CROSS JOIN** is the best choice when we need to match each row of one table to every other row of another table. It is helpful in many applications where we need to obtain **paired combinations** of records.

---

## Syntax

```sql
SELECT * FROM table1
CROSS JOIN table2;
````

---

## Examples of SQL CROSS JOIN

Let's look at some examples of `CROSS JOIN` statement in SQL to understand its working.

In this CROSS JOIN tutorial, we will use the following two tables in examples:

### Table 1 - CUSTOMER

| ID | NAME        | AGE | PHONE |
| -- | ----------- | --- | ----- |
| 1  | AMIT JAIN   | 21  | 98474 |
| 2  | JATIN VERMA | 47  | 63996 |

### Table 2 - ORDERS

| ORDER\_ID | AMOUNT | PLACED\_ON |
| --------- | ------ | ---------- |
| 101       | 999    | 2023-04-19 |
| 102       | 4999   | 2023-04-20 |

---

## Creating Tables (Sample Data)

To create both these tables on your system, you can write the following SQL code:

```sql
-- Creating Customer Table
CREATE TABLE CUSTOMER (
  ID INT,
  NAME VARCHAR(50),
  AGE INT,
  PHONE INT
);

INSERT INTO CUSTOMER (ID, NAME, AGE, PHONE) VALUES
(1, 'AMIT JAIN', 21, 98474),
(2, 'JATIN VERMA', 47, 63996);

-- Creating Orders Table
CREATE TABLE ORDERS (
  ORDER_ID INT,
  AMOUNT INT,
  PLACED_ON DATE
);

INSERT INTO ORDERS (ORDER_ID, AMOUNT, PLACED_ON) VALUES
(101, 999, '2023-04-19'),
(102, 4999, '2023-04-20');
```

---

## Example 1: CROSS JOIN

In this example, we will use the `CROSS JOIN` command to match the data of the `CUSTOMER` and `ORDERS` table.

### Query:

```sql
SELECT *
FROM CUSTOMER
CROSS JOIN ORDERS;
```

### Output:

| ID | NAME        | AGE | PHONE | ORDER\_ID | AMOUNT | PLACED\_ON |
| -- | ----------- | --- | ----- | --------- | ------ | ---------- |
| 1  | AMIT JAIN   | 21  | 98474 | 101       | 999    | 2023-04-19 |
| 1  | AMIT JAIN   | 21  | 98474 | 102       | 4999   | 2023-04-20 |
| 2  | JATIN VERMA | 47  | 63996 | 101       | 999    | 2023-04-19 |
| 2  | JATIN VERMA | 47  | 63996 | 102       | 4999   | 2023-04-20 |

---

## Important Points About CROSS JOIN

* **CROSS JOIN** performs the **cross-product** of records from two or more joined tables.
* It is used when we want every possible combination of rows to be present in a database's tables.
* SQL **CROSS JOIN** with condition of **WHERE Clause** operates as an **INNER JOIN**; when used without one, it produces the cartesian product of all the rows from all the tables provided in the SQL query.
* **CROSS JOIN** is different from other join types like `INNER JOIN`, `LEFT JOIN`, and `RIGHT JOIN`, as it does **not require a matching condition** between the tables.

---
