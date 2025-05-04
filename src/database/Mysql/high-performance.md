# MySQL

This is trip for improve performance for MYSQL

## Example

#### Check the performance of schema

```
USE performance_schema;
SHOW tables; 

SELECT *
FROM   performance_schema.events_statements_summary_by_digest;

SELECT *
FROM   performance_schema.events_statements_summary_by_digest\G 

SELECT   *
FROM     performance_schema.events_statements_summary_by_digest
ORDER BY sum_timer_wait DESC limit 10\G
```

#### Check the performance of table IO

- [IO Thread](https://dev.mysql.com/doc/refman/5.7/en/innodb-io-thread.html)
```
USE performance_schema;
SHOW tables; 

SELECT *
FROM   performance_schema.events_statements_summary_by_digest;

SELECT *
FROM   performance_schema.events_statements_summary_by_digest\G 

SELECT   *
FROM     performance_schema.events_statements_summary_by_digest
ORDER BY sum_timer_wait DESC limit 10\G
```

#### Choose primary key between generate Id and auto increment
```
USE performance_schema;
SHOW tables; 

SELECT *
FROM   performance_schema.events_statements_summary_by_digest;

SELECT *
FROM   performance_schema.events_statements_summary_by_digest\G 

SELECT   *
FROM     performance_schema.events_statements_summary_by_digest
ORDER BY sum_timer_wait DESC limit 10\G
```