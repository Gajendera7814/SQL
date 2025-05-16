
---

# SQL CREATE INDEX Statement

In SQL, indexes are important for optimizing query performance by speeding up data retrieval operations. The `CREATE INDEX` statement is used to create indexes in tables, enabling quicker searches and improving database efficiency.

---

## What is the CREATE INDEX Statement?

The `CREATE INDEX` Statement in SQL is used to create indexes in tables and retrieve data from the database faster than usual. Indexes are invisible structures that work behind the scenes to speed up data retrieval operations in databases. They are essential for optimizing query performance and improving overall system efficiency. While they are not visible to users, indexes improve query performance significantly, making them an essential part of database optimization.

The `CREATE INDEX` command enables us to create an index on a table, improving query performance by providing a faster way to retrieve rows.

### Syntax:

```sql
CREATE INDEX index_name
ON table (column1, column2.....);
````

---

### Key Terms

* **index\_name**: The name of the index.
* **table\_name**: The name of the table on which the index is created.
* **column1, column2, ...**: The columns that the index will be applied to.

---

## Creating a Unique Index

A unique index ensures that all values in the indexed columns are unique preventing duplicate values.

```sql
CREATE UNIQUE INDEX index_name
ON table_name (column1, column2, ...);
```

---

## When Should Indexes Be Created?

Indexes should be created under the following conditions:

* **Frequent Search Columns**: When a column is frequently used in `WHERE` clauses or as part of joins.
* **Wide Range of Values**: When a column has a large variety of distinct values (e.g., product IDs, customer IDs).
* **Low Null Values**: Indexes work best on columns that contain a low number of `NULL` values.

---

## Example of SQL CREATE INDEX Statement

Let’s look at an example where we use the `CREATE INDEX` command on a `STUDENTS` table given below:

| student\_id | name         | address        | age | birthdate  |
| ----------- | ------------ | -------------- | --- | ---------- |
| 1           | DEV SHARMA   | 91 ABC STREET  | 25  | 1991-08-19 |
| 2           | ARYA RAJPUT  | 77 XYZ STREET  | 21  | 1999-09-29 |
| 3           | GAURAV VERMA | 101 YEMEN ROAD | 29  | 2000-01-01 |

### Step 1: Create an Index

In this example, we will create an index on the `name` column of the `STUDENTS` table to speed up queries that search by name.

#### Query:

```sql
CREATE INDEX idx
ON STUDENTS(NAME);
```

**Explanation**:
This creates an index named `idx_name` on the `name` column of the `STUDENTS` table. The index will improve performance for queries that search for students by name.

---

### Step 2: Retrieve Data Using the Index

After creating the index, queries that use the `name` column in their `WHERE` clause will benefit from the faster data retrieval provided by the index. The `USE INDEX` hint directs the query to use the `idx_name` index to speed up data retrieval.

#### Query:

```sql
SELECT * FROM STUDENTS USE INDEX(idx);
```

---

## DROP INDEX Statement in SQL

The `DROP INDEX` statement in SQL is used to delete an index from a table. Removing unnecessary or redundant indexes can improve write performance by reducing the overhead involved in maintaining them during `INSERT`, `UPDATE`, or `DELETE` operations.

The syntax for the `DROP INDEX` statement varies slightly depending on the database management system (DBMS) being used.

### 1. DROP INDEX in MS Access

```sql
DROP INDEX index_name ON table_name;
```

#### Key Terms:

* **index\_name**: The name of the index to be deleted.
* **table\_name**: The name of the table from which the index is being removed.

---

### 2. DROP INDEX in SQL Server

```sql
DROP INDEX table_name.index_name;
```

#### Key Terms:

* **table\_name**: The name of the table that contains the index.
* **index\_name**: The name of the index to be deleted.

---

### 3. DROP INDEX in DB2/Oracle

```sql
DROP INDEX index_name;
```

---

### 4. DROP INDEX in MySQL

```sql
ALTER TABLE table_name DROP INDEX index_name;
```

#### Key Terms:

* **table\_name**: The name of the table.
* **index\_name**: The name of the index to be dropped.

---

## Important Points About SQL CREATE INDEX Statement

* **Improves Data Retrieval**: The `CREATE INDEX` statement is used to create indexes on columns, speeding up query execution and enabling faster data retrieval, especially on large tables.
* **Enhances Query Efficiency**: Indexes help with efficiently searching for data, sorting results in a specified order, and optimizing joins between tables.
* **Over-Indexing Risks**: While indexes speed up `SELECT` queries, too many indexes can degrade overall system performance. They require additional storage and can slow down data modification operations (`INSERT`, `UPDATE`, `DELETE`). Indexes should be created on columns frequently queried or used in joins.
* **Unique Indexes**: The `CREATE UNIQUE INDEX` statement ensures that the indexed column contains only unique values, helping maintain data integrity by preventing duplicates.
* **Removing Unused Indexes**: The `DROP INDEX` statement allows for removing indexes that are no longer needed, helping improve database performance by eliminating unnecessary overhead.

---

## Conclusion

Indexes are essential for improving database performance, particularly for frequently searched columns or those used in `WHERE` clauses of `SELECT` queries. While they speed up data retrieval, it's important to use them judiciously. Over-indexing can lead to slower database updates and overall system performance degradation. The `CREATE INDEX` statement allows for both simple and unique indexes, offering flexibility in how data is indexed and queried.

```
