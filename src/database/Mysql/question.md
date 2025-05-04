# Question for query

#### Write a query to select/delete duplicate rows from the EMP table

```bash
```

#### Write a query to find the employees who are working in the company for the past 5 years

```bash
select * from emp where hiredate < add_months(sysdate,-60);
```

#### Write a query to find the LAST inserted record in a table

```bash
select * from t
where TIMESTAMP_COLUMN = (select max(timestamp_column) from T) and rownum = 1;
```

#### Write a query to find the number of rows in a table without using COUNT function

```bash
select * from emp
where sal not in
(
    select A.sal
    from emp A, emp B
    where A.sal < B.sal
)
```

#### Write a query to display the employee information, who have more than 2 employees under a manager

```bash
select * from
(
    SELECT e.*, count(mgr) over (partition by mgr) as cnt
    from emp e
)
where cnt >= 2
```

#### Write a query to select only those employee information who are earning the same salary?

- 1st way

```bash
select e1.* from emp e1,emp e2
 where e1.sal=e2.sal
   and e1.ename <> e2.ename
```

- 2st way

```bash
select * from emp
 where sal in
 3rd way
(select sal from emp
  group by sal
 having count(sal)>=2
)
```
