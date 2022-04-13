# Entity Framework

EF Core can serve as an object-relational mapper (O/RM), which:

Enables .NET developers to work with a database using .NET objects.
Eliminates the need for most of the data-access code that typically needs to be written.

## The model
With EF Core, data access is performed using a model. A model is made up of entity classes and a context object that represents a session with the database. The context object allows querying and saving data. 

**EF supports the following model development approaches:**

Generate a model from an existing database.
Hand code a model to match the database.
Once a model is created, use EF Migrations to create a database from the model. Migrations allow evolving the database as the model changes.


## Querying
Instances of your entity classes are retrieved from the database using Language Integrated Query (LINQ)

## Saving data
Data is created, deleted, and modified in the database using instances of your entity classes.

<br>

---

<br>

## Data Seeding

Data seeding is the process of populating a database with an initial set of data.

There are several ways this can be accomplished in EF Core:

1. Model seed data
2. Manual migration customization
3. Custom initialization logic