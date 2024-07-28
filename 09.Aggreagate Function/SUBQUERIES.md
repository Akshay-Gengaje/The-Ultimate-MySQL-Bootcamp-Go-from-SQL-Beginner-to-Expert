Subqueries in MySQL are queries nested inside another query. They can be used in various ways, such as in the `SELECT`, `FROM`, `WHERE`, or `HAVING` clauses, and are useful for breaking down complex queries into simpler components.

### Types of Subqueries

1. **Scalar Subquery**: Returns a single value.
2. **Column Subquery**: Returns a single column of values.
3. **Row Subquery**: Returns a single row of values.
4. **Table Subquery**: Returns a result set that can be treated as a table.

### Basic Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE column_name = (SELECT column_name FROM another_table WHERE condition);
```

### Example Table: `employees`

Let's consider a table `employees` with the following data:

| id  | name       | department | salary | hire_date  |
| --- | ---------- | ---------- | ------ | ---------- |
| 1   | John Doe   | HR         | 60000  | 2022-01-10 |
| 2   | Jane Smith | IT         | 80000  | 2021-03-15 |
| 3   | Sam Brown  | Sales      | 50000  | 2023-02-20 |
| 4   | Lucy White | IT         | 75000  | 2020-11-05 |
| 5   | Mike Green | Marketing  | 65000  | 2023-07-01 |

### Examples of Subqueries

#### Example 1: Subquery in `SELECT`

To find the highest salary in each department and display the department name with the highest salary:

```sql
SELECT department, (SELECT MAX(salary) FROM employees e2 WHERE e2.department = e1.department) AS highest_salary
FROM employees e1
GROUP BY department;
```

**Result:**

| department | highest_salary |
| ---------- | -------------- |
| HR         | 60000          |
| IT         | 80000          |
| Sales      | 50000          |
| Marketing  | 65000          |

This query uses a subquery in the `SELECT` clause to find the maximum salary for each department.

#### Example 2: Subquery in `WHERE`

To find employees who earn more than the average salary:

```sql
SELECT name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

**Result:**

| name       | salary |
| ---------- | ------ |
| Jane Smith | 80000  |
| Lucy White | 75000  |

This query uses a subquery in the `WHERE` clause to filter employees whose salary is greater than the average salary.

#### Example 3: Subquery in `FROM`

To find the department with the highest average salary:

```sql
SELECT department, avg_salary
FROM (SELECT department, AVG(salary) AS avg_salary FROM employees GROUP BY department) AS dept_avg
ORDER BY avg_salary DESC
LIMIT 1;
```

**Result:**

| department | avg_salary |
| ---------- | ---------- |
| IT         | 77500.00   |

This query uses a subquery in the `FROM` clause to calculate the average salary for each department and then selects the department with the highest average salary.

#### Example 4: Subquery in `HAVING`

To find departments where the total salary exceeds the average salary across the company:

```sql
SELECT department, SUM(salary) AS total_salary
FROM employees
GROUP BY department
HAVING total_salary > (SELECT AVG(salary) * COUNT(*) FROM employees);
```

**Result:**

| department | total_salary |
| ---------- | ------------ |
| IT         | 155000       |

This query uses a subquery in the `HAVING` clause to filter departments where the total salary exceeds the average salary times the number of employees.

#### Example 5: Correlated Subquery

A correlated subquery depends on the outer query for its value. To find employees who have the highest salary in their respective department:

```sql
SELECT name, department, salary
FROM employees e1
WHERE salary = (SELECT MAX(salary) FROM employees e2 WHERE e2.department = e1.department);
```

**Result:**

| name       | department | salary |
| ---------- | ---------- | ------ |
| John Doe   | HR         | 60000  |
| Jane Smith | IT         | 80000  |
| Sam Brown  | Sales      | 50000  |
| Mike Green | Marketing  | 65000  |

This query uses a correlated subquery in the `WHERE` clause to find the employee with the highest salary in each department.

#### Example 6: Using `EXISTS` with a Subquery

To find departments that have more than one employee:

```sql
SELECT DISTINCT department
FROM employees e1
WHERE EXISTS (SELECT 1 FROM employees e2 WHERE e2.department = e1.department AND e2.id <> e1.id);
```

**Result:**

| department |
| ---------- |
| IT         |

This query uses the `EXISTS` clause with a subquery to check if there is more than one employee in a department.

### Summary

- **Subqueries** can be used in various parts of a query, such as `SELECT`, `WHERE`, `FROM`, and `HAVING`.
- **Scalar Subqueries** return a single value.
- **Correlated Subqueries** reference columns from the outer query and are evaluated row by row.
- **Subqueries with `EXISTS`** check for the existence of rows matching a condition.
- Subqueries can simplify complex queries by breaking them down into manageable parts.
