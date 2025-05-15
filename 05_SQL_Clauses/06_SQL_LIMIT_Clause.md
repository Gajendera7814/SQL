
---

## What is the SQL LIMIT Clause?

The SQL LIMIT clause is used to control maximum number of records returned by a query. It is commonly used for limiting query results when only a subset of the data is required, such as for pagination, filtering top values, or analyzing a smaller portion of a large table. This can be particularly useful for tasks like:

- Paginating results (e.g., showing 10 results per page)
- Retrieving top records (e.g., the top 5 highest-rated products)
- Sampling data (e.g., getting a random sample of rows for analysis)

---

## Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition
ORDER BY column
LIMIT [offset,] row_count;
````

---

### Key Terms

* `offset`: number of rows to skip before returning the result set.
* `row_count`: number of rows to return in the result set.

---

## Example 1: Basic LIMIT Usage

Let's look at some examples of the LIMIT clause in SQL to understand it's working. Imagine we have a Student table with a list of students, and we just want to retrieve the first 3 students from the table. Here's how you can do that using LIMIT:

```sql
CREATE TABLE student (
  id INT PRIMARY KEY,
  name VARCHAR(50),
  age INT
);

INSERT INTO student (id, name, age)
VALUES (1, 'Shubham Thakur', 18),
       (2, 'Aman Chopra', 19),
       (3, 'Bhavika uppala', 20),
       (4,'Anshi Shrivastava',22);
```

**Query:**

```sql
SELECT * FROM student 
LIMIT 3;
```

**Output:**

LIMIT Clause Example

---

## Example 2: LIMIT with ORDER BY Clause

In this example, we will use the LIMIT clause with ORDER BY clause to retrieve the top 3 students sorted by their grade (assuming a Grade column exists). The LIMIT operator can be used in situations like these, where we need to find the top 3 students in a class and do not want to use any conditional statements.

**Query:**

```sql
SELECT * FROM Student
ORDER BY Grade DESC
LIMIT 3;
```

**Output:**

LIMIT with ORDER BY Clause

**Explanation:** This query first orders the students by their grades in descending order, then limits the results to just the top 3 students. It's an excellent way to get the "best" records from a dataset without needing complex filtering or conditions.

---

## SQL LIMIT with OFFSET

The OFFSET clause allows us to skip a specified number of rows before starting to return the results. OFFSET can only be used with the ORDER BY clause. It cannot be used on its own. It’s particularly helpful for pagination, where we might want to show different "pages" of results from a larger dataset. OFFSET value must be greater than or equal to zero. It cannot be negative, else returns an error.

### Syntax:

```sql
SELECT * FROM table_name ORDER BY column_name LIMIT X OFFSET Y;
```

**OR**

```sql
SELECT * FROM table_name ORDER BY column_name LIMIT Y,X;
```

* `X` → Number of rows to return.
* `Y` → Number of rows to skip.

---

## Example: Skipping First 2 Rows & Fetching 2 Rows

Imagine we have a list of students, but we want to skip the first 2 rows and fetch the next 2 students based on their age.

**Query:**

```sql
SELECT * 
FROM Student 
ORDER BY age 
LIMIT 2 OFFSET 2;
```

**Output:**

SQL LIMIT OFFSET Example Output

---

## Using LIMIT to Get the nth Highest or Lowest Value

Now we will look for LIMIT use in finding highest or lowest value we need to retrieve the rows with the nth highest or lowest value. In that situation, we can use the subsequent LIMIT clause to obtain the desired outcome.

### Syntax:

```sql
SELECT column_list  
FROM table_name  
ORDER BY expression  
LIMIT n-1, 1;
```

---

## Example: Fetching the 3rd Highest Age

Let’s say we want to find the third-highest age from your Student table. We can do this using LIMIT along with ORDER BY.

**Query:**

```sql
SELECT age FROM Student  
ORDER BY age LIMIT 2, 1;
```

**Output:**

SQL LIMIT to Get the nth Highest Value Example Output

**Explanation:**

* Orders records in descending order (highest age first).
* Skips 2 records (`LIMIT 2`) and retrieves the next one (`LIMIT 2,1`).

---

## Using LIMIT with WHERE Clause

The WHERE clause can also be used with LIMIT. It produces the rows that matched the condition after checking the specified condition in the table.

---

### Example: Fetching a Limited Set of Students Based on ID

For example, let's say we want to find the youngest student with an ID less than 4.

**Query:**

```sql
SELECT age
FROM Student
WHERE id<4
ORDER BY age
LIMIT 2, 1;
```

**Output:**

LIMIT with WHERE Clause Example Output

**Explanation:** This query filters students whose ID is less than 4, orders them by age, and retrieves the second youngest student (skipping the first one and fetching the next one). It's a powerful way to focus on specific data before limiting the output.

---

## Restrictions on the LIMIT clause

There are several limitations of SQL LIMIT. The following situations do not allow the LIMIT clause to be used:

* With regard to defining a view
* The use of nested SELECT statements
* Except for subqueries with table expressions specified in the FROM clause.
* Embedded SELECT statements are used as expressions in a singleton SELECT (where max = 1) within an SPL routine where embedded SELECT statements are used as expressions.

---

## Important Points About SQL LIMIT

* The LIMIT clause is used to set an upper limit on the number of tuples returned by SQL.
* It is important to note that this clause is not supported by all SQL versions.
* The LIMIT clause can also be specified using the SQL 2008 OFFSET/FETCH FIRST clauses.
* The limit/offset expressions must be a non-negative integer.

---

