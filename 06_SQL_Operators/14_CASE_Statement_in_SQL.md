
---

## CASE Statement in SQL

The CASE statement in SQL is a conditional expression that allows you to perform conditional logic within a query.  
It is commonly used to create new columns based on conditional logic, provide custom values, or control query outputs based on certain conditions.  
If no condition is true then the ELSE part will be executed. If there is no ELSE part then it returns NULL.

---

## Syntax:

To use CASE Statement in SQL, use the following syntax:

```sql
CASE case_value
WHEN condition THEN result1
WHEN condition THEN result2
...
Else result
END CASE;
````

---

## Example of SQL CASE Statement

Let's look at some examples of the CASE statement in SQL to understand it better.

---

## Demo SQL Database

We will be using this sample SQL table for our examples on SQL CASE statement:

| CustomerID | CustomerName             | LastName | Country   | Age | Phone      |
| ---------- | ------------------------ | -------- | --------- | --- | ---------- |
| 1          | Shubham                  | Thakur   | India     | 23  | xxxxxxxxxx |
| 2          | Aman                     | Chopra   | Australia | 21  | xxxxxxxxxx |
| 3          | Naveen                   | Tulasi   | Sri Lanka | 24  | xxxxxxxxxx |
| 4          | Aditya                   | Arpan    | Austria   | 21  | xxxxxxxxxx |
| 5          | Nishant. Salchichas S.A. | Jain     | Spain     | 22  | xxxxxxxxxx |

You can create the same Database in your system, by writing the following MySQL query:

```sql
CREATE TABLE Customer(
    CustomerID INT PRIMARY KEY,
    CustomerName VARCHAR(50),
    LastName VARCHAR(50),
    Country VARCHAR(50),
    Age int(2),
    Phone int(10)
);
-- Insert some sample data into the Customers table
INSERT INTO Customer (CustomerID, CustomerName, LastName, Country, Age, Phone)
VALUES (1, 'Shubham', 'Thakur', 'India','23','xxxxxxxxxx'),
       (2, 'Aman ', 'Chopra', 'Australia','21','xxxxxxxxxx'),
       (3, 'Naveen', 'Tulasi', 'Sri lanka','24','xxxxxxxxxx'),
       (4, 'Aditya', 'Arpan', 'Austria','21','xxxxxxxxxx'),
       (5, 'Nishant. Salchichas S.A.', 'Jain', 'Spain','22','xxxxxxxxxx');
```

---

## Example 1: Simple CASE Expression

In this example, we use CASE statement

**Query:**

```sql
SELECT CustomerName, Age,
CASE
    WHEN Country = "India" THEN 'Indian'
    ELSE 'Foreign'
END AS Nationality
FROM Customer;
```

**Output:**

| CustomerName             | Age | Nationality |
| ------------------------ | --- | ----------- |
| Shubham                  | 23  | Indian      |
| Aman                     | 21  | Foreign     |
| Naveen                   | 24  | Foreign     |
| Aditya                   | 21  | Foreign     |
| Nishant. Salchichas S.A. | 22  | Foreign     |

---

## Example 2: SQL CASE When Multiple Conditions

We can add multiple conditions in the CASE statement by using multiple WHEN clauses.

**Query:**

```sql
SELECT CustomerName, Age,
CASE
    WHEN Age> 22 THEN 'The Age is greater than 22'
    WHEN Age = 21 THEN 'The Age is 21'
    ELSE 'The Age is over 30'
END AS QuantityText
FROM Customer;
```

**Output:**

| CustomerName             | Age | QuantityText               |
| ------------------------ | --- | -------------------------- |
| Shubham                  | 23  | The Age is greater than 22 |
| Aman                     | 21  | The Age is 21              |
| Naveen                   | 24  | The Age is greater than 22 |
| Aditya                   | 21  | The Age is 21              |
| Nishant. Salchichas S.A. | 22  | The Age is over 30         |

---

## Example 3: CASE Statement With ORDER BY Clause

Let's take the Customer Table which contains CustomerID, CustomerName, LastName, Country, Age, and Phone. We can check the data of the Customer table by using the ORDER BY clause with the CASE statement.

**Query:**

```sql
SELECT CustomerName, Country
FROM Customer
ORDER BY
(CASE
    WHEN Country  IS 'India' THEN Country
    ELSE Age
END);
```

**Output:**

| CustomerName             | Country   |
| ------------------------ | --------- |
| Aman                     | Australia |
| Aditya                   | Austria   |
| Nishant. Salchichas S.A. | Spain     |
| Naveen                   | Sri lanka |
| Shubham                  | India     |

---

## Important Points About CASE Statement

* The SQL CASE statement is a conditional expression that allows for the execution of different queries based on specified conditions.
* There should always be a SELECT in the CASE statement.
* END ELSE is an optional component but WHEN THEN these cases must be included in the CASE statement.
* We can make any conditional statement using any conditional operator (like WHERE ) between WHEN and THEN. This includes stringing together multiple conditional statements using AND and OR.
* We can include multiple WHEN statements and an ELSE statement to counter with unaddressed conditions.

---
