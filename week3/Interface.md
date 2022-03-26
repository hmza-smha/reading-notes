# Interface

Interface is a ***Blueprint*** of a *class*, it is a mechanisim to achieve *full abstraction* and *multiple inheritance*.

An interface is a reference type that defines a set of members. All classes and structs that implement that interface *must* implement that set of members. An interface may define a default implementation for any or all of these members.

An interface contains definitions for a group of related functionalities that a non-abstract ```class``` or a ```struct``` must implement. An interface may define ```static``` methods, which must have an implementation. 

## Why do we need Interfaces?

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

<br>

### Notes
- In C# versions earlier than 8.0, an interface is like an abstract base class with only abstract members. A class or struct that implements the interface must implement all its members.

- Beginning with C# 8.0, an interface may define default implementations for some or all of its members. 

- A class or struct that implements the interface doesn't have to implement members that have default implementations.

- An interface can't be instantiated directly. Its members are implemented by any class or struct that implements the interface.

- A class or struct can implement multiple interfaces. A class can inherit a base class and also implement one or more interfaces.

<br>

---
[Abstract Interface](Abstract&Interface.md)
