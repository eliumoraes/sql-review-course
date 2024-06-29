
# I.c.4 Best Practices and Precautions When Handling Data
Okay, I've got the power to add, modify, and delete data... pretty cool! But with great power comes great responsibility, right? So let's talk about some best practices and precautions to keep my data safe and sound.

### The Importance of Backups
It's a good habit to regularly back up my database. This way, if something goes wrong (like accidentally deleting a bunch of rows - yikes!), I can always restore my data from the backup.

**Interview-Ready Explanation:**
Regular backups are essential to protect against data loss due to accidental deletions, hardware failures, or other unforeseen events.

### Transactions: My Safety Net
Transactions are like a safety net for my data changes. They group a set of SQL statements together and ensure that either all of them succeed or none of them do. This helps me maintain the consistency of my data.
- `BEGIN;`: Starts a new transaction.
- `COMMIT;`: Makes all the changes in the transaction permanent.
- `ROLLBACK;`: Undoes all the changes made since the last `BEGIN` or `COMMIT`.

**Example:**
```
BEGIN;
UPDATE employees
SET salary = salary * 1.1 -- Give everyone a 10% raise
WHERE department = 'Sales';
-- If everything looks good, commit:
COMMIT;
-- If something goes wrong, rollback:
ROLLBACK;
```
**Interview-Ready Explanation:**
Transactions ensure data integrity by grouping multiple SQL statements into a single unit of work. If any statement fails, the entire transaction can be rolled back.

### Using `WHERE` Wisely
I need to be extra careful when using `UPDATE` or `DELETE` statements without a `WHERE` clause. If I forget the `WHERE`, I could accidentally modify or delete all the rows in my table.

**Tip:** Double-check your `WHERE` conditions, and always test with a `SELECT` statement first to make sure I'm targeting the right rows.

### Assertions Withing Transactions
Within a transaction, you can use the `SELECT` statement combined with assertions to ensure your data modifications have the desired effect before you commit. If an assertion fails, you can `ROLLBACK` the transaction to revert the changes.

**Example:** Update Salaries and Assert Changes
```
BEGIN; -- Start the transaction

-- Give a 10% raise to all employees in the sales department
UPDATE employees
SET salary = salary * 1.1
WHERE deparment = 'Sales';

-- Assert that no one's salary is now less than $30,000
ASSERT (
	SELECT COUNT (*)
	FROM employees
	WHERE department = 'Sales' AND salary < 30000
) = 0;

-- If the assertion passes, commit the changes
COMMIT;
```
In this example:
1. We begin the transaction.
2. We update the salaries of employees in the Sales department.
3. The `ASSERT` statement checks if any employees in the Sales department now have a salary below $30,000.
4. If the assertion fails (meaning there are employees with salaries below $30,000), it raises an exception, and the transaction is automatically rolled back.
5. If the assertion passes, we commit the transaction, making the salary updates permanent.

**Other Assertion Tricks**
- **Count Rows Affected:** After an `UPDATE` or `DELETE`, you can check the number of rows affected using `GET DIAGNOSTICS`. This helps you verify if the correct number of rows were modified.
- **Aggregate Checks:** You can use aggregate functions like `SUM`, `AVG`, `MIN`, or `MAX` to check if the overall results of your update meet certain criteria.
- **Custom Functions:** If you have complex validation logic, you can create custom functions within PostgreSQL to perform checks and return a boolean value (true/false) for your assertion.

**Interview-Ready Explanation**
Before committing a transaction, it's crucial to verify that the data modifications had the intended effect. This can be done using `SELECT` statements in combination with `ASSERT` or other validation techniques to check if the data meets specific criteria. If any checks fail, you can rollback the transaction to avoid corruption your data.

**Note:** In this case of the assertion is TRUE, the transaction proceeds, but if it is FALSE, PostgreSQL raises an error and automatically triggers a ROLLBACK.

### Why Explicitly Declare a`ROLLBACK`?
The explicit declaration of a `ROLLBACK` statement is typically used when you want more granular control over the transaction flow. This can be useful when you're not relying on an `ASSERT` statement to trigger an automatic rollback, or when you want to rollback the transaction under specific conditions or errors. You can achieve this using an `EXCEPTION` block or an `IF-ELSE` statement within your transaction.
