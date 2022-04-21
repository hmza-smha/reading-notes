# Dependency Injection

### Dependency injection is a programming technique *(Design Pattern)* that makes a class independent of its dependencies.


## what is Dependency?
Dependency or dependent means relying on something for support. Like if I say we are relying too much on mobile phones than it means we are dependent on them.

- In programming 
When class A uses some functionality of class B, then its said that class A has a dependency of class B.


## So, What is dependency injection?
Classes often require references to other classes.
For example, a Car class might need a reference to an Engine class. These required classes are called dependencies, and in this example the Car class is dependent on having an instance of the Engine class to run


### RECALL
before we can use methods of classes, we first need to create the object of that class (i.e. class A needs to create an instance of class B).

transferring the task of creating the object to someone else and directly using the dependency is called ***dependency injection.***

## Why should I use dependency injection?
Let’s say we have a car class which contains various objects such as *wheels, engine, etc.*

Here the car class is responsible for creating all the dependency objects. Now, what if we decide to ditch *MRFWheels* in the future and want to use *Yokohama* Wheels?

We will need to recreate the car object with a new *Yokohama* dependency. But when using dependency injection (DI), we can change the Wheels at runtime (because dependencies can be injected at runtime rather than at compile time).

You can think of DI as the middleman in our code who does all the work of creating the preferred wheels object and providing it to the Car class.

It makes our Car class independent from creating the objects of *Wheels, Battery, etc.*

## There are basically three types of dependency injection:
1. **constructor injection**: the dependencies are provided through a class constructor.
2. **setter injection**: the client exposes a setter method that the injector uses to inject the dependency.
3. **interface injection**: the dependency provides an injector method that will inject the dependency into any client passed to it. Clients must implement an interface that exposes a setter method that accepts the dependency.

<br>

---

<br>

# What is the*** DI ????

## Part I: Dependency Non-Injection
Classes have variables, let’s call those “dependencies.”.
```
public class Example {
  private DatabaseThingie myDatabase;  // dependency 

  public Example() {
    myDatabase = new DatabaseThingie();
  }

  public void DoStuff() {
    ...
    myDatabase.GetData();
    ...
  }
}
```
Here, we have a variable... uh, dependency... named “myDatabase.” We initialize it in the constructor.

## Part II: Dependency Injection

If we wanted to, we could pass the variable into the constructor. That would “inject” the “dependency” into the class. Now when we use the variable (dependency), we use the object that we were given rather than the one we created.

```
public class Example {
  private DatabaseThingie myDatabase;

  public Example() {
    myDatabase = new DatabaseThingie();
  }

    // here is the game
  public Example(DatabaseThingie useThisDatabaseInstead) {
    myDatabase = useThisDatabaseInstead;
  }

  public void DoStuff() {
    ...
    myDatabase.GetData();
    ...
  }
}
```

## Exapmle

consider a `Car` object.

A `Car` depends on wheels, engine, fuel, battery, etc. to run. Traditionally we define the brand of such dependent objects along with the definition of the `Car` object.

Without Dependency Injection (DI):

```c#
  class Car{  
    private Wheel wh = new NepaliRubberWheel();  
    private Battery bt = new ExcideBattery();  
    //The rest  
   } 
``` 

Here, the `Car` object *is responsible for creating the dependent objects.*

What if we want to change the type of its dependent object - say `Wheel` - after the initial `NepaliRubberWheel()` punctures?

We need to recreate the Car object with its new dependency say `ChineseRubberWheel()`, but only the `Car` manufacturer can do that.
 Then what does the `Dependency Injection` do for us...?

When using dependency injection, objects are given their dependencies *at run time rather than compile time (car manufacturing time)*.

So that we can now change the `Wheel` whenever we want. Here, the `dependency` (`wheel`) can be injected into `Car` at run time.

After using dependency injection:

Here, we are **injecting** the **dependencies** (Wheel and Battery) at runtime. Hence the term : *Dependency Injection.* We normally rely on DI frameworks such as Spring, Guice, Weld to create the dependencies and inject where needed.

```c#
   class Car{  
    private Wheel wh; // Inject an Instance of Wheel (dependency of car) at runtime  
    private Battery bt; // Inject an Instance of Battery (dependency of car) at runtime  
    Car(Wheel wh,Battery bt) {  
      this.wh = wh;  
      this.bt = bt;  
    }  
    //Or we can have setters  
    void setWheel(Wheel wh) {  
      this.wh = wh;  
    }  
   }  
```

### The advantages/benefits of dependency injection are:
- decoupling the creation of an object (in another word, separate usage from the creation of object)
- ability to replace dependencies (eg: Wheel, Battery) without changing the class that uses it(Car)
- promotes "Code to interface not to an implementation" principle
- ability to create and use mock dependency during a test (if we want to use a Mock of Wheel during test instead of a real instance.. we can create Mock Wheel object and let DI framework inject to Car)

<br>

---

<br>

## Please

### Dependency Injection is passing dependency to other objects or framework( dependency injector).

### Dependency injection makes testing easier. The injection can be done through constructor.

```SomeClass()``` has its constructor as following:

```c#
public SomeClass() {
    myObject = Factory.getObject();
}
```

Problem: If ```myObject``` involves complex tasks such as disk access or network access, it is hard to do unit test on ```SomeClass()```. Programmers have to mock myObject and might intercept the factory call.

Alternative solution:

Passing ```myObject``` in as an argument to the constructor

```c#
public SomeClass (MyClass myObject) {
    this.myObject = myObject;
}
```

myObject can be passed directly which makes testing easier.

<br>

---

<br>

# Final Wallah

Let's try simple example with Car and Engine classes, any car need an engine to go anywhere, at least for now. So below how code will look without dependency injection.

```c#
public class Car
{
    public Car()
    {
        GasEngine engine = new GasEngine();
        engine.Start();
    }
}

public class GasEngine
{
    public void Start()
    {
        Console.WriteLine("I use gas as my fuel!");
    }
}
```
And to instantiate the Car class we will use next code:

```Car car = new Car();```

#### The issue with this code that we tightly coupled to GasEngine and if we decide to change it to ElectricityEngine then we will need to rewrite Car class. And the bigger the application the more issues and headache we will have to add and use new type of engine.

#### In other words with this approach is that our high level Car class is dependent on the lower level GasEngine class which violate Dependency Inversion Principle(DIP) from SOLID. DIP suggests that we should depend on abstractions, not concrete classes. So to satisfy this we introduce IEngine interface and rewrite code like below:

```c#
    public interface IEngine
    {
        void Start();
    }

    public class GasEngine : IEngine
    {
        public void Start()
        {
            Console.WriteLine("I use gas as my fuel!");
        }
    }

    public class ElectricityEngine : IEngine
    {
        public void Start()
        {
            Console.WriteLine("I am electrocar");
        }
    }

    public class Car
    {
        private readonly IEngine _engine;
        public Car(IEngine engine)
        {
            _engine = engine;
        }

        public void Run()
        {
            _engine.Start();
        }
    }
```

#### Now our Car class is dependent on only the IEngine interface, not a specific implementation of engine. Now, the only trick is how do we create an instance of the Car and give it an actual concrete Engine class like GasEngine or ElectricityEngine. That's where Dependency Injection comes in.

```c#
   Car gasCar = new Car(new GasEngine());
   gasCar.Run();
   Car electroCar = new Car(new ElectricityEngine());
   electroCar.Run();
```

#### Here we basically inject(pass) our dependency(Engine instance) to Car constructor. So now our classes have loose coupling between objects and their dependencies, and we can easily add new types of engines without changing the Car class.

The main benefit of the Dependency Injection that classes are more loosely coupled, because they do not have hard-coded dependencies. This follows the Dependency Inversion Principle, which was mentioned above. Instead of referencing specific implementations, classes request abstractions (usually interfaces) which are provided to them when the class is constructed.

So in the end Dependency injection is just a technique for achieving loose coupling between objects and their dependencies. Rather than directly instantiating dependencies that class needs in order to perform its actions, dependencies are provided to the class (most often) via constructor injection.

Also when we have many dependencies it is very good practice to use Inversion of Control(IoC) containers which we can tell which interfaces should be mapped to which concrete implementations for all our dependencies and we can have it resolve those dependencies for us when it constructs our object. For example, we could specify in the mapping for the IoC container that the IEngine dependency should be mapped to the GasEngine class and when we ask the IoC container for an instance of our Car class, it will automatically construct our Car class with a GasEngine dependency passed in.