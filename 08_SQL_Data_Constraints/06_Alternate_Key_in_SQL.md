
---

# SQL - ALTERNATE KEY

Alternate Key is any candidate key not selected as the primary key. So, while a table may have multiple candidate keys (sets of columns that could uniquely identify rows), only one of them is designated as the Primary Key. The rest of these candidate keys become Alternate Keys.

---

## Some important points about Alternate Keys are as follows :

- A Primary Key can't be an Alternate Key. For a table with a single Candidate Key which has to be the Primary Key will not contain any Alternate Key.
- A Foreign Key can't be an Alternate Key as it is only used to reference another table.
- The alternate Key should be unique.
- An Alternate Key can be a set of a single attribute or multiple attributes.
- It can be NULL as well.

---

## Creating an Alternate Key in SQL

We are going to see how to create an ALTERNATE Key in SQL using sample tables as shown.

Consider two tables, **Product Information** and **Customer Information**. We will assume that we are creating a customer information system where we want to keep track of customers' orders. In this case, we use the Product ID as a Foreign Key in the Customer Information table to reference products purchased by customers.

---

### Product Information

| Product ID | Product Name | Price |
|------------|--------------|-------|
| 1001       | Washing Soap | 25    |
| 1020       | Shampoo      | 150   |
| 1030       | Notebook     | 200   |
| 1045       | Headphone    | 1000  |

---

### Customer Information

| Customer ID | Customer Name | Email Address     | Shipping Address       | Pan Number | Product ID |
|-------------|---------------|-------------------|-----------------------|------------|------------|
| 1           | Madhulika     | abc@gmail.com     | XYZ-Colony, Patna     | XXABX10011 | 1030       |
| 2           | Tanmoy        | tdq@gmail.com     | ABC-Colony, Guwahati  | DDABX10034 | 1001       |
| 3           | Ritik         | def@gmail.com     | XYZ_Street, Chennai   | ACQBX10555 | 1045       |
| 4           | Satadru       | sm11@gmail.com    | Park_Street, Kolkata  | ZZABX20035 | 1045       |

---

In the Customer Information Table, **Customer ID**, **Pan Number**, **Email Address** are unique as they can uniquely identify a row in the given table. PAN Number is unique for every person and Customer ID is also a unique number provided by E-Commerce sites to distinguish among tons of customers registered in their shopping site.

A user can register on the shopping site using only a single E-Mail Address. If he/she wants to create another account using the same E-Mail, it will show a message,  
_"An account with this E-Mail Address already exists, Please Login"_.  
So, every consumer will have a unique E-Mail Address. Hence, all these attributes can uniquely identify a row in a table.

---

## The candidate key set for the above table is :  
{ Customer ID, Pan Number, Email Address }

Say, the Database Administrator of this E-Commerce site picked Customer ID as the Primary Key. Therefore, PAN Number and E-Mail Address will be Alternate Keys or Secondary Keys. Alternate Key has all the properties to become a Primary Key and so is an alternate option.

---

## ALTERNATE Keys in SQL are defined using the SQL constraint UNIQUE.

```

UNIQUE(col\_name(s))

````

- **col_name(s)**: The name of the column(s) in the table which need to be unique.

---

## BASIC SQL QUERY :

1. Creating a Database

```sql
CREATE DATABASE database_name;
````

2. Creating a Table

```sql
CREATE TABLE Table_name(
    col_1 TYPE col_1_constraint,
    col_2 TYPE col_2_constraint,
    col_3 TYPE UNIQUE,
    col_4 TYPE REFERENCES Table_Name(col_name),
    .....
);
```

* **col**: The name of the columns.
* **TYPE**: Data type whether an integer, variable character, etc.
* **col\_constraint**: Constraints in SQL like PRIMARY KEY, NOT NULL, UNIQUE, REFERENCES, etc.
* **col\_3**: Defining an ALTERNATE KEY using constraint UNIQUE.
* **col\_4**: Defining a FOREIGN KEY using constraint REFERENCES.

3. Inserting into a Table

```sql
INSERT INTO Table_name
VALUES(val_1, val_2, val_3, ..........);
```

* **val**: Values in particular column.

4. View The Table

```sql
SELECT * FROM Table_name;
```

---

### Output :

#### Product Table

| Product ID | Product Name | Price |
| ---------- | ------------ | ----- |
| 1001       | Washing Soap | 25    |
| 1020       | Shampoo      | 150   |
| 1030       | Notebook     | 200   |
| 1045       | Headphone    | 1000  |

#### Customer Table

| Customer ID | Customer Name | Email Address                           | Shipping Address      | Pan Number | Product ID |
| ----------- | ------------- | --------------------------------------- | --------------------- | ---------- | ---------- |
| 1           | Madhulika     | [abc@gmail.com](mailto:abc@gmail.com)   | XYZ-Colony, Patna     | XXABX10011 | 1030       |
| 2           | Tanmoy        | [tdq@gmail.com](mailto:tdq@gmail.com)   | ABC-Colony, Guwahati  | DDABX10034 | 1001       |
| 3           | Ritik         | [def@gmail.com](mailto:def@gmail.com)   | XYZ\_Street, Chennai  | ACQBX10555 | 1045       |
| 4           | Satadru       | [sm11@gmail.com](mailto:sm11@gmail.com) | Park\_Street, Kolkata | ZZABX20035 | 1045       |

---

## A pictorial view of all the keys present in the table is shown below :

![Keys Diagram](https://www.geeksforgeeks.org/sql-alternate-key/)
*Note: Replace the URL with an actual image if needed.*

---

## KEYS

---

## Key Differences Between Primary Key and Alternate Key

| Feature                             | Primary Key                        | Alternate Key                                |
| ----------------------------------- | ---------------------------------- | -------------------------------------------- |
| **Uniqueness**                      | Must be unique                     | Must be unique                               |
| **Null Values**                     | Cannot contain NULL values         | Can contain NULL values                      |
| **Use**                             | Used to identify each row uniquely | An alternate option for uniqueness           |
| **Relationship with Candidate Key** | The selected candidate key         | Other candidate keys not selected as primary |
| **Number of Keys**                  | One primary key per table          | Multiple alternate keys possible             |

---

## Conclusion

Alternate Keys are an essential feature in SQL that helps maintain data uniqueness and integrity. While the Primary Key is the most important key used to uniquely identify rows in a table, Alternate Keys provide additional options for uniqueness constraints and can be used to enforce data integrity across multiple columns. Understanding how to use and define alternate keys can significantly improve database design, particularly in systems where multiple attributes could serve as a unique identifier for records.

---
