The `MIN()` and `MAX()` functions in MySQL are aggregate functions used to find the smallest and largest values in a set of values, respectively. They are often used with the `GROUP BY` clause to find the minimum or maximum values within specific groups of data.

### Basic Syntax

```sql
SELECT MIN(column_name) AS min_value, MAX(column_name) AS max_value
FROM table_name
WHERE condition;
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

### Examples of `MIN()` and `MAX()` with Aggregation

#### Example 1: Finding the Minimum and Maximum Salary

To find the minimum and maximum salary among all employees:

```sql
SELECT MIN(salary) AS min_salary, MAX(salary) AS max_salary
FROM employees;
```

**Result:**

| min_salary | max_salary |
| ---------- | ---------- |
| 50000      | 80000      |

This query returns the smallest and largest salary values from the `employees` table.

#### Example 2: Using `GROUP BY` with `MIN()` and `MAX()`

To find the minimum and maximum salary in each department:

```sql
SELECT department, MIN(salary) AS min_salary, MAX(salary) AS max_salary
FROM employees
GROUP BY department;
```

**Result:**

| department | min_salary | max_salary |
| ---------- | ---------- | ---------- |
| HR         | 60000      | 60000      |
| IT         | 75000      | 80000      |
| Sales      | 50000      | 50000      |
| Marketing  | 65000      | 65000      |

This query groups the data by `department` and calculates the minimum and maximum salary within each department.

#### Example 3: Finding the Earliest and Latest Hire Dates

To find the earliest and latest hire date in the company:

```sql
SELECT MIN(hire_date) AS earliest_hire_date, MAX(hire_date) AS latest_hire_date
FROM employees;
```

**Result:**

| earliest_hire_date | latest_hire_date |
| ------------------ | ---------------- |
| 2020-11-05         | 2023-07-01       |

This query finds the earliest and latest dates when employees were hired.

#### Example 4: Using `MIN()` and `MAX()` with a Condition

To find the minimum and maximum salary among employees in the IT department:

```sql
SELECT MIN(salary) AS min_salary, MAX(salary) AS max_salary
FROM employees
WHERE department = 'IT';
```

**Result:**

| min_salary | max_salary |
| ---------- | ---------- |
| 75000      | 80000      |

This query filters the employees by the IT department and then finds the minimum and maximum salary within that department.

#### Example 5: Finding the Oldest and Newest Employee in Each Department

To find the hire dates of the oldest (earliest hired) and newest (latest hired) employees in each department:

```sql
SELECT department, MIN(hire_date) AS earliest_hire_date, MAX(hire_date) AS latest_hire_date
FROM employees
GROUP BY department;
```

**Result:**

| department | earliest_hire_date | latest_hire_date |
| ---------- | ------------------ | ---------------- |
| HR         | 2022-01-10         | 2022-01-10       |
| IT         | 2020-11-05         | 2021-03-15       |
| Sales      | 2023-02-20         | 2023-02-20       |
| Marketing  | 2023-07-01         | 2023-07-01       |

This query groups the data by `department` and finds the earliest and latest hire dates within each department.

#### Example 6: Combining `MIN()` and `MAX()` with Other Aggregations

To find the minimum, maximum, and average salary in each department:

```sql
SELECT department, MIN(salary) AS min_salary, MAX(salary) AS max_salary, AVG(salary) AS avg_salary
FROM employees
GROUP BY department;
```

**Result:**

| department | min_salary | max_salary | avg_salary |
| ---------- | ---------- | ---------- | ---------- |
| HR         | 60000      | 60000      | 60000.00   |
| IT         | 75000      | 80000      | 77500.00   |
| Sales      | 50000      | 50000      | 50000.00   |
| Marketing  | 65000      | 65000      | 65000.00   |

This query calculates the minimum, maximum, and average salary within each department.

### Summary

- The `MIN()` function returns the smallest value in a set, while the `MAX()` function returns the largest.
- These functions are often used with `GROUP BY` to find the minimum or maximum values within specific groups.
- `MIN()` and `MAX()` can be used with different data types, including numbers and dates.
- You can combine `MIN()` and `MAX()` with other aggregate functions like `AVG()` and `SUM()` for more complex queries.
