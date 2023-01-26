# A Stored Procedure:

- Accepts parameters
- Can **NOT** be used as building block in a larger query
- Can contain several statements, loops, IF ELSE, etc.
- Can perform modifications to one or several tables
- Can NOT be used as the target of an INSERT, UPDATE or DELETE statement.

# A View:

- Does **NOT** accept parameters
- Can be used as building block in a larger query
- Can contain only one single **SELECT** query
- Can **NOT** perform modifications to any table
- But can (sometimes) be used as the target of an INSERT, UPDATE or DELETE statement.