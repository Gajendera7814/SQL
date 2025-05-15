
---
# SQL UNION ALL

UNION ALL Operator is used to combine the results of two or more SELECT statements into a single result set. Unlike the UNION operator, which eliminates duplicate records, UNION ALL includes all duplicates. This makes UNION ALL faster and more efficient when we don't need to remove duplicates.

---

## SQL UNION ALL Operator

The SQL UNION ALL command combines the result of two or more SELECT statements in SQL.  
For performing the UNION ALL operation, it is necessary that both the SELECT statements should have an equal number of columns/fields, otherwise, the resulting expression will result in an error.

---

## Syntax:

The syntax for the SQL UNION ALL operation is:

```sql
SELECT columns FROM table1
UNION ALL
SELECT columns FROM table2;
````

---

## Examples of SQL UNION ALL

Let's look at some examples of the UNION ALL command in SQL to understand its working. First, let's create a demo SQL database and tables on which UNION ALL will be performed.

---

## Demo SQL Database

In this tutorial on the UNION ALL operator, we will use the following tables in examples.

**STUDENTS table:**

| ROLL\_NO | NAME        | DOB        | AGE |
| -------- | ----------- | ---------- | --- |
| 1        | DEV SHARMA  | 2001-08-16 | 17  |
| 2        | AMAN VERMA  | 2002-01-04 | 16  |
| 3        | KRISH VATSA | 2000-11-29 | 18  |

**TRIP\_DETAIL Table:**

| ROLL\_NO | NAME        | DOB        | AGE |
| -------- | ----------- | ---------- | --- |
| 1        | DEV SHARMA  | 2001-08-16 | 17  |
| 2        | AMAN VERMA  | 2002-01-04 | 16  |
| 3        | KRISH VATSA | 2000-11-29 | 18  |
| 4        | VARUN GOYAL | 2003-09-21 | 15  |

---

## Example 1: Single Field With Same Name

We want to combine the names from both the STUDENTS and TRIP\_DETAIL tables, including all names, even if there are duplicates.

```sql
SELECT NAME FROM STUDENTS
UNION ALL
SELECT NAME FROM TRIP_DETAIL;
```

---

### Output:

| NAME        |
| ----------- |
| DEV SHARMA  |
| AMAN VERMA  |
| KRISH VATSA |
| DEV SHARMA  |
| AMAN VERMA  |
| KRISH VATSA |
| VARUN GOYAL |

Explanation: The UNION ALL operator combines all rows from the NAME column in both tables. It includes all names, including duplicates. In this case, "DEV SHARMA", "AMAN VERMA", and "KRISH VATSA" appear twice because they exist in both tables.

---

## Example 2: Different Field Names

Suppose we want to combine the ROLL\_NO from both tables and align the column names for consistency.

```sql
SELECT ROLL_NO AS Identifier FROM STUDENTS
UNION ALL
SELECT ROLL_NO AS Identifier FROM TRIP_DETAIL;
```

---

### Output:

| Identifier |
| ---------- |
| 1          |
| 2          |
| 3          |
| 1          |
| 2          |
| 3          |
| 4          |

Explanation: Here, ROLL\_NO from both tables is selected and aliased as Identifier. The UNION ALL operator combines all roll numbers from both tables, including duplicates. Each ROLL\_NO from STUDENTS appears twice because it also exists in TRIP\_DETAIL.

---

## Important Points About SQL UNION ALL

* UNION ALL command helps us to combine results of two or more SELECT statements from different tables.
* The UNION ALL command includes the duplicate records from the SELECT statements whereas the UNION command does not include duplicate records otherwise both the commands are same.
* For performing the UNION ALL operation, it is necessary that both the SELECT statements should have equal number of columns otherwise the resulting expression will result in an error.

---

## SQL UNION ALL vs UNION

Here is the comparison between UNION ALL and UNION Operator:

| Feature           | UNION ALL                                                                             | UNION                                                                |
| ----------------- | ------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| Duplicate Records | Includes all duplicates                                                               | Removes duplicate records                                            |
| Performance       | Faster, as it doesn't check for duplicates                                            | Slower, as it needs to eliminate duplicates                          |
| Use Case          | When duplicates are acceptable or needed                                              | When duplicates need to be removed                                   |
| Syntax            | `SELECT columns FROM table1 UNION ALL SELECT columns FROM table2;`                    | `SELECT columns FROM table1 UNION SELECT columns FROM table2;`       |
| Memory Usage      | Generally lower, since no extra processing for duplicates                             | Higher, due to additional steps for duplicate removal                |
| Result Set        | Combined rows from all SELECT statements, including duplicates                        | Combined rows from all SELECT statements, without duplicates         |
| Applicability     | Useful for large datasets where performance is critical and duplicates are acceptable | Useful when data integrity requires unique records in the result set |

---
