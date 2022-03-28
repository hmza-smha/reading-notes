# Interface

Two ways to achive abstraction:
1. Abstract class (0 - 100)%.
2. Interface (100%).

Interface is a ***Blueprint*** of a *class*, it is a mechanisim to achieve *full abstraction* and *multiple inheritance*.

An interface is a reference type that defines a set of members. All classes and structs that implement that interface *must* implement that set of members. An interface may define a default implementation for any or all of these members.

An interface contains definitions for a group of related functionalities that a non-abstract ```class``` or a ```struct``` must implement. An interface may define ```static``` methods, which must have an implementation. 

## Why do we need Interfaces?

## ONE
A class can implement multiple interfaces but it can derive from only a single direct base class, because of the **ambiguity**. for example

```c#
class A{
    void print(){
        stmt;
    }
}

class B{
    void print(){
        stmt;
    }
}

class C extend B, A{

}
```
Now, The object form class C which ```print()``` method should inherit? this is the **ambiguity**.

To Solve this problem we use ```Interface```, because the method body is provided bt the implementation class.

In addition, in c# you must use an interface if you want to simulate inheritance for structs, because they can't actually inherit from another struct or class.

## TWO
The basic problem an interface is trying to solve is to separate how we use something from how it is implemented.

Why do we want to separate the use from the implementation?

So that we can write code that can work with a variety of different implementations of some set of responsibilities without having to specifically handle each implementation.

To put this more simply, this means that if we have a Driver class it should be able to have a method Drive that can be used to drive any car, boat, or other kind of class that implements the IDriveable interface.

<br>

### Notes
- In C# versions earlier than 8.0, an interface is like an abstract base class with only abstract members. A class or struct that implements the interface must implement all its members.

- Beginning with C# 8.0, an interface may define default implementations for some or all of its members. 

- A class or struct that implements the interface doesn't have to implement members that have default implementations.

- An interface can't be instantiated directly. Its members are implemented by any class or struct that implements the interface.

- A class or struct can implement multiple interfaces. A class can inherit a base class and also implement one or more interfaces.

<br>

---
[Abstract VS Interface](Abstract&Interface.md)
