
---

# SQL PRIMARY KEY Constraint

The `PRIMARY KEY` constraint in SQL is one of the most important constraints used to ensure data integrity in a database table. A primary key uniquely identifies each record in a table, preventing duplicate or `NULL` values in the specified column(s). Understanding how to properly implement and use the primary key constraint is crucial for managing relational data effectively.

---

## 🔑 PRIMARY KEY in SQL

`PRIMARY KEY` in SQL is a column (or group of columns) that uniquely identifies the records in that table. A primary key must contain **unique values** and **can not have any NULL value**.

- There can only be **one primary key** in a table, but that primary key can consist of **one or more columns**.  
- When there are two or more columns in the primary key it is called a **composite key**.
- A primary key automatically has a `UNIQUE` constraint defined on it, and it ensures that there are **no duplicate or NULL values** in that column.

---

## 📌 SQL PRIMARY KEY Properties

- ❌ No duplicate values are allowed — the column assigned as the primary key should have **UNIQUE** values only.
- ❌ NO `NULL` values are present in the primary key column — values must be **mandatory**.
- Only **one primary key per table** exists, although the primary key may have **multiple columns**.
- ❌ No new row can be inserted with an already existing primary key.
- ✅ Primary keys can be:
  - **Simple primary key** — consists of one column.
  - **Composite primary key** — consists of multiple columns.
- Defined using either `CREATE TABLE` or `ALTER TABLE` statement.

---

## 🧩 Syntax

There are two syntaxes to create/add primary key to a table:

### ✅ Using `CREATE TABLE` Statement

```sql
CREATE TABLE table_name (
  column1 datatype constraint,
  column2 datatype constraint,
  ...,
  CONSTRAINT pk_constraint_name PRIMARY KEY (column1, column2, ...)
);
````

### ✅ Using `ALTER TABLE` Statement

```sql
ALTER TABLE table_name
ADD CONSTRAINT constraint_name PRIMARY KEY (column1, column2, ... column_n);
```

---

## 🧪 SQL PRIMARY KEY Examples

Let's look at some examples of the `PRIMARY KEY` Constraint in SQL and understand its working.

---

### Example 1: Create PRIMARY KEY in SQL

In this example, we will create primary key in a new table using `CREATE TABLE` statement.

**Query:**

```sql
CREATE TABLE Persons (
  PersonID int NOT NULL PRIMARY KEY,
  LastName varchar(255) NOT NULL,
  FirstName varchar(255),
  Age int
);
```

---

### ✅ Verify SQL Primary key creation

To verify if the primary key has been successfully created, we will try adding duplicate values in primary key column, and SQL should return an error.

**Query:**

```sql
INSERT INTO Persons VALUES
  (1, "Thakur", "Aditya", 22),
  (1, "Kumar", "Shubham", 21);
```

**Output:**

```
Error: UNIQUE constraint failed: Persons.PersonID
```

---

### Example 2: Add PRIMARY KEY to a Table

In this example, we will add a primary key to an already existing table using `ALTER TABLE` command.

Let's consider the previous table, and create it without primary key this time.

```sql
CREATE TABLE Persons ( 
  PersonID int,
  LastName varchar(255) NOT NULL,
  FirstName varchar(255),
  Age int
);
```

Now, this query will add a primary key to the `Persons` table:

```sql
ALTER TABLE Persons
ADD CONSTRAINT PK_Person PRIMARY KEY (PersonID);
```

---

## 💡 Important Points About SQL PRIMARY KEY

* A primary key is a column or a set of columns in a table that **uniquely identifies each row**.
* It ensures **data integrity** by preventing duplicate records and `NULL` values.
* A primary key can be defined on a **single column (simple)** or **multiple columns (composite)**.
* Creating a primary key automatically creates a **unique index** on the key column(s), improving query performance.
* Establishing relationships between tables using **SQL primary key and foreign key** improves database design, reduces data redundancy, and improves data consistency.

---

## 🎯 Benefits of Using Primary Keys

* **Data Integrity:** The primary key enforces data integrity by ensuring each record is unique.
* **Efficient Querying:** Since a primary key automatically creates an index, querying for records by the primary key is faster.
* **Referential Integrity:** Primary keys are used to establish relationships between tables (via foreign keys), ensuring consistency across related data.

---

## ⚠️ Common Issues and Best Practices

* **Avoid NULL values:** Always ensure that the columns involved in the primary key do not accept `NULL` values.
* **Choose meaningful primary keys:** If possible, choose a primary key that naturally fits the data and serves as a meaningful identifier, like an ID field.
* **Composite Keys:** Be cautious when using composite keys. While they are useful in some scenarios, they can make queries more complex. If possible, use a simple key or generate an artificial primary key (like an ID).
* **Changing Primary Keys:** Once a primary key is established, changing it can be difficult because of the interdependencies with other tables (foreign key constraints). Always plan ahead when designing your database schema.

---

## 🧾 Conclusion

The `PRIMARY KEY` constraint is a **fundamental concept** in relational databases that ensures each record in a table is **unique and identifiable**. By using the primary key effectively, you can:

* Maintain **data integrity**
* Improve **query performance**
* Establish **meaningful relationships** between tables

---

