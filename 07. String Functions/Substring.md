The SUBSTRING function in MySQL is used to extract a specific portion of characters from a given string. It's a handy tool for manipulating text data within your queries.

Here's how it works:

**Syntax:**

```sql
SUBSTRING(str, pos [, length])
```

- **str** (required): This is the string from which you want to extract the substring.
- **pos** (required): This is the starting position of the substring within the original string. Positive values start from the beginning, while negative values start from the end (counting backwards). If `pos` is 0 or negative and exceeds the string length, the function returns NULL.
- **length** (optional): This is the number of characters you want to extract from the starting position (`pos`). If omitted, the function extracts all characters from the starting position (`pos`) to the end of the string. A value of 0 for `length` returns an empty string.

**Examples:**

1. Extracting characters from a specific position:

```sql
SELECT SUBSTRING("This is a string", 8, 5) AS extracted_text;
```

This query extracts 5 characters starting from the 8th position (inclusive) of the string "This is a string". The result will be "is a s".

2. Extracting everything from a specific position to the end:

```sql
SELECT SUBSTRING("Hello, world!", 7) AS extracted_text;
```

Here, we omit the `length` argument. The function will extract all characters from the 7th position (inclusive) onwards, resulting in "world!".

3. Extracting characters from the end of the string:

```sql
SELECT SUBSTRING("Welcome back", -3) AS extracted_text;
```

By using a negative value for `pos` (-3), we instruct the function to start from the 3rd character from the end (inclusive). This returns "back".

**Additional Points:**

- If `pos` is greater than the length of the string, the function returns an empty string.
- The SUBSTRING function is case-sensitive.

By incorporating the SUBSTRING function into your MySQL queries, you can effectively manipulate text data to retrieve specific portions of strings based on your requirements.