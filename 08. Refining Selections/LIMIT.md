The `LIMIT` clause in MySQL is used to specify the number of records you want to retrieve from the result set. It's particularly useful when you need to paginate results or when you only need a subset of data. The basic syntax of the `LIMIT` clause is:

```sql
SELECT column1, column2, ...
FROM table_name
LIMIT offset, row_count;
```

- **offset**: The position of the first row to return. The first row has an offset of `0`.
- **row_count**: The maximum number of rows to return.

### Example 1: Basic Usage of `LIMIT`

Suppose you have a table `employees` with the following data:

| id  | name       | department |
| --- | ---------- | ---------- |
| 1   | John Doe   | HR         |
| 2   | Jane Smith | IT         |
| 3   | Sam Brown  | Sales      |
| 4   | Lucy White | Marketing  |
| 5   | Mike Green | IT         |

To retrieve the first 3 rows from the `employees` table:

```sql
SELECT * FROM employees
LIMIT 3;
```

**Result:**

| id  | name       | department |
| --- | ---------- | ---------- |
| 1   | John Doe   | HR         |
| 2   | Jane Smith | IT         |
| 3   | Sam Brown  | Sales      |

### Example 2: Using `LIMIT` with Offset

If you want to skip the first 2 rows and retrieve the next 2 rows:

```sql
SELECT * FROM employees
LIMIT 2, 2;
```

**Result:**

| id  | name       | department |
| --- | ---------- | ---------- |
| 3   | Sam Brown  | Sales      |
| 4   | Lucy White | Marketing  |

### Example 3: Using `LIMIT` for Pagination

When you need to paginate results, `LIMIT` is often used in conjunction with an `OFFSET` value. For example, to get the results for the second page with 2 rows per page:

```sql
SELECT * FROM employees
LIMIT 2 OFFSET 2;
```

This is equivalent to:

```sql
SELECT * FROM employees
LIMIT 2, 2;
```

**Result:**

| id  | name       | department |
| --- | ---------- | ---------- |
| 3   | Sam Brown  | Sales      |
| 4   | Lucy White | Marketing  |

### Example 4: Using `LIMIT` Without `OFFSET`

If you only specify the row count without an offset, MySQL will return the first `n` rows:

```sql
SELECT * FROM employees
LIMIT 4;
```

**Result:**

| id  | name       | department |
| --- | ---------- | ---------- |
| 1   | John Doe   | HR         |
| 2   | Jane Smith | IT         |
| 3   | Sam Brown  | Sales      |
| 4   | Lucy White | Marketing  |

### Example 5: `LIMIT` with ORDER BY

`LIMIT` is often used with `ORDER BY` to get the top `n` records based on a specific order. For example, to get the first 2 employees sorted by name:

```sql
SELECT * FROM employees
ORDER BY name ASC
LIMIT 2;
```

**Result:**

| id  | name       | department |
| --- | ---------- | ---------- |
| 1   | John Doe   | HR         |
| 2   | Jane Smith | IT         |

This will return the first 2 records in alphabetical order by the `name` column.

### Summary

- `LIMIT` allows you to control the number of rows returned by a query.
- You can use `OFFSET` to skip a specified number of rows.
- Commonly used in pagination and retrieving top `n` records.
