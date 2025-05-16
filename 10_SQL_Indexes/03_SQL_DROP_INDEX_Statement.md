
---

# SQL DROP INDEX Statement

In SQL, indexes play an essential role in optimizing query performance by speeding up data retrieval operations. However, indexes can also slow down data modification operations such as `INSERT`, `UPDATE`, and `DELETE` due to the overhead of maintaining them. When an index is no longer required or becomes redundant, it's important to remove it using the `DROP INDEX` statement.

---

## What is SQL DROP INDEX?

The SQL `DROP INDEX` command is used to remove an existing index from a table. Indexes are created to speed up query performance, but they can also consume storage space and add overhead to write operations. By removing unnecessary indexes, we can free up space and improve the performance of `INSERT`, `UPDATE`, and `DELETE` operations.

> **Note:** Indexes created by `PRIMARY KEY` or `UNIQUE` constraint cannot be deleted with just a `DROP INDEX` statement. To delete such indexes, we need to first drop the constraints using the `ALTER TABLE` statement, and then drop the index.

---

## Syntax for DROP INDEX Statement

The syntax for dropping an index varies slightly depending on the database system we are using. Here are the syntaxes for different database management systems (DBMS):

### MySQL

```sql
ALTER TABLE table_name DROP INDEX index_name;
````

### MS Access

```sql
DROP INDEX index_name ON table_name;
```

### SQL Server

```sql
DROP INDEX table_name.index_name;
```

### DB2/Oracle

```sql
DROP INDEX index_name;
```

### PostgreSQL

```sql
DROP INDEX index_name;
```

---

## Example of SQL DROP INDEX

Let’s go through an example where we create a table and add an index using the `CREATE INDEX` statement, and then drop it using the `DROP INDEX` statement.

### Step 1: Create the EMPLOYEE Table

```sql
CREATE TABLE EMPLOYEE(
   EMP_ID INT,
   EMP_NAME VARCHAR(20),
   AGE INT,
   DOB DATE,
   SALARY DECIMAL(7,2)); 
```

### Step 2: Create an Index on the EMPLOYEE Table

```sql
CREATE INDEX EMP
ON EMPLOYEE(EMP_ID, EMP_NAME);
```

This creates an index named `EMP` on the `EMP_ID` and `EMP_NAME` columns of the `EMPLOYEE` table, improving query performance for queries involving these columns.

---

## Dropping an Index

Now let's look at some examples of `DROP INDEX` statement and understand its workings in SQL. We will learn different use cases of the SQL `DROP INDEX` statement with examples. We can drop the index using two ways: either with `IF EXISTS` or with `ALTER TABLE`, so we will first drop the index using `IF EXISTS`.

---

### Example 1: SQL DROP INDEX with IF EXISTS

Using the `IF EXISTS` clause ensures that the index is dropped only if it already exists in the table. This prevents errors from being thrown if the index is not present.

#### Query:

```sql
DROP INDEX IF EXISTS EMP ON EMPLOYEE;
```

#### Output

```
Commands Executed Successfully;
```

#### Explanation:

This query drops the `EMP` index from the `EMPLOYEE` table only if the index exists, ensuring no error occurs if the index is absent. Since the `EMP` index exists, it is successfully removed. If the index didn’t exist, no error would be thrown.

---

### Example 2: SQL DROP INDEX with ALTER TABLE

In MySQL, PostgreSQL, and some other databases, the `ALTER TABLE` statement is used to drop an index. This query drops the `EMP` index on the `EMPLOYEE` table using the `ALTER TABLE` statement.

#### Query:

```sql
ALTER TABLE EMPLOYEE
DROP INDEX EMP;
```

#### Output:

```
Dropping the index
Dropping the index
```

---

## Verifying the DROP INDEX

To verify if the `DROP INDEX` statement has successfully removed the index from the table, we can check the indexes on the table. If the index is not present in the list, we know it has been deleted. This can be done using database-specific commands.

### MySQL Verification:

```sql
SHOW INDEXES FROM EMPLOYEE;
```

### SQL Server Verification:

```sql
SELECT * FROM sys.indexes 
WHERE object_id = (SELECT object_id FROM sys.objects WHERE name = 'EMPLOYEE');
```

### PostgreSQL Verification:

```sql
SELECT * FROM USER_INDEXES WHERE table_name = 'EMPLOYEE';
```

#### Explanation:

These queries retrieve information about the indexes associated with the `EMPLOYEE` table. If the index was successfully removed, it will not appear in the results.

---

## Important Points About SQL DROP INDEX Statement

* The SQL `DROP INDEX` statement is used to remove an existing index from a database table.
* It optimizes database performance by reducing index maintenance overhead.
* It improves the speed of `INSERT`, `UPDATE`, and `DELETE` operations on the table.
* Indexes created by `PRIMARY KEY` or `UNIQUE` constraints cannot be dropped using just the `DROP INDEX` statement.
* The `IF EXISTS` clause can be used to conditionally drop the index only if it exists.
* To verify if the `DROP INDEX` statement has successfully removed the index from the table, we can check the indexes on the table.

---

## Conclusion

The SQL `DROP INDEX` statement is an important tool for database optimization. By removing unnecessary indexes, we can free up space, improve write performance, and enhance overall system efficiency. However, we should always evaluate the impact of dropping an index on query performance before proceeding, especially for frequently accessed columns. Indexes should be used strategically, and removing them should only be done when they are no longer required, ensuring a balanced and efficient database environment.

```
