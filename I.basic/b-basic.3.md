# I.b.3. Other Operators and Filtering Techniques
The `WHERE` clause is incredibly flexible, allowing you to use various operators and techniques to filter your data precisely. Let's explore some additional options beyond the basic comparison and logical operators.

### `BETWEEN` Operator
The `BETWEEN` operator simplifies range checks. It allows you to select values within a specified range.
```
SELECT product_name, price
FROM products
WHERE price BETWEEN 50 and 100;
```
This is equivalent to
```
SELECT product_name, price
FROM products
WHERE price >= 50 AND price <= 100;
```
Both queries retrieve products with prices between 50 and 100, inclusive.

**Interview-Ready Explanation:**
The `BETWEEN` operator provides a concise way to filter values within a specified range, including the endpoints.

### `IN` Operator
The `IN` operator is handy when you want to check if a value matches any item in a list.
```
SELECT first_name, last_name
FROM employees
WHERE department IN ('Sales', 'Marketing');
```
This query retrieves employees who work in either the "Sales" or "Marketing" departments.

**Interview-Ready Explanation:**
The `IN` operator checks if a value exists within a specified list of values.

### `LIKE` Operator (Pattern Matching)
The `LIKE` operator allows you to match patterns in text data using wildcards:
- `%`: Matches zero or more characters.
- `_`: Matches exactly one character.
```
SELECT first_name, last_name
FROM employees
WHERE last_name LIKE 'Sm%';
```
This query finds employees whose last name starts with "Sm" (e.g., Smith, Smirnov).

**Interview-Ready Explanation:**
The `LIKE` operator performs pattern matching on text data using wildcards. `%` matches any number of characters, and `_` matches a single character.

### `IS NULL` and `IS NOT NULL`
These operators check for missing (NULL) values:
```
SELECT first_name, last_name
FROM employees
WHERE email IS NULL;
```
This query retrieves employees who haven't provided an email address.

**Interview-Ready Explanation:**
`IS NULL` and `IS NOT NULL` are used to filter rows based on the presence or absence of values in a column

