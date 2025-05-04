# Transaction

A database transaction is a single unit of work that consists of one or more operations.

## Example

- Start a transaction

```
begin transaction;
    update public.products 
    set "name" = 'test'
    where id = 1;
end transaction;
```

- Commit a transaction
```
begin;
insert into product-category (id, "name", description, status, "updatedAt", "createdAt", "deletedAt")
values(6, 'Test', 'Test', false, NOW(),NOW(), null)
commit;
```

- Rollback a transaction
```
start transaction;

insert into "product-category" (id, "name", description, status, "updatedAt", "createdAt", "deletedAt")
values(6, 'Test 6', 'Test', true, NOW(),NOW(), null);

savepoint ignore_update_status;

update "product-category" set status = true;

rollback to ignore_update_status;

update "product-category" set status = false where id = 6;

commit;
```

- CASE ROLLBACK
- When we run a transaction, we can rollback the transaction by using the ROLLBACK statement. please view example below. You will see that when starts transaction the row will be locked. and value also changed

```
START TRANSACTION;
UPDATE `awesome-db`.test SET data = 'hhhhhhh' WHERE id = 10;
```
- Then we will run the script below to update the value of column data to 'sdsfdsds'

```
UPDATE `awesome-db`.test SET data = 'sdsfdsds' WHERE id = 10;

```
- Now when we get new value of data, we will see that it is 'sdsfdsds'
- But run ROLLBACK, we will see that the value of data will back first value
```
ROLLBACK
```
## Reference

- <https://www.postgresqltutorial.com/postgresql-transaction/>
