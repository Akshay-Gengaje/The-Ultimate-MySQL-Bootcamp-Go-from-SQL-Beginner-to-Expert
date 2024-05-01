## Database Operations -

1. Showing Databases - 

To show the databases in MySQL, you can use the following SQL command:

```sql
SHOW DATABASES;
```

When you run this command in MySQL, it will display a list of databases that are currently available on the MySQL server. Each row in the result represents a different database.



2. Creating Database - 

   To create a new database in MySQL, you can use the `CREATE DATABASE` statement followed by the name of the database you want to create. Here's the basic syntax:

```sql
CREATE DATABASE database_name;
```

   Replace `database_name` with the name you want to give to your new database. Here's an example:

```sql
CREATE DATABASE my_database;
```

   This will create a new database named `my_database`. Make sure you have the necessary privileges to create databases on your MySQL server.

3. Use Database and Drop Database

To use a specific database in MySQL, you can use the `USE` statement followed by the name of the database you want to switch to. Here's how you do it:

```sql
USE database_name;
```

Replace `database_name` with the name of the database you want to use. For example:

```sql
USE my_database;
```

This command switches your current session to use the `my_database` database. Any subsequent SQL queries you run will operate within this database.

To drop (delete) a database in MySQL, you can use the `DROP DATABASE` statement followed by the name of the database you want to drop. Be very careful with this command as it permanently deletes the database and all its associated data.

```sql
DROP DATABASE database_name;
```

Replace `database_name` with the name of the database you want to drop. For example:

```sql
DROP DATABASE my_database;
```

This command will permanently delete the `my_database` database and all its contents. Make sure you have the necessary permissions and you're absolutely certain you want to delete the database before executing this command.



## Datatypes in Mysql

MySQL supports various data types to store different types of data efficiently. Here's an overview of some common MySQL data types:

1. **Numeric Types**:
   
   - `INT` or `INTEGER`: Integer value, signed or unsigned.
   - `TINYINT`: Very small integer, signed or unsigned.
   - `SMALLINT`: Small integer, signed or unsigned.
   - `MEDIUMINT`: Medium-sized integer, signed or unsigned.
   - `BIGINT`: Large integer, signed or unsigned.
   - `FLOAT`: Single-precision floating-point number.
   - `DOUBLE`: Double-precision floating-point number.
   - `DECIMAL`: Fixed-point decimal numbers.

2. **Date and Time Types**:
   
   - `DATE`: Date value in 'YYYY-MM-DD' format.
   - `TIME`: Time value in 'HH:MM:SS' format.
   - `DATETIME`: Date and time value in 'YYYY-MM-DD HH:MM:SS' format.
   - `TIMESTAMP`: Timestamp value, typically 'YYYY-MM-DD HH:MM:SS'.
   - `YEAR`: Year value in 2-digit or 4-digit format.

3. **String Types**:
   
   - `CHAR`: Fixed-length string.
   - `VARCHAR`: Variable-length string.
   - `TEXT`: Variable-length string with a maximum length.
   - `BINARY`: Fixed-length binary string.
   - `VARBINARY`: Variable-length binary string.
   - `BLOB`: Binary large object.

4. **Spatial Types**:
   
   - `GEOMETRY`: Spatial value for geometric data.
   - `POINT`: Point in a spatial coordinate system.
   - `LINESTRING`: Sequence of points representing a line.
   - `POLYGON`: Polygonal shape consisting of one or more exterior rings and zero or more interior rings.

5. **JSON Type**:
   
   - `JSON`: Stores JSON (JavaScript Object Notation) data.

6. **Other Types**:
   
   - `ENUM`: Enumerated type, allows you to specify a list of possible values.
   - `SET`: Set of values, similar to ENUM but can hold multiple values.

These are the basic data types provided by MySQL. Depending on the version and specific use case, there might be additional or specialized data types available.



## Table Operations -

1. Creating Table -

To create a table in MySQL, you can use the `CREATE TABLE` statement followed by the table name and the column definitions. Here's the basic syntax:

```sql
CREATE TABLE table_name (
    column1 datatype constraints,
    column2 datatype constraints,
    ...
    columnN datatype constraints
);
```

Let's break it down:

- `table_name`: The name you want to give to your table.
- `column1`, `column2`, ..., `columnN`: The names of the columns in your table.
- `datatype`: The data type for each column.
- `constraints`: Optional constraints such as `PRIMARY KEY`, `NOT NULL`, `AUTO_INCREMENT`, etc.

Here's an example of creating a simple table named `users` with `id`, `username`, and `email` columns:

```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL
);
```

This SQL statement creates a table named `users` with three columns: `id`, `username`, and `email`. The `id` column is set as the primary key and will auto-increment for each new record. Both `username` and `email` columns are defined as `VARCHAR` data type with specific length limits and are marked as `NOT NULL`, meaning they must have a value.

You can add more columns and define additional constraints as needed based on your specific requirements.

2. Show Table and Drop Table

To view the structure of a table in MySQL, you can use the `DESCRIBE` statement followed by the table name. Alternatively, you can use the `SHOW COLUMNS` statement. Here's how you can do it:

```sql
DESCRIBE table_name;
```

or

```sql
SHOW COLUMNS FROM table_name;
```

Replace `table_name` with the name of the table you want to show. For example:

```sql
DESCRIBE users;
```

This will display the structure of the `users` table, including the column names, data types, and any constraints.

To drop (delete) a table in MySQL, you can use the `DROP TABLE` statement followed by the table name. Here's the syntax:

```sql
DROP TABLE table_name;
```

Replace `table_name` with the name of the table you want to drop. For example:

```sql
DROP TABLE users;
```

This command will permanently delete the `users` table and all its data. Make sure you have the necessary permissions and are absolutely certain you want to delete the table before executing this command.




