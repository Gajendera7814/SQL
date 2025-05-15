
---

## 📖 What is RANDOM() in SQL?

The `RANDOM()` (or `RAND()` in MySQL) function is used to fetch **random rows** from a table. This is useful in many real-world scenarios, including:

- Selecting random employees for sending emails
- Displaying random questions in online tests
- Performing random sampling in data analysis

---

## 📊 Use Case Example: Customer Information Table

Let’s consider the following table for demonstration:

### Customer Information

| Customer ID | Customer Name | E-Mail Address   |
|-------------|----------------|------------------|
| 1           | Srishti        | abc@gmail.com    |
| 2           | Rajdeep        | def@gmail.com    |
| 3           | Aman           | xxx@gmail.com    |
| 4           | Pooja          | xyz@gmail.com    |

---

## ✅ Example 1: Using `RAND()` in MySQL

### Syntax to Fetch All Rows in Random Order:

```sql
SELECT col_1, col_2, ...
FROM Table_Name
ORDER BY RAND();
````

* `col_1`, `col_2`: Columns to be selected
* `ORDER BY RAND()` will shuffle the rows randomly

### Syntax to Fetch a Single Random Row:

```sql
SELECT col_1, col_2, ...
FROM Table_Name
ORDER BY RAND()
LIMIT 1;
```

### Example Output (varies each time):

| Customer ID | Customer Name | E-Mail Address                        |
| ----------- | ------------- | ------------------------------------- |
| 3           | Aman          | [xxx@gmail.com](mailto:xxx@gmail.com) |

---

## 🐘 Example 2: Using `RANDOM()` in PostgreSQL and SQLite

The approach is the **same** as MySQL, but replace `RAND()` with `RANDOM()`.

### Syntax:

```sql
SELECT col_1, col_2, ...
FROM Table_Name
ORDER BY RANDOM()
LIMIT 1;
```

### Output:

| RANDOM ROW                       |
| -------------------------------- |
| Any single row randomly selected |

Each time you run the query, a different row might be returned, as the function generates new random values per execution.

---

## ⚙️ Performance Considerations

Using `RANDOM()` or `RAND()` involves sorting **every row by a random number**, which can be **computationally expensive** for large datasets.

### 🔧 Optimization Tips:

* ✅ **Use `LIMIT`**: Always restrict the number of rows using `LIMIT` to avoid full-table scans.
* ✅ **Use indexed columns**: If applying filters, make sure filter columns are indexed to speed up lookups.
* ❌ Avoid using this method on millions of records without constraints or filters.

---

## 📌 Summary Table

| SQL Dialect | Function Used | Example Query                                    |
| ----------- | ------------- | ------------------------------------------------ |
| MySQL       | `RAND()`      | `SELECT * FROM table ORDER BY RAND() LIMIT 1;`   |
| PostgreSQL  | `RANDOM()`    | `SELECT * FROM table ORDER BY RANDOM() LIMIT 1;` |
| SQLite      | `RANDOM()`    | `SELECT * FROM table ORDER BY RANDOM() LIMIT 1;` |

---

## 🧾 Conclusion

In this guide, we explored the usage of the `RANDOM()` or `RAND()` function in SQL to retrieve random rows from a table. Whether you're working with:

* ✅ MySQL → use `RAND()`
* ✅ PostgreSQL / SQLite → use `RANDOM()`

The method to shuffle rows and select random entries remains consistent and highly useful in real-world applications such as:

* Random sampling
* Random user selection
* Randomized quizzes

**Tip**: Always use `LIMIT` and indexed filtering where possible for better performance!

---

## 📚 Related Topics

* SQL `ORDER BY`
* SQL `LIMIT`
* SQL `TOP` (for SQL Server)
* SQL `OFFSET` (pagination)
* SQL `WHERE` clause for filtering random selections

---
