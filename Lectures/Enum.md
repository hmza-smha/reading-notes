# Enums 

An ```enum``` is a special "class" that represents a group of constants (unchangeable/read-only variables).

```enum``` (also called enumeration) is a user-defined value type used to represent a list of named integer constants. It is created using the ```enum``` keyword inside a class, structure, or namespace. 

It improves a program’s readability, maintainability and reduces complexity.

## Why And When To Use Enums?
Use enums when you have values that you know aren't going to change, like month days, days, colors, deck of cards, etc.

## Enum Values
If we do not assign values to the enum items, the items are assigned an integer value by the compiler by default starting from 0. The first item will be assigned 0 and increment by one each time we add an item.

```c#
enum year
{
    // items of the enum
    January,    //0
    February,   //1
    March,      //2
    April,      //3
    May,        //4
    June        //5
}
```

## Assigning our values
We can change the values of the enum item. If we change a value to one of the months e.g March to 10. Then the compiler will assign the others sequentially i.e it will increment by one from 10:

```c#
enum year
{
    // items of the enum
    January,    //0
    February,   //1
    March,      //10
    April,      //11
    May,        //12
    June        //13
}
```

### Access Enum
```c#
Console.WriteLine(year.January); // January
Console.WriteLine((int)year.January); // 0 
```

### Interesting facts and rules about the initialization of enum

1. We can assign one value to two enum names.

```c#
enum color
{
    Blue = 1,
    Green = 1,
    Yellow = 2
}
```
2. The compiler assigns values to the enum items if we fail to assign them. The first item is assigned 0 and the compiler increments by one.

3. We can only assign integral values to the enum names. We should not assign strings as values.

---

```c#
class Program
    {
        enum Day{
            Sun = 1,
            Mon,
            Tue,
            Wed,
            Thu,
            Fri,
            Sat
        }
        class Date
        {
            public Day Day { get; set; }
        }
        
        static void Main(string[] args)
        {
            Date date = new Date();
            date.Day = Day.Mon;
        }
    }
```

