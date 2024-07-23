Aggregation in MySQL refers to the process of performing a calculation on a set of values to return a single value. Aggregation functions are commonly used in conjunction with the `GROUP BY` clause to group rows that share a property so that an aggregate value can be calculated.

### Common Aggregation Functions

1. **`COUNT()`**: Counts the number of rows.
2. **`SUM()`**: Calculates the sum of a set of values.
3. **`AVG()`**: Calculates the average of a set of values.
4. **`MAX()`**: Returns the maximum value in a set.
5. **`MIN()`**: Returns the minimum value in a set.

### Example Table: `sales`

Suppose you have a table `sales` with the following data:

| sale_id | product_id | quantity | price | sale_date  |
| ------- | ---------- | -------- | ----- | ---------- |
| 1       | 101        | 2        | 100   | 2024-08-01 |
| 2       | 102        | 1        | 200   | 2024-08-01 |
| 3       | 101        | 3        | 100   | 2024-08-02 |
| 4       | 103        | 5        | 150   | 2024-08-03 |
| 5       | 102        | 2        | 200   | 2024-08-04 |

### Examples of Aggregation

#### Example 1: `COUNT()`

Count the total number of sales:

```sql
SELECT COUNT(*) AS total_sales
FROM sales;
```

**Result:**

| total_sales |
| ----------- |
| 5           |

#### Example 2: `SUM()`

Calculate the total revenue from all sales:

```sql
SELECT SUM(quantity * price) AS total_revenue
FROM sales;
```

**Result:**

| total_revenue |
| ------------- |
| 1900          |

#### Example 3: `AVG()`

Calculate the average price of all products sold:

```sql
SELECT AVG(price) AS average_price
FROM sales;
```

**Result:**

| average_price |
| ------------- |
| 150           |

#### Example 4: `MAX()` and `MIN()`

Find the highest and lowest sale amounts:

```sql
SELECT MAX(quantity * price) AS highest_sale, MIN(quantity * price) AS lowest_sale
FROM sales;
```

**Result:**

| highest_sale | lowest_sale |
| ------------ | ----------- |
| 750          | 100         |

#### Example 5: Aggregation with `GROUP BY`

To find the total revenue per product:

```sql
SELECT product_id, SUM(quantity * price) AS total_revenue
FROM sales
GROUP BY product_id;
```

**Result:**

| product_id | total_revenue |
| ---------- | ------------- |
| 101        | 500           |
| 102        | 600           |
| 103        | 750           |

#### Example 6: Filtering Groups with `HAVING`

To find products with total revenue greater than 500:

```sql
SELECT product_id, SUM(quantity * price) AS total_revenue
FROM sales
GROUP BY product_id
HAVING total_revenue > 500;
```

**Result:**

| product_id | total_revenue |
| ---------- | ------------- |
| 102        | 600           |
| 103        | 750           |

### Summary

- Aggregation in MySQL involves performing calculations across multiple rows and returning a single result.
- Common aggregation functions include `COUNT()`, `SUM()`, `AVG()`, `MAX()`, and `MIN()`.
- The `GROUP BY` clause is used to group rows before applying an aggregation function.
- The `HAVING` clause is used to filter groups after aggregation.
