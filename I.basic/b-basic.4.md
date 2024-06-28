# I. b. 4. Sorting and Limiting Results (ORDER BY, LIMIT, OFFSET)
Alright, so I can filter the data I want to see. But what if I want to arrange it in a specific order or just see a few results at a time? That's where `ORDER BY` and `LIMIT` come in.

### `ORDER BY`: Sorting My Results
The `ORDER BY` clause lets me sort my results based on one or more columns. It's like rearranging the rows of my results table.

**Basic Syntax**:
```
SELECT column1, column2, ...
FROM table_name
WHERE condition
ORDER BY column1 ASC/DESC, column2 ASC/DESC, ...;
```
- `ORDER BY`: This keyword indicates that I want to sort the results.
- `column1`, `column2`, ...: The names of the columns I want to use for sorting.
- `ASC` (Ascending): Sorts the results in ascending order (lowest to highest, A to Z).
- `DESC` (Descending): Sorts the results in descending order (highest to lowest, Z to A).

**Example:**
If I want to see employees ordered by their last name alphabetically:
```
SELECT first_name, last_name
FROM employees
ORDER BY last_name ASC;
```

**Interview-Ready Explanation:**
The `ORDER BY` clause sorts the results of a query based on one or more columns, either in ascending (`ASC`) or descending (`DESC`) order.

### `LIMIT` and `OFFSET`: Just a Taste of the Data
These clauses help me control how many rows I get back.

**Basic Syntax:**
```
SELECT column1, column2, ...
FROM table_name
LIMIT number_of_rows OFFSET starting_row;
```

**Example:**
If I only want to see the top 3 highest-paid employees:
```
SELECT first_name, last_name, salary
FROM employees
ORDER BY salary DESC
LIMIT 3;
```

**Interview-Ready Explanation:**
 `LIMIT` restricts the number of rows returned by a query. `OFFSET`lets you skip a certain number of rows before starting the result set. They're useful for pagination or when you only need a subset of the data.

