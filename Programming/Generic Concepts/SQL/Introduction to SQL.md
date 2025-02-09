**SQL** or *Structured Query Language* provides a means for us to communicate with Databases.

Generally speaking, SQL databases are stored in conventional tables consisting of rows and columns. SQL databases, which are also often referred to as *relational* databases, have the ability to create relationships with other databases allowing for a separation of concerns while maintaining the ability to store large amounts of data per item in the database.

![](Pictures/Introduction%20to%20SQL%20-%20Relational%20Database.png)

**Note**: There are many SQL operations and not all of them will be covered in this document, for a comprehensive list simply navigate to W3 Schools [Page](https://www.w3schools.com/sql/) on SQL.
# CRUD

CRUD forms the basis of our SQL based applications, it outlines the 4 common operations that we expect to be able to complete in order to work with and store large datasets. They are:

- Create
- Read
- Update
- Destroy

Let's look at a handful of SQL operations in the aforementioned categories.
## Create

Let's *create* a new table using SQL syntax:

```sql nums
CREATE TABLE products (
  id INT NOT NULL,
  name STRING,
  price MONEY,
  PRIMARY KEY(id)
  )
```

Using this schema we create the following table with some test data added for clarity:

**Products**:

| id  | name  | price |
| --- | ----- | ----- |
| 1   | Ruler | 19.99 |

First we issue the `CREATE TABLE` command followed by the table name, all table fields will be entered within parenthesis. We then specify the name of the field followed by the datatype in capital letters. There are many datatypes that can be used in SQL to store data, more information on these data types can be found on the W3 Schools page linked earlier. Finally we specify that the 'id' field is to be the `PRIMARY KEY` for the database. The primary key is used as a means to uniquely identify each record in the database.

Now, let's *insert* a new value into our table:

```sql nums
INSERT INTO products
VALUES ('2', 'Pen', '1.99')
```

First we specify the table that we intend to `INSERT INTO` followed by the `VALUES` in parenthesis. Note these values must be enclosed in single quotes and separated by commas. Also note that this command is actually a single line command generally this kind of command will be written over multiple lines for readability.

This method for inserting data can be used when you intend to fill each field in the new entry with data. If only specific fields are to be filled then those columns will need to be specified as well.

```sql nums
INSERT INTO products (id,name) 
VALUES (
  '3',
  'Pencil'
);
```

| id  | name   | price  |
| --- | ------ | ------ |
| 1   | Ruler  | 19.99  |
| 2   | Pen    | 1.99   |
| 3   | Pencil | [Null] |
## Read

In order to *read* data from our database we will use the SQL `SELECT` keyword.

For instance, if we simply wish to view our table then we will issue the following query:

`SELECT * FROM products;`

| id  | name   | price  |
| --- | ------ | ------ |
| 1   | Ruler  | 19.99  |
| 2   | Pen    | 1.99   |
| 3   | Pencil | [Null] |
The asterisk, which is generally used to indicate multiplication, is also generally used to indicate 'all'. Therefore, in this context we wish to select *all* records from our products table.

Let's say we wanted to only see the name and price columns for the table:

`SELECT name, price FROM products;`

| name   | price  |
| ------ | ------ |
| Ruler  | 19.99  |
| Pen    | 1.99   |
| Pencil | [Null] |
Now, in the instance that you want to select a particular row from the table, you will need to issue a *search* query. We can issue such a query using the `WHERE` syntax. 

Let's query for the first item in our table.

`SELECT * FROM products WHERE id=1`
 
| id  | name   | price  |
| --- | ------ | ------ |
| 1   | Ruler  | 19.99  |
The `WHERE` keyword specifies a condition, in other words only rows will be displayed where the condition is true. Other operators can be used and those are mentioned in the W3 Schools page.
## Update

In order to *update* the data inside our table we will need to use the `UPDATE` keyword. 

Let's update a specific field inside of our table, we will need to specify the table name, the field we would like to update along with the new value, and we will need to select the specific element inside of our database via condition.

```sql nums
UPDATE products
SET price = 0.80
WHERE id=2
```

| id  | name   | price  |
| --- | ------ | ------ |
| 1   | Ruler  | 19.99  |
| 2   | Pen    | 0.80   |
| 3   | Pencil | [Null] |

In the event that you would like to update the table rather than a specific row inside the table, for example by adding a column to keep track of stock, then we need to `ALTER` the table.

The `ALTER` keyword allows us to add, delete, or modify columns in an existing table.

```sql nums
ALTER TABLE products
ADD stock INT
```

**Note**: It is important to include the datatype for the column along with any other rules that may be necessary. 

| id  | name   | price  | stock  |
| --- | ------ | ------ | ------ |
| 1   | Ruler  | 19.99  | [Null] |
| 2   | Pen    | 0.80   | [Null] |
| 3   | Pencil | [Null] | [Null] |
## Delete

The final operation we need to be able to query to complete our CRUD application is the *delete* operation.

Let's delete the pencil record:

```sql nums
DELETE FROM products
WHERE id = 3
```
 
| id  | name   | price  | stock  |
| --- | ------ | ------ | ------ |
| 1   | Ruler  | 19.99  | [Null] |
| 2   | Pen    | 0.80   | [Null] |

Just as when we selected a specific row from a table via condition, we will delete a specific row from the table via a condition. **Note**: It is very important that you carefully specify your condition because if you were to, for example, forget to specify the condition in this case then you will delete all records from the products table.
# Relationships

Relationships are what make SQL databases powerful, they provide us with the ability to create multiple tables for different things while maintaining relationships between those datasets.

Let's create a new table called `orders` 

```sql nums
CREATE TABLE orders (
  id INT NOT NULL,
  order_number INT,
  customer_id INT,
  product_id INT,
  PRIMARY KEY(id),
  FOREIGN KEY(customer_id) REFERENCES customers(id),
  FOREIGN KEY(product_id) REFERENCES products(id)
  )
```

Now, in addition to specifying a primary key we will also specify two *foreign* keys which *reference* other tables and you can also see that they reference a specific column of those tables.

This allows us to maintain relationships between these tables by enabling us to find the dataset from one table that is relevant to another by following the foreign key.

**Customers**

| id  | name |
| --- | ---- |
| 1   | Brad |
| 2   | Fred |

**Products**

| id  | name   | price | stock |
| --- | ------ | ----- | ----- |
| 1   | Ruler  | 19.99 | 3     |
| 2   | Pen    | 0.80  | 6     |
| 3   | Pencil | 2.99  | 9     |

**Orders**

| id  | order_number | customer_id | product_id |
| --- | ------------ | ----------- | ---------- |
| 1   | 83432        | 1           | 2          |
| 2   | 32480        | 2           | 3          |

Let's have a look at the **Orders** table. If we pay attention to the customer and product IDs we can see that the first row indicates an order by Brad for a Pen by looking for the corresponding IDs in the **Products** and **Customers** tables.
## Join

In order to make viewing relational data easier we can create or view a *new* table by selecting columns from two related tables and *joining* them together into a new table via the condition that there is data that is present that matches both tables.

```sql nums
SELECT orders.order_number, customers.name
FROM orders
INNER JOIN customers ON orders.customer_id = customers.id
```


| order_number | name |
| ------------ | ---- |
| 83432        | Brad |
| 32480        | Fred |

Now we have a new table showing the relational data between two tables joined together as new rows making it easy for as to match order numbers to the people who made the orders.

To break down the query, first we specify columns we would to be present in our new table, then we specify a starting table for our `JOIN` operation and finally we specify the table to be joined by specifying a join method, the name of the table and finally the condition for joining.