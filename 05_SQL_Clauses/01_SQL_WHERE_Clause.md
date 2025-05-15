
---

## What is the SQL WHERE Clause?

The SQL `WHERE` clause is used to specify a condition while fetching or modifying data in a database. It filters the rows that are affected by the `SELECT`, `UPDATE`, `DELETE`, or `INSERT` operations. The condition can range from simple comparisons to complex expressions, enabling precise targeting of the data.

### Syntax:

```sql
SELECT column1, column2 
FROM table_name 
WHERE column_name operator value;
````

### Parameter Explanation:

* **column1, column2**: fields in the table
* **table\_name**: name of the table
* **column\_name**: name of the field used for filtering
* **operator**: operation to be considered for filtering
* **value**: exact value or pattern to get related data in the result

---

## Examples of WHERE Clause in SQL

We will create a basic employee table structure in SQL for performing all the `WHERE` clause operations.

### Table Creation and Insertion

```sql
CREATE TABLE Emp1 (
    EmpID INT PRIMARY KEY,
    Name VARCHAR(50),
    Country VARCHAR(50),
    Age INT(2),
    mob INT(10)
);

-- Insert some sample data into the Emp1 table
INSERT INTO Emp1 (EmpID, Name, Country, Age, mob)
VALUES 
(1, 'Shubham',  'India', 23, 738479734),
(2, 'Aman',     'Australia', 21, 436789555),
(3, 'Naveen',   'Sri lanka', 24, 34873847),
(4, 'Aditya',   'Austria', 21, 328440934),
(5, 'Nishant',  'Spain', 22, 73248679);
```

#### Output:

| EmpID | Name    | Country   | Age | mob       |
| ----- | ------- | --------- | --- | --------- |
| 1     | Shubham | India     | 23  | 738479734 |
| 2     | Aman    | Australia | 21  | 436789555 |
| 3     | Naveen  | Sri lanka | 24  | 34873847  |
| 4     | Aditya  | Austria   | 21  | 328440934 |
| 5     | Nishant | Spain     | 22  | 73248679  |

---

### Example 1: WHERE Clause with Logical Operators

**Query:** To fetch records of employees with age equal to 24.

```sql
SELECT * FROM Emp1 WHERE Age = 24;
```

**Query:** To fetch the EmpID, Name, and Country of employees with Age greater than 21.

```sql
SELECT EmpID, Name, Country FROM Emp1 WHERE Age > 21;
```

---

### Example 2: WHERE Clause with `BETWEEN` Operator

It is used to fetch filtered data in a given range inclusive of two values.

**Syntax:**

```sql
SELECT column1, column2 
FROM table_name 
WHERE column_name BETWEEN value1 AND value2;
```

**Parameter Explanation:**

* **BETWEEN**: operator name
* **value1 AND value2**: range of values to fetch

**Query:** To fetch records of employees where Age is between 22 and 24 (inclusive):

```sql
SELECT * FROM Emp1 WHERE Age BETWEEN 22 AND 24;
```

---

### Example 3: WHERE Clause with `LIKE` Operator

It is used to fetch filtered data by searching for a particular pattern.

**Syntax:**

```sql
SELECT column1, column2 
FROM table_name 
WHERE column_name LIKE pattern;
```

**Parameter Explanation:**

* **LIKE**: operator used for pattern matching
* **pattern**: text pattern (case-insensitive)

**Query:** To fetch records where Name starts with the letter 'S':

```sql
SELECT * FROM Emp1 WHERE Name LIKE 'S%';
```

> The `'%'` (wildcard) signifies any number of trailing characters.

**Query:** To fetch records where Name contains the letter 'M':

```sql
SELECT * FROM Emp1 WHERE Name LIKE '%M%';
```

---

### Example 4: WHERE Clause with `IN` Operator

It is used to match any value within a list.

**Syntax:**

```sql
SELECT column1, column2 
FROM table_name 
WHERE column_name IN (value1, value2, ...);
```

**Parameter Explanation:**

* **IN**: operator name
* **value1, value2, ...**: list of values to match against

**Query:** To fetch the Names of employees where Age is 21 or 23:

```sql
SELECT Name FROM Emp1 WHERE Age IN (21, 23);
```

---

## List of Operators That Can Be Used with WHERE Clause

| Operator  | Description                      |
| --------- | -------------------------------- |
| `>`       | Greater Than                     |
| `>=`      | Greater than or Equal to         |
| `<`       | Less Than                        |
| `<=`      | Less than or Equal to            |
| `=`       | Equal to                         |
| `<>`      | Not Equal to                     |
| `BETWEEN` | In an inclusive range            |
| `LIKE`    | Search for a pattern             |
| `IN`      | Specify multiple possible values |

---

## Conclusion

The `WHERE` clause is used for filtering and refining SQL queries. Whether you’re working with basic conditions, using logical operators, or performing advanced queries with subqueries and `EXISTS`, mastering the `WHERE` clause is essential for every SQL user.

---
