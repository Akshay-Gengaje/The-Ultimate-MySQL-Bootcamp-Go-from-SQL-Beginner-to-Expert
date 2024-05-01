# Update Operations -

The Update operation in MySQL, accomplished with the `UPDATE` statement, allows you to modify existing data within your tables. Here's a breakdown of its capabilities and various query options:

**Basic Update:**

- Updates a single column with a new value for all rows:

```sql
UPDATE customers SET email = 'new_email@example.com';
```

This query updates the `email` column to "new_email@example.com" for all customers in the `customers` table.

**Updating Specific Columns:**

- Modifies multiple columns simultaneously:

```sql
UPDATE customers SET name = 'John Doe', city = 'New York' WHERE id = 1;
```

This query updates both the `name` and `city` columns for the customer with the ID of 1.

**Conditional Updates with WHERE Clause:**

- Targets specific rows for updates based on conditions:

```sql
UPDATE customers SET discount = 10 WHERE total_purchases > 100;
```

This query applies a 10% discount (setting `discount` to 10) to customers who have made purchases exceeding $100 (based on a `total_purchases` column).

**Incrementing/Decrementing Values:**

- Modifies values by a certain amount using mathematical operators:

```sql
UPDATE products SET stock = stock - 5 WHERE product_id = 2;  -- Decrements stock by 5
UPDATE user_points SET points = points + 20 WHERE user_id = 3;  -- Increases points by 20
```

These examples demonstrate decreasing stock by 5 for a product (assuming a `stock` column) and increasing points by 20 for a user (assuming a `points` column).

**Updating with Expressions:**

- Perform calculations within the `SET` clause for dynamic updates:

```sql
UPDATE orders SET total_amount = price * quantity WHERE id = 10;
```

This query calculates the total amount (assuming a `price` and `quantity` column) and updates it for the order with ID 10.

**Limiting Updates:**

- Restricts the number of rows affected using `LIMIT`:

```sql
UPDATE products SET price = price * 1.1 LIMIT 10;  -- Increases price by 10% for the first 10 products
```

This query applies a 10% price increase (multiplying by 1.1) to only the first 10 products in the table.

**Combining Clauses:**

- Combine `WHERE` and `LIMIT` for targeted updates:

```sql
UPDATE customers SET active = 0 WHERE last_login < DATE_SUB(CURDATE(), INTERVAL 30 DAY) LIMIT 50;
```

This query deactivates (setting `active` to 0) accounts that haven't logged in within the last 30 days (using `DATE_SUB` for date subtraction), affecting a maximum of 50 users.

**Updating from Subqueries:**

- Utilize subqueries within `UPDATE` for complex data manipulation:

```sql
UPDATE orders o
SET discount_applied = (
  SELECT discount FROM promotions WHERE product_id = o.product_id
)
WHERE order_date > '2024-04-01';
```

This query applies a discount from the `promotions` table (assuming a `discount` column) to orders placed after April 1, 2024, using a subquery to retrieve the discount value based on the product in the order.

Remember, these examples provide a foundation for the UPDATE operation in MySQL. Explore the MySQL documentation for more advanced functionalities like updating multiple tables at once or using triggers for automated updates based on specific events.
