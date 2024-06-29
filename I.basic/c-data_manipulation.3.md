
# I.c.3 Deleting Rows (DELETE)
Alright, I've covered adding and modifying data. Now, what if I need to remove some rows completely? That's where the `DELETE` statement comes in. It's like hitting the "delete" key on a rows in my spreadsheet, but with more control.

### Basic Syntax
```
DELETE FROM table_name
WHERE condition;
```
- DELETE FROM: This tells PostgreSQL that I'm removing rows.
- `table_name`: The name of the table I want to delete from.
- `WHERE`: (Usually required) The condition to specify which rows to delete.

### Example
Let's say Emily Chen left the company, so I need to remove her record from `employees` table:
```
DELETE FROM employees
WHERE employee_id = 2; -- Assuming Emily Chen's ID is 2
```

**Interview-Ready Explanation:**
The `DELETE` statement removes rows from a table based on a specified condition. It's crucial to use the `WHERE` clause carefully to avoid accidentally deleting data you need.

**Warning!**
- Be **extremely** cautious when using `DELETE` without a `WHERE` clause. It will delete all rows from the table! Always double-check your `WHERE` condition before executing.

**Tip:** Before executing a `DELETE` statement you can test your `WHERE` condition with a `SELECT` statement first to ensure you're targeting the correct rows:
```
SELECT * -- Or just the columns you care about
FROM employees
WHERE employee_id = 2;
```
If the `SELECT` query returns the data you intend to delete, then you can replace `SELECT *` with `DELETE` and safely execute the statement.
