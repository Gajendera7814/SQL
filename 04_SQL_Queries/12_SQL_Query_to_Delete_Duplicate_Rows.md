
---

## What Are Duplicate Rows?

Duplicate rows are records in a database that have identical values in one or more columns. These rows often arise due to issues like multiple imports, user errors, or missing constraints like primary keys or unique indexes. SQL query to delete duplicate rows typically involves identifying duplicates using functions like `ROW_NUMBER()` or `COUNT()` and making sure that only one copy of each record is kept in the table. If not handled properly, duplicates can lead to:

- **Inaccurate Data Reporting:** Reports may contain false information.
- **Storage Waste:** Redundant records consume unnecessary space.
- **Decreased Query Performance:** Queries on large tables with duplicates may perform poorly.

---

## Why You Should Remove Duplicate Rows

- **Data Integrity:** Duplicates can distort reports and analyses, leading to incorrect insights.
- **Optimal Performance:** Redundant data can slow down queries, especially when dealing with large datasets.
- **Efficient Storage:** Removing duplicates helps optimize storage usage, keeping your database lean.

---

## Creating the Sample Table and Inserting Data

To effectively remove duplicate rows in SQL, we can follow a structured approach. Let’s begin by creating a table called `DETAILS` and populating it with some sample data, including duplicate rows.

### Step 1: Create the Sample Table

We will create a table named `DETAILS` to demonstrate how to identify and delete duplicate rows. This step helps in setting up the necessary structure to store sample data and perform operations like detecting duplicates and applying deletion techniques.

```sql
CREATE TABLE DETAILS (
    SN INT IDENTITY(1,1) PRIMARY KEY,
    EMPNAME VARCHAR(25) NOT NULL,
    DEPT VARCHAR(20) NOT NULL,
    CONTACTNO BIGINT NOT NULL,
    CITY VARCHAR(15) NOT NULL
);
````

---

### Step 2: Insert Data into the Table

Let’s insert some data, including duplicates, into the `DETAILS` table. This step allows us to copy real-world scenarios where duplicate records might occur, enabling us to demonstrate how to identify and remove them effectively.

```sql
INSERT INTO DETAILS (EMPNAME, DEPT, CONTACTNO, CITY)
VALUES 
    ('VISHAL', 'SALES', 9193458625, 'GAZIABAD'),
    ('VIPIN', 'MANAGER', 7352158944, 'BAREILLY'),
    ('ROHIT', 'IT', 7830246946, 'KANPUR'),
    ('RAHUL', 'MARKETING', 9635688441, 'MEERUT'),
    ('SANJAY', 'SALES', 9149335694, 'MORADABAD'),
    ('VIPIN', 'MANAGER', 7352158944, 'BAREILLY'),
    ('VISHAL', 'SALES', 9193458625, 'GAZIABAD'),
    ('AMAN', 'IT', 78359941265, 'RAMPUR');
```

---

## How to Identify Duplicate Rows

We use the `GROUP BY` clause with the `COUNT(*)` function to find rows with duplicate values. This step helps us group the records by specific columns and count how many times each combination occurs, making it easier to identify duplicates that appear more than once in the table.

```sql
SELECT EMPNAME, DEPT, CONTACTNO, CITY, 
       COUNT(*) 
FROM DETAILS
GROUP BY EMPNAME, DEPT, CONTACTNO, CITY
HAVING COUNT(*) > 1;
```

**Explanation:** This query will return the duplicate records based on the combination of `EMPNAME`, `DEPT`, `CONTACTNO`, and `CITY`.

---

## Methods to Delete Duplicate Rows in SQL

There are several ways to delete duplicate rows in SQL. Here, we will explain five methods to handle this task effectively.

---

### Method 1: Using GROUP BY and COUNT()

Use the `GROUP BY` clause along with `MIN(SN)` to retain one unique row for each duplicate group. This method identifies the first occurrence of each duplicate combination based on the `SN` (serial number) and deletes the other duplicate rows.

```sql
DELETE FROM DETAILS
WHERE SN NOT IN (
    SELECT MIN(SN)
    FROM DETAILS
    GROUP BY EMPNAME, DEPT, CONTACTNO, CITY
);

SELECT * FROM DETAILS;
```

**Output:**

| SN | EMPNAME | DEPT      | CONTACTNO   | CITY      |
| -- | ------- | --------- | ----------- | --------- |
| 1  | VISHAL  | SALES     | 9193458625  | GAZIABAD  |
| 2  | VIPIN   | MANAGER   | 7352158944  | BAREILLY  |
| 3  | ROHIT   | IT        | 7830246946  | KANPUR    |
| 4  | RAHUL   | MARKETING | 9635688441  | MEERUT    |
| 5  | SANJAY  | SALES     | 9149335694  | MORADABAD |
| 8  | AMAN    | IT        | 78359941265 | RAMPUR    |

---

### Method 2: Using ROW\_NUMBER()

The `ROW_NUMBER()` function provides a more elegant and flexible solution. This window function assigns a unique number to each row within a partition (group of duplicates). We can delete rows where the row number is greater than 1.

```sql
WITH CTE AS (
    SELECT SN, EMPNAME, DEPT, CONTACTNO, CITY,
           ROW_NUMBER() OVER (PARTITION BY EMPNAME, DEPT, CONTACTNO, CITY ORDER BY SN) AS RowNum
    FROM DETAILS
)
DELETE FROM CTE WHERE RowNum > 1;

SELECT * FROM DETAILS;
```

**Output:** Same as Method 1.

---

### Method 3: Using Common Table Expressions (CTEs)

Using a Common Table Expression (CTE), we can delete duplicates in a more structured way. CTEs provide a cleaner approach by allowing us to define a temporary result set that can be referenced within the DELETE statement. This method can be more readable and maintainable, especially when dealing with complex queries.

```sql
WITH CTE AS (
    SELECT SN, EMPNAME, DEPT, CONTACTNO, CITY,
           ROW_NUMBER() OVER (PARTITION BY EMPNAME, DEPT, CONTACTNO, CITY ORDER BY SN) AS RowNum
    FROM DETAILS
)
DELETE FROM CTE WHERE RowNum > 1;

SELECT * FROM DETAILS;
```

**Output:** Same as Method 1.

---

### Method 4: Using Temporary Tables

You can create a temporary table to hold unique records and then replace the original table with the new, clean data.

**Steps:**

1. Insert unique rows into a temporary table.
2. Truncate the original table.
3. Insert the unique rows back.

```sql
SELECT DISTINCT EMPNAME, DEPT, CONTACTNO, CITY
INTO #TempTable
FROM DETAILS;

TRUNCATE TABLE DETAILS;

INSERT INTO DETAILS (EMPNAME, DEPT, CONTACTNO, CITY)
SELECT EMPNAME, DEPT, CONTACTNO, CITY
FROM #TempTable;

DROP TABLE #TempTable;

SELECT * FROM DETAILS;
```

**Output:** Same as Method 1.

---

### Method 5: Using DISTINCT with INSERT INTO

You can use `DISTINCT` to select only unique rows and then insert them back into the original table, effectively deleting duplicates.

```sql
DELETE FROM DETAILS;

INSERT INTO DETAILS (EMPNAME, DEPT, CONTACTNO, CITY)
SELECT DISTINCT EMPNAME, DEPT, CONTACTNO, CITY
FROM DETAILS;

SELECT * FROM DETAILS;
```

**Output:** Same as Method 1.

---

## Best Practices to Prevent Duplicates

While identifying and removing duplicates is essential, preventing them is even better. Here are some best practices to ensure that duplicates don’t enter your database in the first place:

* **Use Primary Keys or Unique Constraints:** These ensure that each record is unique, preventing accidental duplication.
* **Data Validation:** Implement validation rules in your application to prevent duplicate entries.
* **Indexing:** Create unique indexes on columns that must remain unique, like contact numbers or email addresses.
* **Regular Data Cleaning:** Periodically run data-cleaning queries to identify and remove any newly inserted duplicates.

---

## Conclusion

Duplicate rows in SQL databases can negatively impact performance and data accuracy. Using methods like `GROUP BY`, `ROW_NUMBER()`, and `CTE`, we can efficiently delete duplicate rows in SQL while retaining unique records. Always test your queries on a backup or development environment to ensure accuracy before applying them to production databases.

---