# C#
- It is an object-oriented programming language provided by Microsoft that runs on .Net Framework.
- It is based on C++ and Java, but it has many additional extensions used to perform component oriented programming approach.

# .NET Framework
- .Net Framework is a software development platform developed by Microsoft for building and running Windows applications. 
- The .Net framework consists of developer tools, programming languages, and libraries to build desktop and web applications. It is also used to build websites, web services, and games.
- The software programs written in .NET are executed in the execution environment, which is called CLR (Common Language Runtime). 

# CLR (Common Language Runtime)
- .NET CLR is a run-time environment that manages and executes the code written in any .NET programming language.
- It acts as an interface between the framework and operating system. 
- It does exception handling, memory management, and garbage collection. Moreover, it provides security, type-safety, interoperability, and portablility.

# Debugging
Debugging is the process of finding errors during application execution. It does not mean syntax errors, with which the application cannot be compiled, but on logic errors. Logic errors can only be noticed during application execution.

# Arrays in C sharp
- Single-Dimensional
```c#
int[] array = new int[5];
```
- Multi-Dimensional
```c#
int[,] array = new int[4, 2]; // array of four rows and two columns
int[,,] array1 = new int[4, 2, 3]; // three dimensions, 4, 2, and 3.
```
- Jagged Arrays
> A jagged array is an array whose elements are arrays, possibly of different sizes. A jagged array is sometimes called an "array of arrays."
```c#
int[][] jaggedArray = new int[3][]; //  single-dimensional array that has three elements, each of which is a single-dimensional array of integers
```

>The foreach statement provides a simple, clean way to iterate through the elements of an array.

```c#
int[] numbers = { 4, 5, 6, 1, 2, 3, -2, -1, 0 };
foreach (int i in numbers)
{
    System.Console.Write("{0} ", i);
}
// Output: 4 5 6 1 2 3 -2 -1 0
```
- Implicitly Typed Arrays
>You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.

```c#
static void Main()
    {
        var a = new[] { 1, 10, 100, 1000 }; // int[]
        var b = new[] { "hello", null, "world" }; // string[]

        // single-dimension jagged array
        var c = new[]
        {
            new[]{1,2,3,4},
            new[]{5,6,7,8}
        };

        // jagged array of strings
        var d = new[]
        {
            new[]{"Luca", "Mads", "Luke", "Dinesh"},
            new[]{"Karen", "Suma", "Frances"}
        };
    }
```
