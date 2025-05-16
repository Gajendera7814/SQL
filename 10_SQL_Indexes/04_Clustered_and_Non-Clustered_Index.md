
---

# Difference Between Clustered and Non-Clustered Index

Indexing is a critical performance optimization technique in SQL Server that helps speed up data retrieval operations. Understanding the differences between Clustered and Non-Clustered indexes is essential for database administrators and developers looking to optimize query performance.

---

## Differences Between Clustered and Non-Clustered Index

This table organizes the primary differences between clustered and non-clustered indexes, making it easier to understand when to use each index type based on performance requirements and database structure.

| Feature | Clustered Index | Non-Clustered Index |
|--------|------------------|----------------------|
| **Speed** | Faster for range-based queries and sorting. | Slower for range-based queries but faster for specific lookups. |
| **Memory Usage** | Requires less memory for operations. | Requires more memory due to additional index structure. |
| **Data Storage** | The clustered index stores data in the table itself. | The non-clustered index stores data separately from the table. |
| **Number of Indexes per Table** | A table can have only one clustered index. | A table can have multiple non-clustered indexes. |
| **Disk Storage** | The clustered index can store data on the disk. | The non-clustered index stores the index structure (B-tree) on disk with pointers to the data pages. |
| **Pointer Storage** | Stores pointers to the data blocks, not the data itself. | Stores both the indexed value and a pointer to the actual row in a separate data page. |
| **Leaf Nodes** | Leaf nodes contain the actual data itself. | Leaf nodes contain indexed columns and pointers to data. |
| **Data Order** | Defines the physical order of the rows in the table. | Defines the logical order of data in the index, not the table. |
| **Index Structure** | The data is physically reordered to match the index. | The logical order does not match the physical order of rows. |
| **Primary Key** | Primary keys are by default clustered indexes. | Composite keys used with unique constraints are non-clustered. |
| **Size** | Typically larger, especially for large primary clustered indexes. | Smaller than clustered indexes, especially when composite. |
| **Use Case** | Ideal for range queries and sorting. | Suitable for optimizing lookups and queries on non-primary columns. |
| **Impact on Table** | A clustered index directly impacts the table's physical storage order. | A non-clustered index does not affect the physical storage order of the table. |

---

## What is a Clustered Index?

A **Clustered Index** determines the physical order of the data in a table. When a clustered index is created on a column, SQL Server reorders the data in the table based on that index. Because the data is physically stored in the order of the clustered index, a table can only have **one clustered index**. Typically, a clustered index is created on the **primary key** by default.

> A clustered index is created only when both the following conditions are satisfied:
> 
> - The data or file that we are moving into secondary memory should be in sequential or sorted order.
> - There should be a key value, meaning it cannot have repeated values.

---

## Example of Clustered Index

Consider a table called `Student` where the `Roll_No` column is the primary key. This automatically becomes a clustered index. Here, SQL Server automatically creates a clustered index on the `Roll_No` column. The rows are physically stored in ascending order based on the `Roll_No`.

```sql
-- Creating Student Table with a Clustered Index on Primary Key
CREATE TABLE Student (
    Roll_No INT PRIMARY KEY,
    Name VARCHAR(100),
    Age INT,
    Grade CHAR(1)
);
````

We can have only **one clustered index** in one table, but we can have one clustered index on **multiple columns**, and that type of index is called a **composite index**.

The output of querying this table will present data in ascending order of `Roll_No`.

---

## Non-Clustered Index

A **Non-Clustered Index** is an index that does **not affect the physical order** of the data in the table. It is a separate structure from the data table, where the index contains a copy of the indexed columns and a pointer to the actual data. This allows for **multiple non-clustered indexes** on a table, unlike the clustered index, which can only exist once.

The data is stored in one place, and the index is stored in another place. Since the data and non-clustered index are stored separately, we can have **multiple non-clustered indexes** in a table.

---

## Example of Non-Clustered Index

In the `Student` table, we could create a non-clustered index on the `Name` column. Here, `Roll_No` is a primary key, hence there is automatically a clustered index. If we want to apply a non-clustered index on the `Name` column (in ascending order), then a new index structure will be created for that column.

In this example, a non-clustered index is created on the `Name` column. SQL Server will create a separate structure containing `Name` and pointers to the rows where the corresponding data resides.

```sql
-- Creating a Non-Clustered Index on Name Column
CREATE NONCLUSTERED INDEX NIX_FTE_Name
ON Student (Name ASC);
```

### Output:

```
student table
```

The row address is used because, if someone wants to search the data for “Sudhir”, then by using the row address he/she will directly go to that row address and can fetch the data directly.

---

## Conclusion

Understanding the differences between **clustered** and **non-clustered** indexes in SQL Server is fundamental to optimizing database performance.

* Clustered indexes are ideal for **range-based queries** and **sorting**.
* Non-clustered indexes excel in optimizing **specific lookups** and **dynamic queries**.

By carefully choosing the right type of index for our tables, we can significantly improve query performance and overall system efficiency.

```
