# b. Basic Queries (SELECT, FROM, WHERE)

Now that I've got PostgreSQL set up and know how to access it, let's dive into the heart of SQL: querying data. This is where the magic happens - extracting the information I need from my database.

## 1. Basic SELECT Syntax
The `SELECT` statement is the workhorse of SQL queries. It's like asking a question of my database and getting back the answers in a neat table.

**The basic structure looks like this:**
```
SELECT column1, column2, ...
FROM table_name;
```
- `SELECT`: This keyword tells PostgreSQL what columns (or data points) I want to retrieve.
- `column1`, `column2`, ...: These are the names of the specific columns I'm interested in.
- `FROM`: This keyword tells PostgreSQL where to look for the data - the table where those columns reside.

**Interview-Ready Explanation:**
The `SELECT` statement is the primary way to retrieve data from a database. It specifies the columns you want to see and the table where they're located.

**Example**
Let's say I have a table called `employees` with columns `employee_id`, `first_name`, `last_name`, and `department`. Here's how I'd retrieve the first and last names of all employees:
```
SELECT first_name, last_name
FROM employees;
```
This will give me a table showing only the `first_name` and `last_name` columns for every row (employee) in the `employees` table.

**Note:** In SQL, commands are not case-sensitive, but it's a good practice to capitalize keywords like `SELECT` and `FROM` for readability.

## Questions
1. Explain the core components of a `SELECT` statement in SQL.
- `SELECT`: Specifies the columns to retrieve.
- `FROM`: Indicates the table from which to fetch the data.
- (Optional) `WHERE`: Filters the results based on specific conditions.

2. What happens if you omit the `FROM` clause in a `SELECT` statement?
- The `FROM` clause is essential for specifying the source table of your data. Omitting it would result in a syntax error, as the query wouldn't know where to look for the columns you're trying to select.

3. Can you provide an example of a `SELECT` statement that retrieves specific columns from a table named "products"?
Assuming the "products" table has columns `product_id`, `name`, and `price`, a `SELECT` statement to retrieve the `name` and `price` of all products would be:
```
SELECT name, price
FROM products;
```
