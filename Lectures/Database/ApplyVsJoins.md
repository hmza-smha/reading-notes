# Apply VS Joins *(SQL Server)*

```
join is used -- between tables
apply is used -- between table and table valued function
```

- The APPLY operator introduced in SQL Server in 2005, is used to join a table to a **table-valued** function.

- The table-valued *(or normal table)* function on the right hand side of the apply operator gets called for each row from the left table. While JOIN will get the right table THEN perform the JOINing

- CROSS APPLY returns only matching rows.
- OUTER APPLY returns matching + non-matching rows. The unmatched columns of the table-valued *(or normal table)* will be set to NULL

[video 1](https://www.youtube.com/watch?v=kVogo0AbatM)

[video 2](https://www.youtube.com/watch?v=i45-_nuVytc)

### Examples

```sql
SELECT  *
FROM    table1
JOIN    table2
ON      table2.b = table1.a
```

> For each row from table1, select all rows from table2 where the value of field b is equal to that of field a

```sql
SELECT  *
FROM    table1, table2
WHERE   table2.b = table1.a
```

> Make a set of all possible combinations of rows from table1 and table2 and of this set select only the rows where the value of field b is equal to that of field a

- These conditions are worded differently, but they yield the same result and database systems are aware of that. Usually both these queries are optimized to use the same execution plan.


- To use JOINs (with whatever syntax), both sets you are joining must be self-sufficient, i. e. the sets should not depend on each other. You can query both sets without ever knowing the contents on another set.

But for some tasks the sets are not self-sufficient. For instance, let's consider the following query:

> We have table1 and table2. table1 has a column called rowcount. For each row from table1 we need to select first rowcount rows from table2, ordered by table2.id

We cannot come up with a join condition here. The join condition, should it exist, would involve the row number, which is not present in table2, and there is no way to calculate a row number only from the values of columns of any given row in table2.

- That's where the CROSS APPLY can be used.

- CROSS APPLY is a Microsoft's extension to SQL, which was originally intended to be used with table-valued functions (TVF's).

The query above would look like this:

- Notice the TOP keyword

```sql
SELECT  *
FROM    table1
CROSS APPLY
(
SELECT  TOP (table1.rowcount) *
FROM    table2
ORDER BY
id
) t2
```

> For each from table1, select first table1.rowcount rows from table2 ordered by id

[continue reading](https://explainextended.com/2009/07/16/inner-join-vs-cross-apply/)