

##  What are SQL Operators?

SQL operators are **symbols or keywords** used in SQL statements to **perform operations** on data, such as comparisons, calculations, logic checks, or filtering.

They are commonly used in:
- `WHERE` clauses
- `SELECT` statements
- Conditions and joins

---

## 🧩 Types of SQL Operators

### 1. 🔢 **Arithmetic Operators**
Used to perform mathematical calculations.

| Operator | Description | Example |
|----------|-------------|---------|
| `+` | Addition | `SELECT 10 + 5;` |
| `-` | Subtraction | `SELECT 10 - 5;` |
| `*` | Multiplication | `SELECT 10 * 5;` |
| `/` | Division | `SELECT 10 / 5;` |
| `%` | Modulus (remainder) | `SELECT 10 % 3;` |

---

### 2. 🔍 **Comparison Operators**
Used to compare two values.

| Operator | Description | Example |
|----------|-------------|---------|
| `=` | Equal to | `WHERE age = 25` |
| `!=` or `<>` | Not equal to | `WHERE name <> 'John'` |
| `>` | Greater than | `WHERE salary > 50000` |
| `<` | Less than | `WHERE marks < 40` |
| `>=` | Greater than or equal to | `WHERE age >= 18` |
| `<=` | Less than or equal to | `WHERE rating <= 5` |

---

### 3. 🧠 **Logical Operators**
Used to combine multiple conditions.

| Operator | Description | Example |
|----------|-------------|---------|
| `AND` | All conditions must be true | `WHERE age > 18 AND city = 'Delhi'` |
| `OR` | At least one condition is true | `WHERE city = 'Delhi' OR city = 'Mumbai'` |
| `NOT` | Reverses the condition | `WHERE NOT (status = 'active')` |

---

### 4. 📂 **Special Operators**
Used for specific filtering conditions.

| Operator | Description | Example |
|----------|-------------|---------|
| `BETWEEN` | Checks value in a range | `WHERE age BETWEEN 18 AND 30` |
| `IN` | Matches any value in a list | `WHERE country IN ('India', 'USA')` |
| `LIKE` | Pattern matching (wildcards) | `WHERE name LIKE 'A%'` |
| `IS NULL` | Checks for NULL values | `WHERE phone IS NULL` |

---

## 📝 Example Query Using Multiple Operators

```sql
SELECT name, age, city
FROM users
WHERE age BETWEEN 20 AND 30
  AND city IN ('Delhi', 'Mumbai')
  AND is_active = TRUE;