# I.d.2 Grouping Data by Columns (`GROUP BY`)
Okay, aggregate functions are cool for summarizing my entire table, but what if I want to break it down further? That's where `GROUP BY` comes in. It lets me group rows based on shared values in one or more columns and then apply aggregate functions to each group separately.

## Basic Syntax
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