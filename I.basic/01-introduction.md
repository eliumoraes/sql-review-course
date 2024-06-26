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

Before we start querying and manipulating data, we need a playground - a database management system (DBMS) to practice with. Think of this as your sandbox where you can experiment with SQL commands and see the results in action.

We'll focus on two popular options for Ubuntu: PostgreSQL and MySQL. Choose one that aligns with your interests or the requirements of your future job.

## Installing PostgreSQL or MySQL

**PostgreSQL:**

sudo apt update
sudo apt install postgresql postgresql-contrib

**MySQL:**

sudo apt update
sudo apt install mysql-server

**Essential VSCode Extensions**
To enhance your SQL coding experience in VSCode, here are two essential extensions:

**SQLTools**: This extensions provides a comprehensive set of tools for working with SQL databases directly within VSCode. It offers features like:
- Intelligent code completion (IntelliSense)
- Syntax highlighting
- Query formatting
- Connection management (connect to your local or remote databases)
- Result visualization

**PostgreSQL or MySQL:** These extensions offer additional language support and functionalities specific to the respective DBMS. Choose the one that corresponds to your choose database.

> In my case PostgreSQL is the DBMS that will be used during all this
> review course, please take this in consideration in the case you are
> referencing this repository for your test preparation.

**Accessing PostgreSQL**
After installation, PostgreSQL automatically creates a default user named `postgres`. We'll use this user to initially access the database system. Since I'm using the terminal integrated to VSCode, I'll navigate directly to the PostgreSQL shell without changing directories:

    sudo -i -u postgres
    psql

**Result:**

    eliu@eliu-Latitude-3490:~/codedir/sql-review-course$ sudo -i -u postgres
    postgres@eliu-Latitude-3490:~$ psql
    psql (14.12 (Ubuntu 14.12-0ubuntu0.22.04.1))
    Type "help" for help.
    
    postgres=# 
- The first command switches to the postgres user without changing directories. You can try without the `-i` to check the permission issues we are avoiding.
- The second command then opens the PostgreSQL interactive terminal.

**Create a new user**
It's a good practice to create a new user for your day-to-day database operations.

    CREATE USER your_username WITH PASSWORD 'your_password';

**Result:**

    postgres=# CREATE USER admin WITH PASSWORD '123456';
    CREATE ROLE
    postgres=# 

**Create a new database**
To create a new database we can use the following command:

    CREATE DATABASE your_database_name;
**Tip**: The command will run only after you type the `;`. If you forgot it, add it in the next line and press enter.

**Result:**

    postgres=# CREATE DATABASE my_first_database
    postgres-# ;
    CREATE DATABASE
    postgres=# 

**Grant privileges to the new user**
The following command grants access to a user in a database:

    GRANT ALL PRIVILEGES ON DATABASE your_database_name TO your_username;

**Result:**

    postgres=# GRANT ALL PRIVILEGES ON DATABASE my_first_database TO admin;
    GRANT
    postgres=# 

**Connecting to PostgreSQL from VSCode**
Now that you have PostgreSQL installed and set up, you can connect to it from VSCode using the SQLTools extension. To ensure a seamless connection, we'll also install the necessary driver:

**Install the SQLTools PostgreSQL/Cockroach Driver:**
Open the Extensions Marketplace in VSCode (Ctrl+Shift+X).
Search for "SQLTools PostgreSQL/Cockroach Driver" and install the extension by Matheus Teixeira.

**Open the SQLTools extension:** Click on the elephant icon in the VSCode sidebar.
**Add a new connection:** Click on the "+" button and select "PostgreSQL." If you don't see "PostgreSQL" right away, wait a moment for the driver to finish loading.

**Fill in the connection details:**
**Driver:** Select "PostgreSQL Elephant" from the dropdown menu.
**Connection name:** Name the connection as you please
**Connect using:** Server and port
**Server:** localhost (or the address of your PostgreSQL server)
**Port:** 5432 (default)
**Database:** your_database_name (or the name of the database you want to connect to)
**User:** your_username
**Use password:** Save as plaintext in settings (not secure, use only for test purposes)
**Password:** your_password
*Check if the Test Connection button returns a successful message*
**Save the connection:** Click "Save Connection."

You should now see your database listed in the SQLTools sidebar. You can start writing SQL queries in a new file and execute them against your database.

4. Command-line tools and SQL clients (e.g., psql, mysql)
