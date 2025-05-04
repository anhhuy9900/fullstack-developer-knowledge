# Condition Expressions

This is example about Condition Expressions.

## Example

- [Reference](https://www.postgresql.org/docs/9.5/static/functions-conditional.html)

###### Use Case When

```
SELECT productname,unitprice,
CASE WHEN unitprice<10 THEN 'inexpensive'
     WHEN unitprice>=10 AND unitprice<=50 THEN 'mid-range'
     WHEN unitprice > 50 THEN 'premium'
END AS quality
FROM products;
```

###### Use Coalesce

```
SELECT companyname,COALESCE(homepage,'Call to find') from suppliers;
```

###### Use Nullif

```
SELECT companyname,
COALESCE(NULLIF(fax,''),phone) AS confirmation
FROM customers;
```
