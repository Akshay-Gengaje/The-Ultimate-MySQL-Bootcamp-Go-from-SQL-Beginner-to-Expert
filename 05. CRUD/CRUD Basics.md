# CRUD Basics - 

**Create (C):**

- Involves creating new tables to store data.
- Uses the `CREATE TABLE` statement followed by the table name and its structure definition within parentheses.
- Structure definition includes column names, data types (e.g., `INT`, `VARCHAR`), and constraints (e.g., `PRIMARY KEY`).

**Example:**

```sql
CREATE TABLE customers (
  id INT PRIMARY KEY AUTO_INCREMENT,
  name VARCHAR(255) NOT NULL,
  email VARCHAR(255) UNIQUE
);
```

This query creates a table named `customers` with three columns:

- `id`: An integer set as the primary key with auto-increment for unique identification.
- `name`: A string (varchar) to store customer names, not allowing null values.
- `email`: Another string (varchar) to store email addresses, with a unique constraint ensuring no duplicates.

**Read (R):**

- Focuses on retrieving data from existing tables.
- Employs the `SELECT` statement to fetch specific columns or all data from a table.
- Can incorporate `WHERE` clauses to filter results based on conditions.

**Example:**

```sql
SELECT * FROM customers;  -- Selects all columns from the 'customers' table
SELECT id, name FROM customers WHERE email = 'johndoe@example.com';  -- Selects specific columns with a filter on the 'email' column
```

The first query retrieves all data (all columns and rows) from the `customers` table. The second query selects only `id` and `name` columns for customers whose email matches the specified condition.

**Update (U):**

- Modifies existing data within a table.
- Utilizes the `UPDATE` statement to change values in specific columns or rows.
- Often used with `WHERE` clauses to target particular data for updates.

**Example:**

```sql
UPDATE customers SET name = 'Jane Doe' WHERE id = 1;  -- Updates the 'name' for the customer with id 1
UPDATE customers SET email = 'new_email@example.com' WHERE email LIKE '%@gmail.com';  -- Updates emails ending with '@gmail.com'
```

The first query updates the `name` column to "Jane Doe" for the customer with the ID of 1. The second query updates email addresses ending with "@gmail.com" to a new email address.

**Delete (D):**

- Removes unwanted data from a table.
- Achieved using the `DELETE` statement to target specific rows.
- Similar to `UPDATE`, it can leverage `WHERE` clauses for conditional deletion.

**Example:**

```sql
DELETE FROM customers WHERE email IS NULL;  -- Deletes rows with null email values
DELETE FROM customers WHERE id = 5;  -- Deletes the customer record with id 5
```

The first query deletes customer records with null email values. The second query removes the customer record with the ID of 5.

**Remember:**

- Always be cautious with `DELETE` operations, as they permanently remove data.
- Consider using `WHERE` clauses precisely to avoid unintended deletions.
- Explore additional functionalities like `JOIN` clauses for combining data from multiple tables and advanced filtering techniques.

By effectively using CRUD operations with MySQL, you can efficiently manage and manipulate data within your database.
