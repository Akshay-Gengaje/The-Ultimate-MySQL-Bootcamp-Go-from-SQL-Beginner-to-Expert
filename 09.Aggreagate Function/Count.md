The `COUNT()` function in MySQL is an aggregate function that returns the number of rows that match a specified condition. It's commonly used to count the number of records in a table, or to count the number of non-NULL values in a specific column.

### Basic Syntax

```sql
SELECT COUNT(column_name)
FROM table_name
WHERE condition;
```

- **`COUNT(*)`**: Counts all rows in the result set, including those with NULL values.
- **`COUNT(column_name)`**: Counts the number of non-NULL values in a specific column.
- **`COUNT(DISTINCT column_name)`**: Counts the number of unique (distinct) non-NULL values in a specific column.

### Example Table: `employees`

Let's consider a table `employees` with the following data:

| id  | name       | department | salary | hire_date  |
| --- | ---------- | ---------- | ------ | ---------- |
| 1   | John Doe   | HR         | 60000  | 2022-01-10 |
| 2   | Jane Smith | IT         | 80000  | 2021-03-15 |
| 3   | Sam Brown  | Sales      | 50000  | 2023-02-20 |
| 4   | Lucy White | IT         | 75000  | 2020-11-05 |
| 5   | Mike Green | Marketing  | 65000  | 2023-07-01 |

### Examples of `COUNT()`

#### Example 1: Counting All Rows

To count the total number of employees:

```sql
SELECT COUNT(*) AS total_employees
FROM employees;
```

**Result:**

| total_employees |
| --------------- |
| 5               |

#### Example 2: Counting Non-NULL Values in a Column

To count the number of employees with a specified salary (non-NULL):

```sql
SELECT COUNT(salary) AS total_salaried_employees
FROM employees;
```

**Result:**

| total_salaried_employees |
| ------------------------ |
| 5                        |

#### Example 3: Counting Distinct Values

To count the number of distinct departments in the `employees` table:

```sql
SELECT COUNT(DISTINCT department) AS unique_departments
FROM employees;
```

**Result:**

| unique_departments |
| ------------------ |
| 4                  |

#### Example 4: Counting with a Condition

To count the number of employees in the IT department:

```sql
SELECT COUNT(*) AS it_employees
FROM employees
WHERE department = 'IT';
```

**Result:**

| it_employees |
| ------------ |
| 2            |

#### Example 5: Using `COUNT()` with `GROUP BY`

To count the number of employees in each department:

```sql
SELECT department, COUNT(*) AS employee_count
FROM employees
GROUP BY department;
```

**Result:**

| department | employee_count |
| ---------- | -------------- |
| HR         | 1              |
| IT         | 2              |
| Sales      | 1              |
| Marketing  | 1              |

#### Example 6: Counting with `HAVING`

To find departments with more than 1 employee:

```sql
SELECT department, COUNT(*) AS employee_count
FROM employees
GROUP BY department
HAVING COUNT(*) > 1;
```

**Result:**

| department | employee_count |
| ---------- | -------------- |
| IT         | 2              |

### Summary

- `COUNT(*)` counts all rows, including those with NULL values.
- `COUNT(column_name)` counts non-NULL values in a specific column.
- `COUNT(DISTINCT column_name)` counts unique non-NULL values.
- `COUNT()` is often used with `GROUP BY` to count occurrences within groups.
- `HAVING` can be used to filter groups based on the result of `COUNT()`.

These examples demonstrate how `COUNT()` can be used in different scenarios, especially when working with aggregation in MySQL.
