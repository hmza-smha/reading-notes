# DependencyInjection

dependency injection (DI) software design pattern, which is a technique for achieving Inversion of Control (IoC) between classes and their dependencies.

A dependency is an object that another object depends on. Examine the following ```MyDependency``` class with a ```WriteMessage``` method that other classes depend on:

```c#
public class MyDependency
{
    public void WriteMessage(string message)
    {
        Console.WriteLine($"MyDependency.WriteMessage called. Message: {message}");
    }
}
```

A class can create an instance of the ```MyDependency``` class to make use of its ```WriteMessage``` method. In the following example, the ```MyDependency``` class is a dependency of the IndexModel class:

```c#
public class IndexModel : PageModel
{
    private readonly MyDependency _dependency = new MyDependency();

    public void OnGet()
    {
        _dependency.WriteMessage("IndexModel.OnGet");
    }
}
```

The class creates and directly depends on the ```MyDependency``` class. Code dependencies, such as in the previous example, are problematic and should be avoided for the following reasons:

- To replace MyDependency with a different implementation, the IndexModel class must be modified.
- If MyDependency has dependencies, they must also be configured by the IndexModel class. In a large project with multiple classes depending on MyDependency, the configuration code becomes scattered across the app.
- This implementation is difficult to unit test.
- Dependency injection addresses these problems through:



## The Repository pattern
Repositories are classes or components that encapsulate the logic required to access data sources. They centralize common data access functionality, providing better maintainability and decoupling the infrastructure or technology used to access databases from the domain model layer. If you use an Object-Relational Mapper (ORM) like Entity Framework, the code that must be implemented is simplified, thanks to LINQ and strong typing. This lets you focus on the data persistence logic rather than on data access plumbing.

## Repository Design Pattern

the repository pattern have two purposes;
> first it is an abstraction of the data layer
> second it is a way of centralising the handling of the domain objects.

