The `LIKE` operator in MySQL is used to search for a specified pattern in a column. It is often used with `SELECT` statements to find rows that match a specific pattern within a string.

### Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE column_name LIKE pattern;
```

### Wildcards in `LIKE`

- **`%`**: Represents zero or more characters.
- **`_`**: Represents a single character.

### Examples

#### Example 1: Basic Usage of `LIKE` with `%`

Suppose you have a table `customers` with the following data:

| id  | name         | city        |
| --- | ------------ | ----------- |
| 1   | John Doe     | New York    |
| 2   | Jane Smith   | Los Angeles |
| 3   | Sam Brown    | Chicago     |
| 4   | Linda White  | New Orleans |
| 5   | Mike Johnson | Miami       |

If you want to find all customers whose name starts with "J":

```sql
SELECT * FROM customers
WHERE name LIKE 'J%';
```

**Result:**

| id  | name       | city        |
| --- | ---------- | ----------- |
| 1   | John Doe   | New York    |
| 2   | Jane Smith | Los Angeles |

#### Example 2: Using `%` in the Middle of a Pattern

To find customers whose name contains "Smith":

```sql
SELECT * FROM customers
WHERE name LIKE '%Smith%';
```

**Result:**

| id  | name       | city        |
| --- | ---------- | ----------- |
| 2   | Jane Smith | Los Angeles |

#### Example 3: Using `%` at the End of a Pattern

To find customers whose city ends with "York":

```sql
SELECT * FROM customers
WHERE city LIKE '%York';
```

**Result:**

| id  | name     | city     |
| --- | -------- | -------- |
| 1   | John Doe | New York |

#### Example 4: Using `_` for Single Character Matching

To find customers whose name is "John" but may have any single character at the end, such as "John" or "Johnn":

```sql
SELECT * FROM customers
WHERE name LIKE 'John_';
```

**Result:**
(Suppose there are no names like "Johnn" in the table)

| id  | name     | city     |
| --- | -------- | -------- |
| 1   | John Doe | New York |

#### Example 5: Combining `%` and `_` Wildcards

To find customers whose name starts with "J", has exactly 4 characters, and ends with "n":

```sql
SELECT * FROM customers
WHERE name LIKE 'J__n';
```

**Result:**
(Suppose "John" and "Jean" exist)

| id  | name       | city        |
| --- | ---------- | ----------- |
| 1   | John Doe   | New York    |
| 3   | Jean Smith | Los Angeles |

### Example 6: Case Sensitivity in `LIKE`

In MySQL, the `LIKE` operator is case-insensitive by default (for `CHAR` and `VARCHAR` columns using a case-insensitive collation). To match case-sensitive patterns, use `BINARY`:

```sql
SELECT * FROM customers
WHERE BINARY name LIKE 'john%';
```

This will only return rows where the name starts with lowercase "john", not "John" or "JOHN".

### Example 7: Escaping Special Characters

If you want to search for a literal `%` or `_`, you need to escape these characters using a backslash `\` or define an escape character with the `ESCAPE` keyword:

```sql
SELECT * FROM customers
WHERE name LIKE '%\%%' ESCAPE '\';
```

This will match any name that contains a literal `%`.

### Summary

- The `LIKE` operator is used for pattern matching in MySQL.
- `%` is used to represent zero or more characters.
- `_` is used to represent a single character.
- `BINARY` can be used for case-sensitive searches.
- Special characters like `%` and `_` can be escaped if needed.
