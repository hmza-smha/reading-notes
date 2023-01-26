# Functions

A function is a database object in SQL Server. Basically, it is a set of SQL statements that accept only input parameters, perform actions and return the result. The function can return only a single value or a table. We can’t use a function to Insert, Update, Delete records in the database table(s).

- Types of Function

## System Defined Function

These types of functions generally work with the SQL select statement to calculate the values and the manipulated data.

### Scalar Function (عددية)
Scalar functions operate on a single value and return a **single value**. Below is the list of some useful SQL Server Scalar functions.

- **abs(-10.67)**:	        This returns an absolute number of the given number means 10.67.
- **rand(10)**:	            This will generate a random number of 10 characters.
- **round(17.56719,3)**:	This will round off the given number to 3 places of decimal meaning 17.567
- **upper('dotnet')**:	    This will return the upper case of the given string meaning 'DOTNET'
- **lower('DOTNET')**:	    This will returns the lower case of the given string means 'dotnet'
- **ltrim(' dotnet')**:	    This will remove the spaces from the left-hand side of the 'dotnet' string.
- **convert(int, 15.56)**:	This will convert the given float value to integer means 15.

### Aggregate Function (تجميعية)
Aggregate functions operate on a collection of values and return a **single value**. Below is the list of some useful SQL Server Aggregate functions.

- **max()**:    This returns the maximum value from a collection of values.
- **min()**:    This returns the minimum value from a collection of values.
- **avg()**:    This returns an average of all values in a collection.
- **count()**:	This returns no of counts from a collection of values.

## User-Defined Function

The user-defined functions may accept required parameters, perform certain actions, and return the processed data. These custom functions help us to simplify the overall database development by encapsulating the complex business logic and making it available for reuse whenever any similar functionality is required.


### Scalar Function
The user-defined scalar function also returns a single value as a result of actions performed by the function. We return any datatype value from a function.

### Example 

```sql
--Insert Data
Insert into Employee(EmpID,FirstName,LastName,Salary,Address) Values(1,'Mohan','Chauahn',22000,'Delhi');
```

### Create the function

```sql
--Create function to get emp full name 
Create function fnGetEmpFullName
(
 @FirstName varchar(50),
 @LastName varchar(50)
)
returns varchar(101)
As
Begin return (Select @FirstName + ' '+ @LastName);
end 
```

### Calling

```sql
 --Calling the above created function
Select dbo.fnGetEmpFullName(FirstName,LastName) as Name, Salary from Employee 
```


### Multi-Statement Table-Valued Function
A user-defined multi-statement table-valued function returns a table variable as a result of actions performed by the function. In this, a table variable must be explicitly declared and defined whose value can be derived from multiple SQL statements.

### Example

```sql
 --Create function for EmpID,FirstName and Salary of Employee
Create function fnGetMulEmployee()
returns @Emp Table
(
EmpID int, 
FirstName varchar(50),
Salary int
)
As
begin
 Insert into @Emp Select e.EmpID,e.FirstName,e.Salary from Employee e;
--Now update salary of first employee
 update @Emp set Salary=25000 where EmpID=1;
--It will update only in @Emp table not in Original Employee table
return
end 
```

### Calling

```sql
 --Now call the above created function
Select * from fnGetMulEmployee() 
```

>  --Now see the original table. This is not affected by above function update command
Select * from Employee 


## Summary

A function in SQL Server is a set of SQL is a series of statements that perform specific intended tasks. Functions are the best way to achieve higher code reusability and If we have to repeatedly write the intense SQL scripts to perform the same task then we can create a function that performs that similar task seamlessly. So by the next time onwards, instead of rewriting the SQL, you can simply call the user-defined functions. A function may accept some inputs in the form of parameters or arguments and returns some processed values. SQL Server comes with a variety of in-built functions that perform a variety of tasks accordingly.