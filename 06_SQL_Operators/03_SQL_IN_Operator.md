
---

## SQL IN Operator

The IN Operator in SQL is used to specify multiple values/sub-queries in the WHERE clause. It provides an easy way to handle multiple OR conditions.

We only pass a single condition in the WHERE clause, however there might be situations where we need to select data based on multiple conditions. For such cases, the IN operator is used.

> **Note**: If any of the conditions are passed using the IN operator, they will be considered true.

---

## Syntax

```sql
SELECT column_name FROM table_name
WHERE condition IN (condition_value1, condition_value2 .....);
````

Here, we select the column `column_name` from the table `table_name` where the condition is checked in all the `condition_values` passed with the IN operator.

---

## Example of SQL IN Operator

We will use the following SQL table for our examples below:

```sql
CREATE TABLE Employee (
    Fname VARCHAR(50),
    Lname VARCHAR(50),
    Ssn INT,
    Bdate DATE,
    Address VARCHAR(100),
    Sex CHAR(1),
    Salary DECIMAL(10, 2)
);

INSERT INTO Employee (Fname, Lname, Ssn, Bdate, Address, Sex, Salary) VALUES 
('Chiranjeev', 'Singh', 1, '2002-07-31', 'Delhi', 'M', 1111789.00),
('Harry', 'Stark', 2, '1990-07-31', 'Delhi', 'M', 3333.00),
('Meghna', 'Gururaani', 5, '2002-04-04', 'Almora', 'F', 3433.00),
('Aniket', 'Bhardwaj', 6, '2001-05-05', 'Ponta', 'M', 56564.00),
('Vritti', 'Goel', 7, '2002-03-05', 'Delhi', 'F', 7565.00),
('Aashish', 'Kumar', 8, '2002-08-04', 'Himachal', 'M', 44657.00),
('Siddharth', 'Chaturvedi', 9, '2003-11-10', 'Lucknow', 'M', 244322.00);
```

### Output:

| Fname      | Lname      | Ssn | Bdate      | Address  | Sex | Salary     |
| ---------- | ---------- | --- | ---------- | -------- | --- | ---------- |
| Chiranjeev | Singh      | 1   | 2002-07-31 | Delhi    | M   | 1111789.00 |
| Harry      | Stark      | 2   | 1990-07-31 | Delhi    | M   | 3333.00    |
| Meghna     | Gururaani  | 5   | 2002-04-04 | Almora   | F   | 3433.00    |
| Aniket     | Bhardwaj   | 6   | 2001-05-05 | Ponta    | M   | 56564.00   |
| Vritti     | Goel       | 7   | 2002-03-05 | Delhi    | F   | 7565.00    |
| Aashish    | Kumar      | 8   | 2002-08-04 | Himachal | M   | 44657.00   |
| Siddharth  | Chaturvedi | 9   | 2003-11-10 | Lucknow  | M   | 244322.00  |

---

## Example 1: Basic Use of the IN Operator

**SQL Query to get Fname and Lname of employees who have address in Delhi and Himachal**

```sql
SELECT Fname, Lname FROM employee
WHERE Address IN ('Delhi','Himachal');
```

### Output:

| Fname      | Lname |
| ---------- | ----- |
| Chiranjeev | Singh |
| Harry      | Stark |
| Vritti     | Goel  |
| Aashish    | Kumar |

In this query, we fetched the Fname and Lname of all the employees whose address is either Delhi or Himachal. To do so, we use the IN operator to pass these values to the WHERE clause.

---

## Example 2: SQL IN and NOT IN Operators

We can use the SQL IN with the NOT operator to exclude specified data from our result.

```sql
SELECT Fname FROM employee
WHERE Address NOT IN ('Delhi', 'Lucknow');
```

### Output:

| Fname   |
| ------- |
| Meghna  |
| Aniket  |
| Aashish |

Here, we have created a query to fetch the Fname of all employees whose address is neither Delhi nor Lucknow. We used the NOT operator with IN to exclude these values.

---

## Example 3: Using IN with a Subquery

We have used IN operator with explicit values for conditions. However, we can use the IN operator to select values for the condition from another query. For demonstrating this, we will use another table from the database, `manager`. The contents of the table are given below.

### Manager Table

| Ssn | Department |
| --- | ---------- |
| 5   | Sales      |
| 1   | Technical  |

Now, we will write a query to fetch details of all employees who are managers. This can be done by using nested SELECT queries with the IN operator.

```sql
SELECT * FROM employee
WHERE Ssn IN (SELECT Ssn FROM manager);
```

### Output:

| Fname      | Lname     | Ssn | Bdate      | Address | Sex | Salary     |
| ---------- | --------- | --- | ---------- | ------- | --- | ---------- |
| Chiranjeev | Singh     | 1   | 2002-07-31 | Delhi   | M   | 1111789.00 |
| Meghna     | Gururaani | 5   | 2002-04-04 | Almora  | F   | 3433.00    |

Here, we have selected the Ssn of all managers from the `manager` table and then, we have passed the result of this query to the main query in the IN operator, which will fetch the details of all employees who have same Ssn as fetched from the nested query.

---

## 🔑 Key Takeaways About the SQL IN Operator

* The SQL IN operator allows you to specify multiple values in a WHERE clause.
* It checks if a specified value matches any value in a list.
* It simplifies querying for records that match multiple criteria without needing to use multiple OR conditions.
* The syntax is straightforward: `WHERE column_name IN (value1, value2, ...)`.
* It is commonly used with SELECT, INSERT, UPDATE, and DELETE statements for filtering or updating data based on multiple values.
* Using the IN operator can make SQL queries more concise and readable.

---

## ✅ Conclusion

The SQL IN operator is a powerful tool for filtering data based on multiple values. By eliminating the need for multiple OR conditions, it makes your queries more concise and readable. Whether you’re filtering records from a list of values or using a subquery, the IN operator offers an elegant and efficient solution. Mastering the IN operator can help you write cleaner and more efficient SQL queries that scale with your data.

---