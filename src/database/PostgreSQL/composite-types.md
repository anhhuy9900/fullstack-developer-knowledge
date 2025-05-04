## Composite Types

This is example about composite types.

## Example

```
CREATE TYPE address AS (
	street_address 	varchar(50),
	street_address2 varchar(50),
	city			varchar(50),
	state_region	varchar(50),
	country			varchar(50),
	postalcode		varchar(15)
);

CREATE TABLE friends (
	first_name varchar(100),
	last_name varchar(100),
	address	address
);

DROP TYPE address CASCADE;
DROP TABLE friends;
```

- [Reference](https://www.postgresqltutorial.com/postgresql-composite-types/)