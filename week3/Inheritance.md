# Inheritance

Inheritance enables you to create new classes that *reuse, extend, and modify* the behavior defined in other classes.

Inheritance is a mechanisim in which one object acquires all the props and behaviors of a parent object.

Conceptually, a derived class is a specialization of the base class.

Inheritance represent the **IS-A relationship**.

> If a class have an Object reference as a prop, then its known as *Aggregation*, which represent **HAS-A relationship**.

## why do we need Inheritance?
The derived class reuses the code in the base class without having to reimplement it. 
- To perform the concept of DRY code.
- For Reuasability.

<br>

Three types of Inheritance:
1. Single *A extend B*. A inherits the all the members declared in B.
2. Hierarchical *A extend B extend C*. A inherits the all the members declared in B and C.
3. Multilevel *supported through Interfaces only, because of ambiguty*.

<br>

### Note
```c# Structs``` do not support inheritance, but they can implement interfaces.

## Abstract and virtual methods in c#

When a base class declares a method as ```virtual```, a derived class can override the method with its own implementation. If a base class declares a member as ```abstract```, that method **must** be overridden in any non-abstract class that directly inherits from that class. If a derived class is itself ```abstract```, it inherits abstract members without implementing them. ```Abstract``` and ```virtual``` members are the basis for [Polymorphism](week3/Polymorphism.md).

## Preventing further derivation
A class can prevent other classes from inheriting from it, or from any of its members, by declaring itself or the member as ```sealed``` keyword.

## Derived class hiding of base class members
A derived class can hide base class members by declaring members with the same name and signature. 

<br>

---

<br>

[Interface](week3/Interface.md)