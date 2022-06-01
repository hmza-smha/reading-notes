# What is the Class ?

In general, we can say the class is a *container* of some code, a *blueprint* for some code or a *reference type*.

In technical we can say it is a collection of *data (fields & attributes)*, and *methods, functions, algorithms* that operate or work on that data to give a specific result.

<br>

# What is the Object?

In general we can say object is an entity that has a *state (values)* and *behaviour (finctionality)*.

In some ***interpreted languages*** like *JavaScript & Python*, you can create an object without a class.

In some ***compiled languages*** like *Java, C++, C#*, you can NOT create an object without a class, so ***here you can say object is an instance of a class***.

<br>

### - Ananymous Object

It is an object with no reference *(nameless)*, it can be used at the time of object creation only.

<br>

## Objects is a combination of:

- **Declaration**: means to tell the compiler that something exists, so that space may be allocated for it.

- **Initialization**: means to give an initial value to. In some languages, if you don't initialize a variable it will have arbitrary (dirty/garbage) data in it. In C# it is actually a compile-time error to read from an uninitialized variable.

- **Instantiation**: literally means *"to create an instance of"*. In programming, this generally means to create an instance of an object *(generally on "the heap")*. This is done via the ```new``` keyword in most languages.

- **Assigning** is simply the storing of one value to a variable. ```x = 5``` assigns the value 5 to the variable ```x```.

Note that the statement ```object myObject = new object();``` combines all four of these.

```object myObject``` declares a new object reference.
```=``` initializes the reference variable by assigning the value of the reference to it.
```new object()``` instantiates a new object ```object```, returning a reference to it.

<br>

***

[Constructors](./Constructors.md)