# Stored Procedure :
A stored procedure is a prepared SQL code that you can save, so the code can be reused over and over again.

<br>

So if you have an SQL query that you write over and over again, save it as a stored procedure, and then just call it to execute it.

<br>

You can also pass parameters to a stored procedure, so that the stored procedure can act based on the parameter value(s) that is passed.

## Creating 

```sql
CREATE PROCEDURE procedure_name
AS
sql_statement
GO;
```

## Excuting

```sql
EXEC procedure_name;
```

### Example

```sql
CREATE PROCEDURE SelectAllCustomers
AS
SELECT * FROM Customers
GO;
Execute the stored procedure above as follows:
```

```sql
EXEC SelectAllCustomers;
```

## Stored Procedure With One Parameter

The following SQL statement creates a stored procedure that selects Customers from a particular City from the "Customers" table:

```sql
CREATE PROCEDURE SelectAllCustomers @City nvarchar(30)
AS
SELECT * FROM Customers WHERE City = @City
GO;
```


```sql
EXEC SelectAllCustomers @City = 'London';
```

## Stored Procedure With Multiple Parameters
Setting up multiple parameters is very easy. Just list each parameter and the data type separated by a comma as shown below.

The following SQL statement creates a stored procedure that selects Customers from a particular City with a particular PostalCode from the "Customers" table:


```sql
CREATE PROCEDURE SelectAllCustomers @City nvarchar(30), @PostalCode nvarchar(10)
AS
SELECT * FROM Customers WHERE City = @City AND PostalCode = @PostalCode
GO;
```

```sql
EXEC SelectAllCustomers @City = 'London', @PostalCode = 'WA1 1DP';
```