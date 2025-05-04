# Join Table

This is example about Join, Join Multi, Left Join, Right Join, Full Join, Cross Join Table.

## Example

##### Inner Join

```
SELECT firstname,lastname,orderdate
FROM orders
JOIN employees ON employees.employeeid=orders.employeeid;
```
* [Reference](https://www.postgresqltutorial.com/postgresql-inner-join/)

##### Inner Join Multi Tables

```
SELECT companyname, productname, orderdate, order_details.unitprice, quantity
FROM orders
JOIN order_details ON orders.orderid=order_details.orderid
JOIN customers ON customers.customerid=orders.customerid
JOIN products ON products.productid=order_details.productid;
```
* [Reference](https://www.postgresqltutorial.com/postgresql-inner-join/)

##### Left Join

```
SELECT productname, orderid
FROM products
LEFT JOIN order_details ON products.productid=order_details.productid;

SELECT productname, orderid
FROM products
LEFT JOIN order_details ON products.productid=order_details.productid
WHERE orderid IS NULL;
```
* [Reference](https://www.postgresqltutorial.com/postgresql-left-join/)

##### Right Join

```
SELECT companyname, orderid
FROM orders
RIGHT JOIN customers ON customers.customerid=orders.customerid;

SELECT companyname, orderid
FROM orders
RIGHT JOIN customers ON customers.customerid=orders.customerid
WHERE orderid IS NULL;
```
* [Reference](https://www.postgresqltutorial.com/postgresql-right-join/)

#### Full Join
```
SELECT companyname, orderid
FROM orders
FULL JOIN customers ON customers.customerid=orders.customerid;

SELECT productname, categoryname
FROM categories
FULL JOIN products ON products.categoryid=categories.categoryid;
```
* [Reference](https://www.postgresqltutorial.com/postgresql-full-outer-join/)

