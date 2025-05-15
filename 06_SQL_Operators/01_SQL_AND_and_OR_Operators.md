
---

# SQL AND and OR Operators

The SQL AND and OR operators are used to filter data based on multiple conditions. These logical operators allow users to retrieve precise results from a database by combining various conditions in SELECT, INSERT, UPDATE, and DELETE statements.

---

## SQL AND Operator

The AND operator allows you to filter data based on multiple conditions, all of which must be true for the record to be included in the result set.

### Syntax:

The syntax to use the AND operator in SQL is:

```sql
SELECT * FROM table_name WHERE condition1 AND condition2 AND ...conditionN;
````

Here,

* `table_name`: name of the table
* `condition1,2,..N`: first condition, second condition, and so on.

---

## SQL OR Operator

The OR Operator in SQL displays the records where any one condition is true, i.e. either condition1 or condition2 is True.

### Syntax:

The syntax to use the OR operator in SQL is:

```sql
SELECT * FROM table_name WHERE condition1 OR condition2 OR... conditionN;
```

* `table_name`: name of the table
* `condition1,2,..N`: first condition, second condition, and so on

---

## SQL AND and OR Operator Examples

Let's look at some examples of AND and OR operators in SQL and understand their working.

Now, we consider a table database to demonstrate AND & OR operators with multiple cases.

### student table

**Student Table**

---

### Example 1: SQL AND Operator

If suppose we want to fetch all the records from the Student table where Age is 18 and ADDRESS is Delhi.

**Query:**

```sql
SELECT * FROM Student 
WHERE Age = 18 AND ADDRESS = 'Delhi';
```

**Output:**

| ROLL\_NO | NAME   | ADDRESS | PHONE      | Age |
| -------- | ------ | ------- | ---------- | --- |
| 1        | Ram    | Delhi   | XXXXXXXXXX | 18  |
| 4        | SURESH | Delhi   | XXXXXXXXXX | 18  |

---

### Example 2: SQL OR Operator

To fetch all the records from the Student table where NAME is Ram or NAME is SUJIT.

**Query:**

```sql
SELECT * FROM Student 
WHERE NAME = 'Ram' OR NAME = 'SUJIT';
```

**Output:**

| ROLL\_NO | NAME  | ADDRESS | PHONE      | Age |
| -------- | ----- | ------- | ---------- | --- |
| 1        | Ram   | Delhi   | XXXXXXXXXX | 18  |
| 3        | SUJIT | ROHTAK  | XXXXXXXXXX | 20  |
| 3        | SUJIT | ROHTAK  | XXXXXXXXXX | 20  |

---

## Combining AND and OR Operators in SQL

Combining AND and OR Operators in SQL allows the creation of complex conditions in queries. This helps in filtering data on multiple conditions.

### Syntax:

Syntax to use AND and OR operator in one statement in SQL is:

```sql
SELECT * FROM table_name 
WHERE condition1 AND (condition2 OR condition3);
```

---

### Example

Let's look at example of combining AND and OR operators in a single statement. In this example we will fetch all the records from the Student table where Age is 18, NAME is Ram or RAMESH.

**Query:**

```sql
SELECT * FROM Student WHERE Age = 18 AND (NAME = 'Ram' OR NAME = 'RAMESH');
```

**Output:**

| ROLL\_NO | NAME   | ADDRESS | PHONE      | Age |
| -------- | ------ | ------- | ---------- | --- |
| 1        | Ram    | Delhi   | XXXXXXXXXX | 18  |
| 2        | RAMESH | GURGAON | XXXXXXXXXX | 18  |

---

## Important Points About SQL AND and OR Operators

* The SQL AND operator is used to combine multiple conditions, where all the conditions must be true for the row to be included in the result set.
* The OR operator is used to combine multiple conditions, where at least one of the conditions must be true for the row to be included in the result set.
* Any kind of condition, including equality, inequality, comparison, and logical operators, can be utilized with the AND and OR operators.
* The AND operator is more important than the OR operator. In other words, when both are used in the same SQL statement, the AND operator will be executed first. To change the order of evaluation, parentheses can be used.
* You can employ the AND and OR operators inside of other conditions because they can both be nested.

---

## Conclusion

The AND and OR operators are essential tools for filtering data in SQL. By combining multiple conditions, you can create powerful and efficient queries to retrieve exactly the data you need. Remember to use parentheses for clarity and control the order of evaluation, especially when combining both operators. By mastering these logical operators, you’ll be able to handle complex queries and data filtering tasks more effectively.

---
