# View

This is example about View.

## Example

##### Create View

```
CREATE VIEW customer_order_details AS
SELECT companyname, Orders.customerid, employeeid, orderdate, requireddate, shippeddate
Shipvia, freight, shipname, shipaddress, shipcity, shipregion, shippostalcode, shipcountry,
order_details.*
FROM customers
JOIN orders on customers.customerid=orders.customerid
JOIN order_details on order_details.orderid=orders.orderid;

SELECT *
FROM customer_order_details
WHERE customerid='TOMSP';
```

##### Create View with modify

```
CREATE OR REPLACE VIEW customer_order_details AS
SELECT companyname, Orders.customerid,employeeid,requireddate,shippeddate,
Shipvia,freight,shipname,shipcity,shipregion,shippostalcode,shipcountry,
order_details.*,contactname
FROM customers
JOIN orders on customers.customerid=orders.customerid
JOIN order_details on order_details.orderid=orders.orderid;

ALTER VIEW customer_order_details RENAME TO customer_order_detailed;
```

##### Drop View

```
DROP VIEW IF EXISTS customer_order_detailed;
```