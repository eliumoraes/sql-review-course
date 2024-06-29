
# I.c.2 Updating Existing Values (UPDATE)
Okay, I've got the hang of adding new data. Now, what if I need to make changes to existing records? That's where the `UPDATE` statement comes in handy. It's like using the "Find and Replace" feature in a text editor, but for my database tables.

### Basic Syntax
```
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```
- `UPDATE`: This keyword tells PostgreSQL that I want to modify existing data.
- `table_name`: The name of the table I want to update.
- `SET`: This keyword introduces the changes I want to make.
- `column1 = value1`, `column2 = value2`, ...: A list of column-value pairs, specifying the new values for the columns I'm updating.
- `WHERE`: This optional clause lets me filter which rows to update. If I omit it, all rows in the table will be updated.

### Example
Let's say David Lee got promoted from HR to Senior HR Manager. I need to update his department and job title in the `employees` table:
```
UPDATE employees
SET department = 'Senior Management', job_title = 'Senior HR Manager'
WHERE employee_id = 1; -- Assuming David Lee's ID is 1
```

**Interview-Ready Explanation:**
The `UPDATE` statement modifies existing data in a table. It specifies the columns to update, the new values, and optionally a `WHERE` clause to filter which rows are affected.

**Important Note:** Be extremely careful when using `UPDATE` without a `WHERE` clause. You could unintentionally modify all the rows in your table!

**Additional Note:** It's possible to add comments to a SQL code. Comments need to start with two dashes (`--`), and everything that comes after it won't be executed.
