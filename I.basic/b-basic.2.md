# I.b.2. Filtering Data with WHERE clauses
The`WHERE` clause is your tool for precision. It lets you filter the results of your `SELECT` queries, returning only the rows that match specific conditions. Think of it as adding a "but only if..." to your question.

### The basics of WHERE
The structure of a `WHERE` clause is simple:
```
SELECT column1, column 2, ...
FROM table name
WHERE condition;
```
- `WHERE`: This keyword signals the start of your filtering conditions.
- `condition`: This is an expression that evaluates to either `true` or `false`. Rows where the condition is `true` are included in the results, while those where it's `false` are excluded.

### Comparison Operators
You'll often use comparison operators in your `WHERE` conditions:
- `=`: Equal to
- `!=` or `<>`: Not equal to
- `>`: Grater than
- `<`: Less than
- `>=`: Greater than or equal to
- `<=`: Less than or equal to

### Logical Operators
Combine multiple conditions using logical operators:
- `AND`: Both conditions must be true.
- `OR`: At least one condition must be true.
- `NOT`: Reverses the truth value of a condition.

### Example
Let's revisit our `employees` table. Suppose I want to find employees in the "Sales" department:
```
SELECT first_name, last_name
FROM employees
WHERE department = 'Sales';
```
This query will only returns rows where the `department` column has the value 'Sales'.

**Note:** The value is case-sensitive. If some rows contains this department in a different case, it is important to change the case before querying for it. I'll touch this topic later when we cover string functions in PostgreSQL. For now, you could use the `UPPER` function to covert the values to uppercase before comparing:
```
SELECT first_name, last_name
FROM employees
WHERE UPPER(department) = 'SALES';
```
This will ensure that even if the department is store as 'Sales', 'sales' or 'SALES' in the database, they will all match the condition and be included in the result.

### Interview-Ready Explanation
The `WHERE` clause is used to filter the results of a `SELECT` query based on specified conditions. You can use comparison operators like `=` and `!=`, logical operators like `AND` and `OR`, and combine them to create complex filters.

## Questions
1. How does the `WHERE` clause modify the results of a `SELECT` query?
2. Explain the difference between the `AND` and `OR` operators in a `WHERE` clause.
3. Give an example of a query that retrieves products with a price greater than $50 and less than $100.
```
SELECT product_name, price
FROM products
WHERE (price > 50) AND (price < 100);
```
**Note:** The parentheses around the individual conditions are not strictly necessary in this case, but they improve readability and make the logic more explicit.

