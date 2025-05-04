# CTE QUery

This is example about CTE Query.

## Example

```
WITH top_category_sales AS (
 SELECT categoryname,SUM(od.unitprice*quantity) AS sales
 FROM categories AS c
 JOIN PRODUCTS USING(categoryid)
 JOIN order_details AS od USING (productid)
 GROUP BY categoryname
 ORDER BY sales DESC LIMIT 3
)
SELECT categoryname,productname,SUM(od.quantity) AS product_units,
SUM(od.unitprice*quantity) AS product_sales
FROM categories AS c
JOIN PRODUCTS USING(categoryid)
JOIN order_details AS od USING (productid)
WHERE categoryname IN (SELECT categoryname FROM top_category_sales)
GROUP BY categoryname,productname
ORDER BY categoryname
```

##### Use CTE in insert statement

```
WITH new_order AS (
 INSERT INTO orders
 (customerid, employeeid, orderdate, requireddate)
 VALUES ('ALFKI', 1, '1997-03-10', '1997-03-25')
 RETURNING orderid
)

INSERT INTO order_details (orderid, productid, unitprice, quantity, discount)
SELECT orderid, 1, 20, 5, 0
FROM new_order;
```

##### Use CTE in recusive query

```
WITH RECURSIVE upto(t) AS (
 SELECT 1
 UNION ALL
 SELECT t+1 FROM upto
 WHERE t < 50
)
SELECT * FROM upto


WITH RECURSIVE downfrom(t) AS (
 SELECT 500

 UNION ALL
 SELECT t-2 FROM downfrom
 WHERE t > 2
)
SELECT * FROM downfrom


WITH RECURSIVE under_responsible(firstname,lastname,title, employeeid,reportsto,level) AS (
 SELECT firstname,lastname,title,employeeid,reportsto,0 FROM employees
 WHERE employeeid=200
 UNION ALL
 SELECT Managed.firstname,Managed.lastname,Managed.title,Managed.employeeid,Managed.reportsto,level+1
 FROM employees AS managed
 JOIN under_responsible ON managed.reportsto=under_responsible.employeeid
)
SELECT * FROM under_responsible

WITH RECURSIVE report_to(firstname,lastname,title, employeeid,reportsto,level) AS (
 SELECT firstname,lastname,title,employeeid,reportsto,0 FROM employees
 WHERE employeeid=218
 UNION ALL
 SELECT manager.firstname,manager.lastname,manager.title,manager.employeeid,manager.reportsto,level+1
 FROM employees AS manager
 JOIN report_to ON report_to.reportsto=manager.employeeid
)
SELECT * FROM report_to
```

##### References

- [Reference](https://www.postgresqltutorial.com/postgresql-cte/)
