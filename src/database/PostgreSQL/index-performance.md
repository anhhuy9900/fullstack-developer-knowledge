# Index Performance

This is example about index performance.

## Example

##### Types of Indexes

- B-Tree
  - [Reference](https://www.postgresqltutorial.com/postgresql-b-tree-index/)
- Hash
  - [Reference](https://www.postgresqltutorial.com/postgresql-hash-index/)
- Bitmap
  - [Reference](https://www.postgresqltutorial.com/postgresql-bitmap-index/)
- GiST
  - [Reference](https://www.postgresqltutorial.com/postgresql-gist/)
- GIN
  - [Reference](https://www.postgresqltutorial.com/postgresql-gin/)
- GIST
  - [Reference](https://www.postgresqltutorial.com/postgresql-gist/)
- BRIN
  - [Reference](https://www.postgresqltutorial.com/postgresql-brin/)
- SpGist
  - [Reference](https://www.postgresqltutorial.com/postgresql-spgist/)
- RTree
  - [Reference](https://www.postgresqltutorial.com/postgresql-rtree/)

##### Create INDEX

```
CREATE INDEX idx_customers_city ON customers (city);
```

##### Drop INDEX

```
DROP INDEX idx_customers_city;
```

##### How to kill run away queries

```
CREATE TABLE performance_test (
  id serial,
  location text
);

INSERT INTO performance_test (location)
SELECT 'Katmandu, Nepal' FROM generate_series(1,500000000);

//See what is running
SELECT * FROM pg_stat_activity WHERE state = 'active';

// polite way to stop
SELECT pg_cancel_backend(PID);

//stop at all costs - can lead to full database restart
SELECT pg_terminate_backend(PID);
```

###### Using EXPLAIN to see performance of queries

```
DROP TABLE IF EXISTS performance_test;

CREATE TABLE performance_test (
  id serial,
  location text
);


INSERT INTO performance_test (location)
SELECT md5(random()::text) FROM generate_series(1,10000000);

-- this takes forever 332
SELECT COUNT(*) FROM performance_test;

-- this takes 331 msec
SELECT * FROM performance_test
WHERE id = 2000000;

-- notice that it does a sequential scan
EXPLAIN SELECT COUNT(*) FROM performance_test;

EXPLAIN SELECT * FROM performance_test
WHERE id = 2000000;


CREATE INDEX idx_performance_test_id ON performance_test (id);

-- now will use an index scan
EXPLAIN SELECT * FROM performance_test
WHERE id = 2000000;

-- now count runs in 26 msec
SELECT * FROM performance_test
WHERE id = 2000000;

-- still does sequence scan
EXPLAIN SELECT COUNT(*) FROM performance_test;

-- still takes 319 msec
SELECT COUNT(*) FROM performance_test;
```

```
-- it thinks there will be rows=50000
EXPLAIN ANALYZE SELECT * FROM performance_test
WHERE id = 2000000;

ANALYZE performance_test;

-- it now thinks there will be rows=1
EXPLAIN ANALYZE SELECT * FROM performance_test
WHERE id = 2000000;
```
