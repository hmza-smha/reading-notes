# Polymorphism
Polymorphism is a mechanism to perform *single action in different ways*.

Polymorphism is a Greek word that means "many-shaped" and it has two distinct aspects:
1. Compile-time *(Overloading)*.
2. Run-time *(Overriding)*.

### Example
Suppose you have a drawing application that enables a user to create various kinds of shapes on a drawing surface. You don't know at compile time which specific types of shapes the user will create. However, the application has to keep track of all the various types of shapes that are created, and it has to update them in response to user mouse actions. You can use polymorphism to solve this problem in two basic steps:

1. Create a class hierarchy in which each specific shape class derives from a common base class.
2. Use a virtual method to invoke the appropriate method on any derived class through a single call to the base class method.

<br>

## Virtual members
When a derived class inherits from a base class, it gains all the methods, fields, properties, and events of the base class. The designer of the derived class has different choices for the behavior of virtual methods:

- The derived class may override virtual members in the base class, defining new behavior.
- The derived class may inherit the closest base class method without overriding it, preserving the existing behavior but enabling further derived classes to override the method.
- The derived class may define new non-virtual implementation of those members that hide the base class implementations.

A derived class can override a base class member only if the base class member is declared as virtual or abstract. The derived member must use the override keyword to explicitly indicate that the method is intended to participate in virtual invocation.

## Abstract and virtual methods in c#

When a base class declares a method as ```virtual```, a derived class can override the method with its own implementation. If a base class declares a member as ```abstract```, that method **must** be overridden in any non-abstract class that directly inherits from that class. If a derived class is itself ```abstract```, it inherits abstract members without implementing them. ```Abstract``` and ```virtual``` members are the basis for **Polymorphism**.

When a virtual method is invoked, the run-time type of the object is checked for an overriding member. The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.
