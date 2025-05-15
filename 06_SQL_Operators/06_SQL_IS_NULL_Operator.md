
# SQL IS NULL

The SQL IS NULL operator is a logical operator used to identify and filter out rows with NULL values in a column. A NULL value represents missing or undefined data in a database. It is different from a zero value or blank space, and it indicates that the value is unknown.

---

## What is the SQL IS NULL Operator?

The IS NULL operator is used to check if a column contains a NULL value. If a column value is NULL, the operator returns TRUE; otherwise, it returns FALSE. It's commonly used in WHERE clauses to filter rows that contain NULL values in specific columns.

---

## Syntax:

SQL IS NULL syntax is:

```sql
SELECT * FROM table_name
WHERE column_name IS NULL;
````

**Note:** A NULL value is different from a Zero Value and Blank Spaces. A field that has NULL value means the field was left blank.

---

## SQL IS NULL Examples

Let's look at some examples of the IS NULL operator in SQL. These examples will help in understanding the working of IS NULL in SQL.

First, we will create a demo SQL database and table, on which we will use the IS NULL operator.

---

### Query:

```sql
CREATE TABLE geeksforgeeks(
  user_id int PRIMARY KEY,
  name varchar(100),
  problems_solved int,
  coding_score int,
  email varchar(100)
);

INSERT INTO geeksforgeeks (user_id, name, problems_solved, coding_score, email)
VALUES
    (101, 'Vishu', 20, 100, 'example1@gamil.com'),
    (102, 'Sumit', 19, 99, NULL),
    (103, 'Neeraj', 18, 98, 'example2@gamil.com'),
    (104, 'Aayush', 17, 97, NULL),
    (105, 'Harsh', 16, NULL, 'example3@gamil.com'),
    (106, 'Rahul', 15, NULL, 'example4@gamil.com'),
    (107, 'Vivek', 14, 90, NULL);

SELECT * FROM geeksforgeeks;
```

---

### Output:

| user\_id | name   | problems\_solved | coding\_score | email                                           |
| -------- | ------ | ---------------- | ------------- | ----------------------------------------------- |
| 101      | Vishu  | 20               | 100           | [example1@gamil.com](mailto:example1@gamil.com) |
| 102      | Sumit  | 19               | 99            | NULL                                            |
| 103      | Neeraj | 18               | 98            | [example2@gamil.com](mailto:example2@gamil.com) |
| 104      | Aayush | 17               | 97            | NULL                                            |
| 105      | Harsh  | 16               | NULL          | [example3@gamil.com](mailto:example3@gamil.com) |
| 106      | Rahul  | 15               | NULL          | [example4@gamil.com](mailto:example4@gamil.com) |
| 107      | Vivek  | 14               | 90            | NULL                                            |

---

### Example 1: IS NULL with WHERE clause

To filter rows where the email column contains NULL, use the IS NULL operator in a WHERE clause:

```sql
SELECT * 
FROM students
WHERE email IS NULL;
```

---

### Output:

*(This will show all rows where the email column is NULL)*

---

### Example 2: IS NULL Operator on Multiple Columns

We can use the IS NULL operator with multiple columns. For instance, to filter rows where either email or coding\_score is NULL, use the OR operator:

```sql
SELECT * 
FROM students
WHERE email IS NULL OR coding_score IS NULL;
```

---

### Output:

*(This will show all rows where email is NULL or coding\_score is NULL)*

---

### Example 3: IS NULL with COUNT() Function

The COUNT() function can be used to count the number of NULL values in a column. For example, to count how many rows have a NULL value in the coding\_score column:

```sql
SELECT COUNT(*) AS count_empty_coding_score
FROM students
WHERE coding_score IS NULL;
```

---

### Output:

*(This will return the count of rows with NULL coding\_score)*

We can clearly see in our table that we have 2 rows that have NULL values in their coding score column i.e. user\_id: 105, 106.

---

### Example 4: IS NULL with UPDATE Statement

We can update NULL values using the IS NULL operator in an UPDATE statement. For example, let's set a default email for all users with a NULL value in the email column:

```sql
UPDATE students
SET email = 'default@gmail.com'
WHERE email IS NULL;
```

---

### Output:

*(After running the above query, the rows where email was NULL will now have '[default@gmail.com](mailto:default@gmail.com)')*

As we can see user\_id's: 102, 104, and 107 previously contained NULL values in their emails column but now they have a default value i.e. `"default@gmail.com"`.

---

### Example 5: IS NULL with DELETE Statement

We can also use the IS NULL operator to delete rows where a column contains NULL values. For example, to delete rows where coding\_score is NULL:

```sql
DELETE FROM students
WHERE coding_score IS NULL;
```

---

### Output:

*(Rows where coding\_score was NULL are deleted)*

We can notice clearly that all those rows deleted have a null value in their coding score column.

---

## Important Points About SQL IS NULL

* SQL IS NULL is used to detect any rows that contain a NULL value in its column.
* IS NULL operator is mostly used with WHERE clause in SQL.
* We can use IS NULL operator on multiple columns using OR operator.
* Using COUNT function we can count total number of NULL values in SQL.
* We can UPDATE or DELETE the NULL values, after filtering them with IS NULL operator.

---
