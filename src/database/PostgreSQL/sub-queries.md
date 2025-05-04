# Sub queries

this is example about sub queries

* [Reference](https://www.postgresqltutorial.com/postgresql-subquery/)

## Example

##### with WHERE

```
SELECT companyname,contactname
FROM customers
WHERE EXISTS (SELECT customerid FROM orders
              WHERE customerid=customers.customerid AND
               orderdate BETWEEN '1997-04-01' AND '1997-04-30');
```

##### with where and join

```
SELECT productname
FROM products
WHERE NOT EXISTS (
    SELECT orders.orderid FROM orders
    JOIN order_details ON orders.orderid=order_details.orderid
    WHERE order_details.productid=products.productid AND
    orderdate BETWEEN '1997-04-01' AND '1997-04-30'
);
```

##### with ANY

```
SELECT companyname
FROM suppliers
WHERE  supplierid = ANY (SELECT products.supplierid FROM order_details
                        JOIN products ON products.productid=order_details.productid
                        WHERE quantity = 1);
```

##### with ALL

```
SELECT DISTINCT name
FROM products
JOIN order_details ON products.id = order_details.productId
WHERE  order_details.unitPrice * quantity > ALL (
    SELECT AVG(order_details.unitPrice*quantity)
    FROM order_details
    GROUP BY productId
);
```

##### with IN

```
SELECT companyName
FROM suppliers
WHERE city IN (SELECT DISTINCT city
                  FROM customers);
```