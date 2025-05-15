
---

# SQL | WITH Clause (Common Table Expressions)

---

## 📌 Introduction

SQL queries can sometimes become complex—especially when dealing with multiple nested subqueries, aggregations, and joins. The **SQL `WITH` clause**, also known as **Common Table Expressions (CTEs)**, simplifies such queries by allowing temporary result sets that can be referred to within the main query.

This makes SQL easier to **read**, **maintain**, and even **optimize**.

---

## 📘 What is SQL WITH Clause?

The **`WITH` clause** allows us to define **temporary result sets (CTEs)** that exist only during the execution of the query. These result sets act like virtual tables and can be reused in the main query multiple times.

It’s commonly used to simplify:

* Nested queries
* Recursive queries
* Aggregations
* Complex joins

---

## ✅ Why Use the WITH Clause?

| Benefit                     | Description                                             |
| --------------------------- | ------------------------------------------------------- |
| 📖 Improves Readability     | Breaks down complex SQL into smaller parts              |
| 🔧 Enhances Maintainability | Easier to debug and modify                              |
| ⚡ Optimizes Performance     | Avoids repeated subqueries                              |
| ♻ Reusable Logic            | Subqueries can be used multiple times in the main query |

---

## 🧾 Syntax

```sql
WITH temporaryTable (averageValue) AS (
    SELECT AVG (Attr1)
    FROM Table
)
SELECT Attr1
FROM Table, temporaryTable
WHERE Table.Attr1 > temporaryTable.averageValue;
```

---

### 🔍 Key Terms

* `temporaryTable`: Name of the temporary table (CTE)
* `averageValue`: Alias for the column in the CTE
* The main query uses the temporary table in filtering or joining logic

📝 **Note**: The `WITH` clause is evaluated first, its output is stored in a temporary relation, and then the main query is executed.

---

## 💡 Examples of SQL WITH Clause

---

### 📌 Example 1: Finding Employees with Above-Average Salary

#### Employee Table

| EmployeeID | Name   | Salary |
| ---------- | ------ | ------ |
| 100011     | Smith  | 50000  |
| 100022     | Bill   | 94000  |
| 100027     | Sam    | 70550  |
| 100845     | Walden | 80000  |
| 115585     | Erik   | 60000  |
| 1100070    | Kate   | 69000  |

#### Query

```sql
WITH temporaryTable (averageValue) AS (
    SELECT AVG(Salary)
    FROM Employee
)
SELECT EmployeeID, Name, Salary 
FROM Employee, temporaryTable 
WHERE Employee.Salary > temporaryTable.averageValue;
```

#### Output

| EmployeeID | Name   | Salary |
| ---------- | ------ | ------ |
| 100022     | Bill   | 94000  |
| 100845     | Walden | 80000  |

#### Explanation

* The **average salary** of all employees is **70591**
* The query returns only those employees whose salary is **greater than 70591**

---

### 📌 Example 2: Finding Airlines with High Pilot Salaries

#### Pilot Table

| EmployeeID | Airline    | Name   | Salary |
| ---------- | ---------- | ------ | ------ |
| 70007      | Airbus 380 | Kim    | 60000  |
| 70002      | Boeing     | Laura  | 20000  |
| 10027      | Airbus 380 | Will   | 80050  |
| 10778      | Airbus 380 | Warren | 80780  |
| 115585     | Boeing     | Smith  | 25000  |
| 114070     | Airbus 380 | Katy   | 78000  |

#### Query

```sql
WITH totalSalary(Airline, total) AS (
    SELECT Airline, SUM(Salary)
    FROM Pilot
    GROUP BY Airline
),
airlineAverage (avgSalary) AS (
    SELECT AVG(Salary)
    FROM Pilot 
)
SELECT Airline
FROM totalSalary, airlineAverage
WHERE totalSalary.total > airlineAverage.avgSalary;
```

#### Output

| Airline    |
| ---------- |
| Airbus 380 |

#### Explanation

* Total salary for **Airbus 380** = 298,830
* Total salary for **Boeing** = 45,000
* Average salary of all pilots = **57,305**
* Only **Airbus 380** has a total salary greater than the average

---

## ✅ Key Benefits of Using the WITH Clause

1. **Improved Readability**: Break down logic into smaller chunks
2. **Reusable Subqueries**: Avoid repeating the same logic
3. **Performance Optimization**: Avoid redundant calculations
4. **Easy Debugging**: Isolate and test individual components of the query

---

## ⚠️ Important Points to Remember

| Point                | Detail                                                      |
| -------------------- | ----------------------------------------------------------- |
| ⏱ Temporary Lifetime | CTEs exist only during query execution                      |
| 🔁 Multiple CTEs     | You can define and chain multiple CTEs                      |
| ⚙️ Efficiency        | Large CTEs can impact performance—check your execution plan |

### Example with Multiple CTEs:

```sql
WITH CTE1 AS (...), 
     CTE2 AS (...)
SELECT *
FROM CTE1, CTE2;
```

---

## 🧠 Conclusion

The **SQL `WITH` clause** (Common Table Expressions) is a powerful feature for simplifying and optimizing complex SQL queries. It provides:

* Clear structure to your logic
* Performance gains by avoiding repeated subqueries
* Flexibility in breaking down and organizing query components

**Use the WITH clause** when you need clean, maintainable, and efficient SQL code.

---
