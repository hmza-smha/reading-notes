# Properties (get, set) In C#

### A property is a member that provides a flexible mechanism to read, write, or compute the value of a private field.

Properties can be used as if they are public data members, but they are actually special methods called *accessors*.

The ```get``` accessor returns the value of the private field, and the ```set``` accessor may perform some data validation before assigning a value to the private field.

- Properties enable a class to expose a public way of getting and setting values, while hiding implementation or verification code.

- A ```get``` property accessor is used to return the property value, and a ```set``` property accessor is used to assign a new value. An ```init``` property accessor is used to assign a new value only during object construction.

- The ```value``` keyword is used to define the value being assigned by the ```set``` or ```init``` accessor.

- Properties can be read-write (they have **BOTH** a ```get``` and a ```set``` accessor), read-only (they have a ```get``` accessor but **NO** ```set``` accessor), or write-only (they have a set accessor, but **NO** get accessor).
> Write-only properties are rare and are most commonly used to restrict access to sensitive data.

### Example

```c#
using System;

class TimePeriod
{
   private double _seconds;

   public double Hours
   {
       get { return _seconds / 3600; }
       set {
          if (value < 0 || value > 24)
             throw new ArgumentOutOfRangeException(
                   $"{nameof(value)} must be between 0 and 24.");

          _seconds = value * 3600;
       }
   }
}
```


## Auto-implemented properties
In some cases, property get and set accessors just assign a value to or retrieve a value from a backing field without including any additional logic.

```c#
public class SaleItem
{
   public string Name
   { get; set; }

   public decimal Price
   { get; set; }
}
```


## Expression body definitions
Expression body definitions consist of the ```=>``` symbol followed by the expression to assign to or retrieve from the property.

In this case, neither the get accessor keyword nor the return keyword is used. 

The following example implements the *read-only* Name property as an expression-bodied member.

```c# 
public class Person
{
   private string _firstName;
   private string _lastName;

   public Person(string first, string last)
   {
      _firstName = first;
      _lastName = last;
   }

   public string Name => $"{_firstName} {_lastName}";
}
```

The following example illustrates the use of expression body definitions for both accessors.

```c#
public class SaleItem
{
   string _name;
   decimal _cost;

   public SaleItem(string name, decimal cost)
   {
      _name = name;
      _cost = cost;
   }

   public string Name
   {
      get => _name;
      set => _name = value;
   }

   public decimal Price
   {
      get => _cost;
      set => _cost = value;
   }
}
```
