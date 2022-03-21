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

