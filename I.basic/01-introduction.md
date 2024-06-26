# a. Introduction to SQL and Relational Databases:

 1. What is SQL and its uses 

SQL is a powerful language for communicating with databases. It lets you find specific information (query), add new data (insert), change existing data (update), remove data (delete), define the structure of the database (create, alter, drop), and manage who can access what (grant, revoke).  

SQL is used everywhere, from building apps, to analyzing data, running servers, and making business decisions.  

2. Relational model and key concepts (tables, columns, rows)

The relational model is the foundation upon which SQL databases are built. It provides a structured way to organize data into tables, which consist of columns (attributes) and rows (records).

**Tables** are containers for the data. Each table represents a specific entity or concept, like "customers", "products", or "orders".  

**Columns** define the characteristics or attributes of the data within a table. For example, a "customers" table might have columns like "customer_id", "name", "email", and "address".  

**Rows** are records that represents a single instance of the entity. In the "customers" table, a row would contain the information for one specific customer.  

## Key Concepts of the Relational Model: 

- Primary Key: A column (or set of columns) that uniquely identifies each row in a table. For example, the "customer_id" column would likely be the primary key in the "customers" table.

- Foreign Key: A column in one table that references the primary key of another table, creating a relationship between the two tables. This allows you to link related data across different tables.

- Referential Integrity: A set of rules that ensure the consistency and validity of relationships between tables. For example, referential integrity would prevent you from deleting a customer who still has open orders in the "orders" table. 

## Analogy

Imagine a spreadsheet where each sheet is a table, each column header is a column, and each row of data is a row. The primary key would be like the unique ID number assigned to each row, and foreign keys would be like hyperlinks connecting related information on different sheets.

Example

Table: `customers`

customer_id | name   | email               | address
------------|--------|--------------------|--------------------
1           | Alice  | alice@example.com  | 123 Main St
2           | Bob    | bob@example.com    | 456 Elm St
3           | Carol  | carol@example.com  | 789 Oak St

In this example, `customer_id` is the primary key. If we had another table called `orders` , it might have a foreign key column called `customer_id` that would link each order to the corresponding customer in the `customers` table.

3. Installing and configuring a DBMS (e.g., PostgreSQL, MySQL) on Ubuntu   

4. Command-line tools and SQL clients (e.g., psql, mysql)
