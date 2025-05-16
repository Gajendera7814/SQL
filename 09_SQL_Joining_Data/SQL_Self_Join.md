
---

# SQL Self Join

A Self Join in SQL is a powerful technique that allows one to join a table with itself. This operation is helpful when you need to compare rows within the same table based on specific conditions. A Self Join is often used in scenarios where there is hierarchical or relational data within the same table, such as when one employee reports to another in an organizational structure.

---

## What is SQL Self Join?

A Self Join is simply a regular join operation where a table is joined with itself. This allows us to compare rows within the same table, which is particularly useful when working with hierarchical data or when comparing related rows from a single table.

For example, a Self Join can help us retrieve employee-manager relationships, where each employee in the table has a reference to their manager's ID.

---

## Syntax

```sql
SELECT columns
FROM table AS alias1
JOIN table AS alias2 ON alias1.column = alias2.column;
````

### Explanation:

* `SELECT columns`: Specifies the columns you want to retrieve from the self-joined table.
* `FROM table AS alias1`: Specifies the name of the table you want to join with itself.
* `JOIN table AS alias2`: Indicates that we are performing a self-join on the same table.

---

## Example: SQL Self Join to Retrieve Employees and Their Managers

Let's use an illustration to further understand how the self-join functions. Assume that we have a table called `"GFGemployees"` with the columns `employee_id`, `employee_name`, and `manager_id`. Each employee in the company is assigned a manager, and using the `manager_id`s, we can identify each employee. We need to extract the list of employees along with the names of their managers because the `manager_id` column contains the manager ID for each employee.

---

### Step 1: Create the "GFGemployees" table

```sql
CREATE TABLE GFGemployees (
  employee_id INT PRIMARY KEY,
  employee_name VARCHAR(50),
  manager_id INT
);
```

---

### Step 2: Insert data into the 'GFGemployees' table

```sql
INSERT INTO GFGemployees (employee_id, employee_name, manager_id)
VALUES
  (1, 'Zaid', 3),
  (2, 'Rahul', 3),
  (3, 'Raman', 4),
  (4, 'Kamran', NULL),
  (5, 'Farhan', 4);
```

#### Output:

| employee\_id | employee\_name | manager\_id |
| ------------ | -------------- | ----------- |
| 1            | Zaid           | 3           |
| 2            | Rahul          | 3           |
| 3            | Raman          | 4           |
| 4            | Kamran         | NULL        |
| 5            | Farhan         | 4           |

---

### Step 3: Explanation and Implementation of Self Join

Now, we need to perform a self join on the table we created (`GFGemployees`) to retrieve the list of employees and their corresponding manager names. We will create two different aliases for the `GFGemployees` table:

* `e` → Represents employee's information
* `m` → Represents manager's information

By joining the table with itself using the `manager_id` and `employee_id` columns, we can generate relationships between employees and their managers.

---

### Step 4: Query for Self Join

```sql
SELECT e.employee_name AS employee,
       m.employee_name AS manager
FROM GFGemployees AS e
JOIN GFGemployees AS m
ON e.manager_id = m.employee_id;
```

#### Output:

| employee | manager |
| -------- | ------- |
| Zaid     | Raman   |
| Rahul    | Raman   |
| Raman    | Kamran  |
| Farhan   | Kamran  |

---

## Applications of SQL Self Join

* **Hierarchical Data**: Self joins are particularly useful when working with hierarchical data such as organizational structures, where each employee has a manager.
* **Finding Relationships**: Self joins can be used to find relationships within the same table, such as identifying employees with similar attributes or roles.
* **Data Comparison**: Self joins allow comparing records within the same table based on specific conditions, like comparing sales figures of employees working in the same department.

---
