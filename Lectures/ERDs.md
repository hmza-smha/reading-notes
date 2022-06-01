## Database
It is a collection of data stored in a format that can be easily be accessed.

<br>

### Data can be stored in defferent ways:
  1. On paper.
  2. In your mind.
  3. On a PC 😍


## DBMS 
A special software program, helps users to CRUD and maintain DBs.

<br>

## DB types

## 1. Relational-DB (SQL)
- Rows & Columns (two-dimensional).
- Relationships b/t tables.
- simmilar to Excel Sheets.
- Unique key in each table.
- MySQL, Oracle, SQL Server.
    - Each DBMS has different flavor of SQL.

## 2. Non-Relational-DB (No SQL)
- Organize data in anything but not tables.
- Key-Value
- JSON, XML
- mongoDB, Firebase

## What is Schema ?
A database schema is a blueprint or architecture of how our data will look. 

It doesn’t hold data itself, but instead describes the shape of the data and how it might
relate to other tables or models. An entry in our database will be an instance of the
database schema. It will contain all of the properties described in the schema.

## Why do we need Schema ?
Database schemas are important because they help developers visualize how a database should be structured.

---

## What's primary key in database?
A primary key is the column or columns that contain values that uniquely identify each row in a table. A database table must have a primary key for Optim to insert, update, restore, or delete data from a database table. Optim uses primary keys that are defined to the database.

## What's FOREIGN key in database?
A FOREIGN KEY is a field (or collection of fields) in one table, that refers to the PRIMARY KEY in another table. The table with the foreign key is called the child table, and the table with the primary key is called the referenced or parent table.

## What's composite key in database?
A composite key is a specific type of primary key which uses the contents of two or more fields from a table to create a unique value

---

## Database Relationships

In relational databases, a relationship exists between two tables when one of them has a foreign key that references the primary key of the other table.

### One-to-one	
- Both tables can have only one record on each side of the relationship.
- Each primary key value relates to none or only one record in the related table.
- Most one-to-one relationships are forced by business rules and do not flow naturally from the data. - Without such a rule, you can typically combine both tables without breaking any normalization rules.

### One-to-many
The primary key table contains only one record that relates to none, one, or many records in the related table.

### Many-to-many
Each record in both tables can relate to none or any number of records in the other table. These relationships require a third table, called an associate or linking table, because relational systems cannot directly accommodate the relationship.