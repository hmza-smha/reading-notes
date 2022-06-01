# Abstraction

Two ways to achive abstraction:
1. Abstract class (0 - 100)%.
2. Interface (100%).

The ```abstract``` keyword enables you to create classes and class members that are incomplete and must be implemented in a derived class.

It can have ```abstract``` and Non-```abstract``` methods.

It can not be instantiated, so it need to be extended.

## Why do we need ```abstract``` class ?
The purpose of an abstract class is to provide a common definition of a base class that multiple derived classes can share. For example, a class library may define an abstract class that is used as a parameter to many of its functions, and require programmers using that library to provide their own implementation of the class by creating a derived class.

## Abstract base classes
You can declare a class as abstract if you want to prevent direct instantiation by using the new operator. An abstract class can be used only if a new class is derived from it. An abstract class can contain one or more method signatures that themselves are declared as abstract. These signatures specify the parameters and return value but have no implementation (method body). An abstract class doesn't have to contain abstract members; however, if a class does contain an abstract member, the class itself must be declared as abstract. Derived classes that aren't abstract themselves must provide the implementation for any abstract methods from an abstract base class.

## Abstract and virtual methods in c#

When a base class declares a method as ```virtual```, a derived class can override the method with its own implementation. If a base class declares a member as ```abstract```, that method **must** be overridden in any non-abstract class that directly inherits from that class. If a derived class is itself ```abstract```, it inherits abstract members without implementing them. ```Abstract``` and ```virtual``` members are the basis for [Polymorphism](week3/Polymorphism.md).


### Notes
The ```sealed``` keyword enables you to prevent the inheritance of a class or certain class members that were previously marked ```virtual```.

> When applied to a class, the ```sealed``` modifier prevents other classes from inheriting from it. You can also use the sealed modifier on a method or property that overrides a virtual method or property in a base class. This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties.

> The ```virtual``` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class. 

<br>

---
[Abstract Interface](Abstract&Interface.md)