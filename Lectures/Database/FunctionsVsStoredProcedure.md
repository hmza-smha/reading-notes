# Functions VS Stored Procedure

Both stored procedures and functions are database objects which contain a set of SQL statements to complete a task. In many ways, both are different from each other. In this article, we’re going to discuss the differences between stored procedures and functions.

## Stored Procedures
Stored Procedures are **pre-compiled** objects which are compiled for the first time and its compiled format is saved, which executes (compiled code) whenever it is called.

## Functions
A function is compiled and executed every time whenever it is called. A function must return a value and cannot modify the data received as parameters.

### Basic Differences between Stored Procedure and Function in SQL Server
- The function must return a value but in Stored Procedure it is optional. Even a procedure can return zero or n values.
- Functions can have only input parameters for it whereas Procedures can have input or output parameters.
- Functions can be called from Procedure whereas Procedures cannot be called from a Function.

### Advance Differences between Stored Procedure and Function in SQL Server

- The procedure allows SELECT as well as DML(INSERT/UPDATE/DELETE) statement in it whereas Function allows only SELECT statement in it.
- Procedures cannot be utilized in a SELECT statement whereas Function can be embedded in a SELECT statement.
- Stored Procedures cannot be used in the SQL statements anywhere in the WHERE/HAVING/SELECT section whereas Function can be.
- Functions that return tables can be treated as another rowset. This can be used in JOINs with other tables.
- Inline Function can be though of as views that take parameters and can be used in JOINs and other Rowset operations.
- An exception can be handled by try-catch block in a Procedure whereas try-catch block cannot be used in a Function.
- We can use Transactions in Procedure whereas we can't use Transactions in Function.