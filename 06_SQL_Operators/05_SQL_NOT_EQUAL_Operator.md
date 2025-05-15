
---

## NOT EQUAL Operator in SQL

NOT EQUAL Operator in SQL is used to compare two values and return if they are **not equal**. This operator returns boolean values. If given expressions are equal, the operator returns false otherwise true. If any one expression is NULL, it will return NULL.

It performs type conversion when expressions are of different data types, for example, `5 != "Five"`.

We use the NOT EQUAL operator to display our table without some exceptional values. For example, let's consider a table 'Students'. For this table, we have "id", "name", and "marks" as its columns. Now we want to display all those rows that have marks **not equal** to "100". In this kind of situation, the NOT EQUAL operator can be used.

**Note:** `<>` and `!=` perform the same operation i.e. check inequality. The only difference between `<>` and `!=` is that `<>` follows the ISO standard but `!=` does not. So it is recommended to use `<>` for NOT EQUAL Operator.

---

## Syntax

The SQL NOT EQUAL Operator syntax is:

```sql
SELECT * FROM table_name
WHERE column_name != value;
````

---

## Examples of NOT EQUAL Operator

Let's look at some examples of the NOT EQUAL Operator in SQL, and understand its working.

First, we will create a demo SQL database and table on which we will use the NOT EQUAL operator.

```sql
CREATE TABLE geeksforgeeks(
  user_id varchar(100) PRIMARY KEY,
  name varchar(100),
  contest_score int,
  rank int,
  coding_streak int
);

INSERT INTO geeksforgeeks(user_id,name,contest_score,rank,coding_streak)
VALUES('vish3001','Vishu',100,01,150);
INSERT INTO geeksforgeeks(user_id,name,contest_score,rank,coding_streak)
VALUES('neeraj119','Neeraj',99,02,125);
INSERT INTO geeksforgeeks(user_id,name,contest_score,rank,coding_streak)
VALUES('ayush105','Aayush',98,03,110);
INSERT INTO geeksforgeeks(user_id,name,contest_score,rank,coding_streak)
VALUES('sumit85','Sumit',99,02,100);
INSERT INTO geeksforgeeks(user_id,name,contest_score,rank,coding_streak)
VALUES('harsh05','Harsh',98,03,95);
```

**Output:**

| user\_id  | name   | contest\_score | rank | coding\_streak |
| --------- | ------ | -------------- | ---- | -------------- |
| vish3001  | Vishu  | 100            | 1    | 150            |
| neeraj119 | Neeraj | 99             | 2    | 125            |
| ayush105  | Aayush | 98             | 3    | 110            |
| sumit85   | Sumit  | 99             | 2    | 100            |
| harsh05   | Harsh  | 98             | 3    | 95             |

---

### Example 1: SQL NOT EQUAL Operator For String

In this example, we will display all those rows which do **not** have a name equal to `'Harsh'`. We will use NOT EQUAL with the WHERE clause in this case.

**Query:**

```sql
SELECT * 
FROM students
WHERE name != 'Harsh';
```

**Output:**

*(Assuming the students table has similar data, this would return all rows except the one with name 'Harsh')*

---

### SQL NOT EQUAL Operator For String Explanation

In the above example, we can see all those rows displayed which do not have their name equal to `'Harsh'`.

**Note:** The NOT EQUAL comparison is **case-sensitive** for strings. Meaning `"geeks"` and `"GEEKS"` are two different strings for NOT EQUAL operator.

---

### Example 2: SQL NOT EQUAL Operator with Multiple Conditions

In this example, we will display all those rows which do **not** have their contest score as `98` and rank as `3` and the coding streak should be greater than or equal to `100`. Using `AND` or `OR` operator you can use the SQL NOT operator for multiple values.

**Query:**

```sql
SELECT * FROM geeksforgeeks
WHERE contest_score != 98 AND rank != 3
AND coding_streak >= 100;
```

**Output:**

*(This will return rows where contest\_score is not 98, rank is not 3, and coding\_streak >= 100)*

---

### Example 3: SQL NOT EQUAL Operator with GROUP BY Clause

In this example, we will display all those ranks with their count that do **not** have their contest score as `100` using `GROUP BY` clause.

**Query:**

```sql
SELECT rank, COUNT(*) as count_score
FROM geeksforgeeks
WHERE contest_score <> 100
GROUP BY rank;
```

**Output:**

*(This will show count of rows grouped by rank where contest\_score is not 100)*

---

## Also Read: EQUAL Operators in SQL

---

## Important Points About SQL NOT EQUAL Operator

* SQL NOT EQUAL Operator is a comparison operator denoted as `!=` or `<>`. It returns boolean values i.e. True or False.
* It returns False when the compared expressions are equal otherwise it returns True.
* We use this operator with the `WHERE` clause.
* We can use this operator for integers and strings-based logical reasoning. It is case-sensitive for string comparisons.
* We can put multiple conditions using the `AND` or `OR` operator.

---

