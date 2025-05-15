
---

# SQL LIKE Operator


The SQL LIKE operator is used for performing pattern-based searches in a database. It is used in combination with the WHERE clause to filter records based on specified patterns, making it essential for any database-driven application that requires flexible search functionality.

---

## What is the SQL LIKE Operator?

SQL LIKE operator is used with the WHERE clause to search for a specified pattern in a column. LIKE operator finds and returns the rows that fit in the given pattern.

LIKE operator is case-insensitive by default in most database systems. This means that if you search for "apple" using the LIKE operator, it will return results that include "Apple", "APPLE", "aPpLe", and so on.

### Syntax:

```sql
SELECT column1, column2, ...
FROM table_name
WHERE column_name LIKE pattern;
````

* `column_name`: The column to be searched.
* `pattern`: The pattern to search for, which can include wildcard characters.

For making the LIKE operator case-sensitive, you can use the **"BINARY"** keyword in MySQL or the **"COLLATE"** keyword in other database systems.

**For example:**

```sql
SELECT * FROM products WHERE name LIKE BINARY 'apple%'
```

This following query will only return products whose name starts with `"apple"` and is spelled exactly like that, without capital letters.

---

## Wildcard Characters with the SQL LIKE Operator

Wildcards are used with the LIKE operator to search for specific patterns in strings. Wildcard characters substitute one or more characters in the string. There are four wildcard characters in SQL:

* `%` (Percent): Represents zero or more characters.
* `_` (Underscore): Represents a single character.
* `[]` (Square Brackets): Represents any single character within brackets.
* `-` (Hyphen): Specify a range of characters inside brackets.

---

## Examples of Wildcards

The below table shows some examples on how wild card can be written and what do they mean:

| Pattern   | Meaning                                                                    |
| --------- | -------------------------------------------------------------------------- |
| `'a%'`    | Match strings that start with `'a'`                                        |
| `'%a'`    | Match strings that end with `'a'`                                          |
| `'a%t'`   | Match strings that start with `'a'` and end with `'t'`                     |
| `'%wow%'` | Match strings that contain the substring `'wow'`                           |
| `'_wow%'` | Match strings that contain `'wow'` at the second position                  |
| `'_a%'`   | Match strings that contain `'a'` at the second position                    |
| `'a__%'`  | Match strings that start with `'a'` and contain at least 2 more characters |

---

## Examples of SQL LIKE Operator

In this tutorial on SQL LIKE Operator, we will use the following table in the examples.

### Supplier Table

```sql
CREATE TABLE Supplier (
    SupplierID CHAR(2) PRIMARY KEY,
    Name VARCHAR(50),
    Address VARCHAR(100)
);

INSERT INTO Supplier (SupplierID, Name, Address)
VALUES
    ('S1', 'Paragon Suppliers', '21-3, Okhla, Delhi'),
    ('S2', 'Mango Nation', '21, Faridabad, Haryana'),
    ('S3', 'Canadian Biz', '6/7, Okhla Phase II, Delhi'),
    ('S4', 'Caravan Traders', '2-A, Pitampura, Delhi'),
    ('S5', 'Harish and Sons', 'Gurgaon, NCR'),
    ('S6', 'Om Suppliers', '2/1, Faridabad, Haryana');
```

| SupplierID | Name              | Address                    |
| ---------- | ----------------- | -------------------------- |
| S1         | Paragon Suppliers | 21-3, Okhla, Delhi         |
| S2         | Mango Nation      | 21, Faridabad, Haryana     |
| S3         | Canadian Biz      | 6/7, Okhla Phase II, Delhi |
| S4         | Caravan Traders   | 2-A, Pitampura, Delhi      |
| S5         | Harish and Sons   | Gurgaon, NCR               |
| S6         | Om Suppliers      | 2/1, Faridabad, Haryana    |

---

### Example 1 : Match Names Starting with 'Ca'

Retrieve SupplierID, Name, and Address from suppliers table, where supplier name starts form k.

```sql
SELECT SupplierID, Name, Address
FROM Supplier
WHERE Name LIKE 'Ca%';
```

**Output:**

| SupplierID | Name            | Address                    |
| ---------- | --------------- | -------------------------- |
| S3         | Canadian Biz    | 6/7, Okhla Phase II, Delhi |
| S4         | Caravan Traders | 2-A, Pitampura, Delhi      |

---

### Example 2: Match Addresses Containing 'Okhla'

Retrieve entire table, where address contains OKHLA.

```sql
SELECT *
FROM Supplier
WHERE Address LIKE '%Okhla%';
```

**Output:**

| SupplierID | Name              | Address                    |
| ---------- | ----------------- | -------------------------- |
| S1         | Paragon Suppliers | 21-3, Okhla, Delhi         |
| S3         | Canadian Biz      | 6/7, Okhla Phase II, Delhi |

---

### Example 3: Match Names Where 'ango' Appears in the Second Position

Retrieve SupplierID, Name and Address of supplier whose name contains "ango" in second substring.

```sql
SELECT SupplierID, Name, Address
FROM Supplier
WHERE Name LIKE '_ango%';
```

**Output:**

| SupplierID | Name         | Address                |
| ---------- | ------------ | ---------------------- |
| S2         | Mango Nation | 21, Faridabad, Haryana |

---

### Example 4: Using LIKE with AND for Complex Conditions

Retrieve suppliers from Delhi with names starting with "C":

```sql
SELECT SupplierID, Name, Address
FROM Supplier
WHERE Address LIKE '%Delhi%' AND Name LIKE 'C%';
```

**Output:**

| SupplierID | Name            | Address                    |
| ---------- | --------------- | -------------------------- |
| S3         | Canadian Biz    | 6/7, Okhla Phase II, Delhi |
| S4         | Caravan Traders | 2-A, Pitampura, Delhi      |

---

### Example 5: Using NOT LIKE for Exclusion

To retrieve all suppliers whose name does not contain "Mango":

```sql
SELECT SupplierID, Name, Address
FROM Supplier
WHERE Name NOT LIKE '%Mango%';
```

**Output:**

| SupplierID | Name              | Address                    |
| ---------- | ----------------- | -------------------------- |
| S1         | Paragon Suppliers | 21-3, Okhla, Delhi         |
| S3         | Canadian Biz      | 6/7, Okhla Phase II, Delhi |
| S4         | Caravan Traders   | 2-A, Pitampura, Delhi      |
| S5         | Harish and Sons   | Gurgaon, NCR               |
| S6         | Om Suppliers      | 2/1, Faridabad, Haryana    |

---

## SQL LIKE Application

The LIKE operator is extremely resourceful in situations such as address filtering wherein we know only a segment or a portion of the entire address (such as locality or city) and would like to retrieve results based on that. The wildcards can be resourcefully exploited to yield even better and more filtered tuples based on the requirement.

---

## Key Takeaways About LIKE Operator

* LIKE operator is used to search for specific patterns in a column.
* It is mostly used with WHERE clause for finding or filtering specific data.
* Like Operator is case-insensitive by default, to make it case sensitive, we can use BINARY keyword.
* LIKE operator has 4 wild cards, which we can use with LIKE operator to specify the filter. The wild cards are: `%`, `_`, `[]` and `-`.

---

## Conclusion

The SQL LIKE operator is a powerful tool for pattern matching, allowing you to perform flexible searches within columns. By combining wildcards and logical operators, you can craft complex queries to find the data you need with precision. Understanding how to optimize the use of LIKE with indexes and case sensitivity will help improve query performance.


---
