# SQL Exercises

## Topics

- Structured Query Language (SQL)
- Relational Databases
- SQLite
- Writing Basic Queries

## Assignments

### Create a Database Table

- use DB Browser for SQLite to create a database, name it anything you want.
- add an _accounts_ table with the following _schema_:

  - `id`, numeric value with no decimal places that should autoincrement.
  - `name`, string, add whatever is necessary to make searching by name faster.
  - `budget` numeric value.

- constraints
  - the `id` should be the primary key for the table.
  - account `name` should be unique.
  - account `name`, required.

### Write Basic Queries

- Visit [SQL Try Editor at W3Schools.com](https://www.w3schools.com/Sql/tryit.asp?filename=trysql_select_top) and write the following queries:

  <!-- - find all customers with a particular first name. -->

  SELECT * FROM customers WHERE contactname like '%john%'

  <!-- - find all customers that live in London. -->

  SELECT * FROM customers WHERE city like '%london%'

  <!-- - find the phone number for a particular supplier (provide id, or supplier name). -->

  SELECT phone FROM [Suppliers] WHERE supplierid = 1

  <!-- - find all customers in a particular postal code. -->

  SELECT * FROM [Customers] WHERE	postalcode = '05033'

  <!-- - find all suppliers who have names with more than 20 characters. -->

  SELECT * FROM [Suppliers] WHERE LENGTH(suppliername) >= 20

  <!-- - list customers descending by the number of orders. -->

  SELECT customers.customername, COUNT(Orders.OrderID) AS NumberOfOrders FROM Orders
  LEFT JOIN customers ON customers.customerID = orders.customerID
  GROUP BY customername
  ORDER BY numberoforders DESC
  

  <!-- - list orders descending by the order date. -->

  SELECT * FROM [Orders]
  ORDER BY orderdate desc

  <!-- - list orders grouped by customer showing the number of orders per customer. -->


  <!-- - list orders grouped by customer's city showing number of orders per city. -->

  SELECT customers.city, COUNT(Orders.OrderID) AS NumberOfOrders FROM Orders
  LEFT JOIN customers ON customers.customerID = orders.customerID
  GROUP BY customers.city
  ORDER BY numberoforders DESC  

  <!-- - add a customer using your information. -->

  INSERT INTO customers (customername, contactname, address, city, postalcode, country)
  VALUES ('skydive city', 'jj ashcraft', '4241 skydive lane', 'zephyrhills', '33542', 'USA')

  <!-- - add 2 products. -->

  INSERT INTO Products (productname, supplierid, categoryid, unit, price)
  VALUES ('coffee', '1', '2', '1 ton', '20')

  INSERT INTO Products (productname, supplierid, categoryid, unit, price)
  VALUES ('jet pack', '5', '6', '5 boxes', '10000')


  <!-- - add 2 orders with you as the customer. -->

  INSERT INTO orders (customerid, employeeid, orderdate, shipperid)
  VALUES ('92', '5', '2018-07-30', '3')

  INSERT INTO orders (customerid, employeeid, orderdate, shipperid)
  VALUES ('92', '6', '2018-07-30', '2')

  <!-- - delete all users that have no orders. -->

  DELETE from customers
  where customerid not in (select customerid from orders)
  


Clicking the `Restore Database` in that page will repopulate the database with the original data and discard all changes you have made.
