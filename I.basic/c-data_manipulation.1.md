# I.c Data Manipulation (INSERT, UPDATE, DELETE)
Now that I can query my data, I need to know how to change it. This is where data manipulation commands come in. They let me add, modify, and remove data from my tables.

## 1. Inserting New Rows into Tables (`INSERT`)
The `INSERT` statement is my tool for adding new rows (records) to a table. It's like adding a new entry to a spreadsheet.

**Basic Syntax:**
```
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```
- `INSERT INTO`: This tells PostgreSQL which table I want to add data to.
- `table_name`: The name of the table.
- `(column1, column2, ...)`: The list of columns I'm providing values for.
- `VALUES`: This keyword introduces the values for the new row.
- `(value1, value2, ...)`: The list of values, in the same order as the columns listed.

**Example:**
To add a new employee named David Lee to the `employees` table:
```
INSERT INTO employees (first_name, last_name, department)
VALUES ('David', 'Lee', 'HR');
```
**Interview-Ready Explanation:**
The `INSERT INTO` statement adds a new row to a table, specifying the values for the columns you want to insert.
**Remember:** The order of values must match the order of columns in the `INSERT` statement.

