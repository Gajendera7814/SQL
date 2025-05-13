
---

##  What are SQL Data Types?

SQL data types define the kind of **values** that can be stored in a database column.

They help SQL engines know:
- How much space to allocate
- How to validate inputs
- How to compare and process data

> Example: Use `INT` for age, `VARCHAR` for names, `DATE` for birthdates.

---

## ✅ Why SQL Data Types Matter

| Reason | Benefit |
|--------|---------|
| 🎯 Accuracy | Prevents invalid data (e.g., text in a numeric field) |
| 💾 Storage Efficiency | Saves space with appropriate types |
| ⚡ Performance | Improves sorting, indexing, and querying |
| 🛡️ Validation | Ensures data integrity |
| 🔄 Consistency | Avoids type mismatch and runtime errors |

---

## 🧩 Common SQL Data Types

### 🔢 Numeric Types
| Type | Description |
|------|-------------|
| `INT` | Whole numbers (e.g., 1, 99) |
| `SMALLINT`, `TINYINT` | Smaller range of integers |
| `BIGINT` | Large integers |
| `DECIMAL(p, s)` | Fixed precision (e.g., money) |
| `FLOAT`, `DOUBLE` | Floating-point (approximate) decimals |

---

### 🔤 String (Character) Types
| Type | Description |
|------|-------------|
| `CHAR(n)` | Fixed-length string (padded if short) |
| `VARCHAR(n)` | Variable-length string |
| `TEXT` | Large text fields |

---

### 📅 Date & Time Types
|       Type    |               Description             |
|---------------|---------------------------------------|
| `DATE`        | Only date (`YYYY-MM-DD`)              |
| `TIME`        | Only time (`HH:MM:SS`)                |
| `DATETIME`    | Date and time                         |
| `TIMESTAMP`   | Auto-tracked time (often for updates) |

---

### ✅ Boolean Type
|   Type    |           Description             |
|-----------|-----------------------------------|
| `BOOLEAN` | TRUE or FALSE (stored as 1 or 0)  |

---

### 📦 Binary Type
|  Type  |          Description                 |
|--------|--------------------------------------|
| `BLOB` | Binary Large Object (images, files)  |

---

## 📝 Example Table Using Data Types

```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(100),
    salary DECIMAL(10, 2),
    is_active BOOLEAN,
    joined_at DATE
);