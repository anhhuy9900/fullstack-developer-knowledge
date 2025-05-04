# Array Data

This is example about array data.

## Example

- [Reference](https://www.postgresql.org/docs/9.5/static/functions-array.html)

##### Create Array Data

```
DROP TABLE IF EXISTS friends;


CREATE TABLE friends (
    name full_name,
    address address,
    specialdates dates_to_remember,
    children varchar(50) ARRAY
);
```

##### Insert Array Data
```
INSERT INTO friends (name, address, specialdates, children)
VALUES (ROW('Boyd','M','Gregory'),
		ROW('7777','','Boise','Idaho','USA','99999'),
		ROW('1969-02-01',49,'2001-07-15'),
	   '{"Austin","Ana Grace"}');
```

##### Access Array Data
```
SELECT children[2]
FROM friends;

SELECT pay_by_quarter[2:3]
FROM salary_employees;

SELECT array_dims(schedule)
FROM salary_employees;

SELECT array_length(schedule,1),array_length(schedule,2)
FROM salary_employees;
```

##### Update Array Data
```
UPDATE friends
SET children=ARRAY['Maddie','Timmy','Cheryl']
WHERE (name).first_name = 'Boyd';

SELECT children
FROM friends
WHERE (name).first_name = 'Boyd'
LIMIT 1;

UPDATE friends
SET children[2]='Ricky'
WHERE (name).first_name = 'Boyd';

SELECT children
FROM friends
WHERE (name).first_name = 'Boyd'
LIMIT 1;

UPDATE friends
SET children[2:3]=ARRAY['Suzy','Billy']
WHERE (name).first_name = 'Boyd';

SELECT children
FROM friends
WHERE (name).first_name = 'Boyd'
LIMIT 1;
```

##### Search Array Data

```
SELECT *
FROM friends
WHERE children[0] = 'Billy' OR children[1] = 'Billy'
OR children[2]='Billy' OR children[3]='Billy';

SELECT *
FROM friends
WHERE 'Austin' = ANY (children)

SELECT *
FROM salary_employees
WHERE 'sales call' = ANY (schedule);
```

##### Delete Array Data

```
DELETE FROM friends
WHERE (name).first_name = 'Boyd';
```
