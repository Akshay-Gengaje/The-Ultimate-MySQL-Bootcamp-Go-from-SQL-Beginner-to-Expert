The `MIN()` and `MAX()` functions, when used with the `GROUP BY` clause in MySQL, allow you to find the smallest and largest values within specific groups of data. This is particularly useful when you want to analyze data within categories or segments, such as finding the minimum and maximum values for each department in a company.

### Basic Syntax with `GROUP BY`

```sql
SELECT column1, MIN(column2) AS min_value, MAX(column2) AS max_value
FROM table_name
GROUP BY column1;
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

### Examples of Using `MIN()` and `MAX()` with `GROUP BY`

#### Example 1: Finding the Minimum and Maximum Salary in Each Department

To find the minimum and maximum salary for employees in each department:

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

#### Example 2: Finding the Earliest and Latest Hire Date in Each Department

To find the earliest and latest hire date for each department:

```sql
SELECT department, MIN(hire_date) AS earliest_hire, MAX(hire_date) AS latest_hire
FROM employees
GROUP BY department;
```

**Result:**

| department | earliest_hire | latest_hire |
| ---------- | ------------- | ----------- |
| HR         | 2022-01-10    | 2022-01-10  |
| IT         | 2020-11-05    | 2021-03-15  |
| Sales      | 2023-02-20    | 2023-02-20  |
| Marketing  | 2023-07-01    | 2023-07-01  |

This query groups the data by `department` and finds the earliest and latest hire date within each department.

#### Example 3: Finding the Minimum and Maximum Salary by Department for Specific Conditions

To find the minimum and maximum salary for departments with a minimum salary greater than 60000:

```sql
SELECT department, MIN(salary) AS min_salary, MAX(salary) AS max_salary
FROM employees
GROUP BY department
HAVING MIN(salary) > 60000;
```

**Result:**

| department | min_salary | max_salary |
| ---------- | ---------- | ---------- |
| IT         | 75000      | 80000      |
| Marketing  | 65000      | 65000      |

This query groups the data by `department` and applies a condition using the `HAVING` clause to include only those departments where the minimum salary is greater than 60000.

#### Example 4: Finding the Minimum and Maximum Hire Dates by Year

To find the earliest and latest hire date for each year:

```sql
SELECT YEAR(hire_date) AS hire_year, MIN(hire_date) AS earliest_hire, MAX(hire_date) AS latest_hire
FROM employees
GROUP BY hire_year;
```

**Result:**

| hire_year | earliest_hire | latest_hire |
| --------- | ------------- | ----------- |
| 2020      | 2020-11-05    | 2020-11-05  |
| 2021      | 2021-03-15    | 2021-03-15  |
| 2022      | 2022-01-10    | 2022-01-10  |
| 2023      | 2023-02-20    | 2023-07-01  |

This query groups the data by the year of the hire date and finds the earliest and latest hire dates for each year.

#### Example 5: Finding Minimum and Maximum Salary in Each Department with Additional Information

To find the minimum and maximum salary in each department, along with the names of the employees earning those salaries:

```sql
SELECT e.department, e.name, e.salary, 
       (SELECT MIN(salary) FROM employees WHERE department = e.department) AS min_salary,
       (SELECT MAX(salary) FROM employees WHERE department = e.department) AS max_salary
FROM employees e
ORDER BY department, salary;
```

**Result:**

| department | name       | salary | min_salary | max_salary |
| ---------- | ---------- | ------ | ---------- | ---------- |
| HR         | John Doe   | 60000  | 60000      | 60000      |
| IT         | Lucy White | 75000  | 75000      | 80000      |
| IT         | Jane Smith | 80000  | 75000      | 80000      |
| Marketing  | Mike Green | 65000  | 65000      | 65000      |
| Sales      | Sam Brown  | 50000  | 50000      | 50000      |

This query provides detailed information, including the minimum and maximum salary in each department, along with the employee names who earn those salaries.

### Summary

- **`MIN()` and `MAX()` with `GROUP BY`** allow you to find the smallest and largest values within specific groups, such as departments or years.
- **`HAVING` clause** can be used to filter the results of grouped data based on the result of aggregate functions.
- Subqueries can be used to add additional information or conditions related to the `MIN()` and `MAX()` values within groups.
- These functions are helpful for analyzing data within categories, such as determining the range of salaries or identifying the span of hire dates in each department.
