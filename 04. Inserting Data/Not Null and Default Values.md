# NOT NULL & DEFAULT Values -

In MySQL, you can enforce data integrity and provide default values for columns when creating or altering tables using the `NOT NULL` and `DEFAULT` constraints.

**1. NOT NULL Constraint:**

- Ensures that a column cannot contain missing values (NULL).
- Enforces data presence, preventing incomplete records.

**Syntax:**

When creating a table:

```sql
CREATE TABLE table_name (
  column1 data_type NOT NULL,
  column2 data_type NOT NULL,
  ...
);
```

When altering an existing table:

```sql
ALTER TABLE table_name
MODIFY column_name data_type NOT NULL;
```

**2. DEFAULT Value:**

- Specifies a value to be automatically inserted into a column if no value is provided during data insertion.
- Useful for setting common default values for optional columns.

**Syntax:**

When creating a table:

```sql
CREATE TABLE table_name (
  column1 data_type DEFAULT default_value,
  column2 data_type,  -- No DEFAULT specified (NULL allowed)
  ...
);
```

When altering an existing table:

```sql
ALTER TABLE table_name
MODIFY column_name data_type DEFAULT default_value;
```

**Example:**

Let's create a `customers` table with columns for `id` (auto-increment), `name` (required), and `email` (optional with a default value):

```sql
CREATE TABLE customers (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(50) NOT NULL,
  email VARCHAR(100) DEFAULT 'unknown@example.com'
);
```

In this example:

- `name` is mandatory (NOT NULL) and won't allow NULL values.
- `email` is optional, but if no value is provided during insertion, the default value `'unknown@example.com'` will be used.

**Key Points:**

- `NOT NULL` and `DEFAULT` can be used together or independently.
- Use `NOT NULL` for mandatory columns to ensure data integrity.
- Use `DEFAULT` for optional columns to provide a sensible default value.
- Remember that the data type of the `DEFAULT` value must be compatible with the column's data type.

By effectively combining `NOT NULL` and `DEFAULT` constraints, you can create robust tables that enforce data presence and provide predictable default behavior while inserting data into your MySQL database.
