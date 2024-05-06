# **UPPER Function in MySQL**

The UPPER function is a built-in string function in MySQL that transforms all lowercase alphabetical characters (a-z) within a string to their uppercase counterparts (A-Z). It leaves uppercase letters, numbers, and special characters unchanged.

**Syntax:**

```sql
UPPER(string)
```

- `string`: This represents the string expression you want to convert to uppercase.

**Return Value:**

UPPER returns a new string with the characters in the input string converted to uppercase, following the rules mentioned above.

**Examples:**

1. Converting a simple string to uppercase:

   ```sql
   SELECT UPPER('hello world');
   ```

   This query will return:

   ```
   HELLO WORLD
   ```

2. Making all column values uppercase in a table:

   Let's assume you have a table named `customers` with a column named `name`. You can use UPPER to create a new column with uppercase names:

   ```sql
   SELECT name, UPPER(name) AS uppercase_name
   FROM customers;
   ```

   This query will select both the original names and their uppercase versions, aliased as `uppercase_name`.

3. Using UPPER with WHERE clause for case-insensitive comparisons:

   ```sql
   SELECT *
   FROM products
   WHERE UPPER(product_name) LIKE '%SHIRT%';
   ```

   In this query, UPPER is applied to both the `product_name` column and the search term "SHIRT" in the `WHERE` clause. This enables case-insensitive searching, meaning products containing "shirt," "Shirt," or "SHIRT" will be matched.

**Important Notes:**

- UPPER only affects lowercase alphabetical characters (a-z). Uppercase letters (A-Z), numbers (0-9), and special characters remain unchanged.
- UPPER returns the original string if it doesn't contain any lowercase alphabetical characters.
- UPPER operates on the string itself and doesn't modify the original data in the database.

**When to Use UPPER:**

- **Case-insensitive comparisons:** UPPER can be helpful for performing case-insensitive searches or comparisons in your queries.
- **Data normalization:** If you want to ensure consistent capitalization across your string data, using UPPER during data entry or retrieval can be a strategy.
- **Displaying data in a specific format:** UPPER can be used to control how text is displayed in your application's user interface if uppercase presentation is desired.

By understanding the UPPER function and its applications, you can effectively manipulate case sensitivity in your MySQL queries, leading to more versatile and robust database operations.