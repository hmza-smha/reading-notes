# SQL Injection

- SQL injection is a code injection technique that might destroy your database.
- SQL injection is one of the most common web hacking techniques.
- SQL injection is the placement of malicious code in SQL statements, via web page input.


### SQL in Web Pages
SQL injection usually occurs when you ask a user for input, like their username/userid, and instead of a name/id, the user gives you an SQL statement that you will unknowingly run on your database.

### SQL Injection Based on 1=1 is Always True
- UserId: 105 OR 1=1
- SELECT * FROM Users WHERE UserId = 105 OR 1=1;

### SQL Injection Based on ""="" is Always True
- Username: " or ""="
- Password: " or ""="
- SELECT * FROM Users WHERE Name ="" or ""="" AND Pass ="" or ""=""

### SQL Injection Based on Batched SQL Statements 
- SELECT * FROM Users WHERE UserId = 105; DROP TABLE Suppliers;