# I.d.2 Grouping Data by Columns (`GROUP BY`) and filtering groups (`HAVING`)
Okay, aggregate functions are cool for summarizing my entire table, but what if I want to break it down further? That's where `GROUP BY` comes in. It lets me group rows based on shared values in one or more columns and then apply aggregate functions to each group separately.

## `GROUP BY` Basic Syntax
```
SELECT column1, aggregate_function(column2)
FROM table _name
GROUP BY column1;
```
- `GROUP BY column1`: This tells PostgreSQL to group the rows based on unique values in `column1`.
- `aggregate_function(column2)`: This applies the aggregate function (e.g., `SUM`, `AVG`) to the values in `column2` for each group defined by `column1`.

### Example
Let's see how many orders each customer has placed and their total spending:
```
SELECT customer_id,
    COUNT(*) AS total_orders,
    SUM(total_amount) AS total_spent
FROM orders
GROUP BY customer_id;
```

#### Interview-Ready Explanation:
`GROUP BY` allows you to group rows based on a column's unique values. Then, aggregate functions can be applied to each group to get summarized results for each distinct value.

## Having Clause (Filtering Groups)
Now, what if I want to filter thr groups themselves? That's where `HAVING` comes in. It's like a `WHERE` clause but for groups, not individual rows.
```
SELECT column1, column2, aggregate_function(coclumn2)
FROM table_name
GROUP BY column1
HAVING condition;
```

### Example
Let's find customers who have placed more than one orders:
```
SELECT customer_id, COUNT(*) AS total_orders
FROM orders
GROUP BY customer_id
HAVING COUNT(*) > 1;
```
Here, there result returned 0 rows. That means we do not have any costumer that placed more than one order. If you want to see a different result, add more orders and run the query again.

#### Interview-Ready Explanation:
`HAVING` is used to filter the results of a `GROUP BY` clause based on aggregate function values.

#### Challenges:
1. What is the difference between `WHERE` and `HAVING`?
2. Can you give me an example of how to use `GROUP BY` and `HAVING` together to find the departments with an average salary greater than $50,000?
