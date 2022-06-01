# What is the Constructor ?

It is a special type method which usually used to give the object default values.

Every time an object is created using ```new``` keyword, at least one cunstructor will be called.

Constructors don't return any type.

<br>

- The constructor can NOT be ```abstract```, ```static``` or ```final```.
- We can use *access modifires* like ```private``` and ```protected``` whith constructors.

### Static Constructor

In fact, constructors are implicitly final and static, you don't need to declare it again.

In C# a ```class``` or ```struct``` can also have a *static* constructor 😮, which initializes *static members of the type*.
*Static* constructors are *parameterless*. If you don't provide a static constructor to initialize static fields, the C# compiler initializes static fields to their default value as listed in the *Default values of C#*.

### Final Constructor
> If you declare a *method* as final, then you cannot *override* it.
By default you can not override nor inherit constructors, so no need for final constructors.

### Abstract Constructor
Constructors needs to have a body and implementatoin, so thre is no sense if it abstract.

### Private Constructor
A *private constructor* is a special instance constructor.
It is generally used in classes that contain *static* members only.
If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.

*Private constructors* are used to prevent creating instances of a class when there are no instance fields or methods, such as the Math class, or when a method is called to obtain an instance of a class. 

If all the methods in the class are static, consider making the complete class static.

### Remember if constructor private then:
- It does not allow a class to be sub-classed.
- It does not allow to create an object outside the class.
- If a class has a private constructor and when we try to extend the class, a compile-time error occurs.
- We cannot access a private constructor from any other class.
- If all the constant methods are there in our class, we can use a private constructor.
- If all the methods are static then we can use a private constructor.
- We can use a public function to call the private constructor if an object is not initialized.
- We can return only the instance of that object if an object is already initialized.

# Private Constructors

### It can only access the static member(s) of the class.
Reason : Non static member is specific to the object instance. If static constructor are allowed to work on non static members it will reflect the changes in all the object instance, which is impractical.

### There should be no parameter(s) in static constructor.
Reason: Since, It is going to be called by CLR, nobody can pass the parameter to it.

### Only one static constructor is allowed.
Reason: Overloading needs the two methods to be different in terms of method/constructor definition which is not possible in static constructor.

### There should be no access modifier to it.
Reason: Again the reason is same call to static constructor is made by CLR and not by the object, no need to have access modifier to it

<br>

A static constructor is used to initialize any static data, or to perform a particular action that needs performed once only. It is called automatically before the first instance is created or any static members are referenced.

Static constructors have the following properties:

1. A static constructor does not take access modifiers or have parameters.

2. A static constructor is called automatically to initialize the class before the first instance is created or any static members are referenced.

3. A static constructor cannot be called directly.

4. The user has no control on when the static constructor is executed in the program.

5. A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.

<br>

Static constructors are also very useful when you have static fields that rely upon each other such that the order of initialization is important. If you run your code through a formatter/beautifier that changes the order of the fields then you may find yourself with null values where you didn't expect them.

Example: Suppose we had this class:

```c#
class ScopeMonitor
{
    static string urlFragment = "foo/bar";
    static string firstPart= "http://www.example.com/";
    static string fullUrl= firstPart + urlFragment;
}
```

When you access fullUr, it will be "http://www.example.com/foo/bar".

Months later you're cleaning up your code and alphabetize the fields (let's say they're part of a much larger list, so you don't notice the problem). You have:

```c#
class ScopeMonitor
{
    static string firstPart= "http://www.example.com/";
    static string fullUrl= firstPart + urlFragment;
    static string urlFragment = "foo/bar";
}
```

Your fullUrl value is now just "http://www.example.com/" since urlFragment hadn't been initialized at the time fullUrl was being set. Not good. So, you add a static constructor to take care of the initialization:

```c#
class ScopeMonitor
{
    static string firstPart= "http://www.example.com/";
    static string fullUrl;
    static string urlFragment = "foo/bar";

    static ScopeMonitor()
    {
        fullUrl= firstPart + urlFragment;

    }
}
```

Now, no matter what order you have the fields, the initialization will always be correct.