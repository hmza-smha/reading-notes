# Collections

For many applications, you want to create and manage groups of related objects. There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.

***Collections*** provide a more flexible way to work with groups of objects. Unlike *arrays*, the group of objects you work with can **grow** and **shrink** dynamically as the needs of the application change.

For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.

A collection is a **class**, so you must declare an instance of the class before you can add elements to that collection.

### Note:
- If your collection contains elements of only one data type, you can use one of the classes in the ```System.Collections.Generic``` namespace.

A generic collection enforces type safety so that no other data type can be added to it.

When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.

### Example
the generic ```List<T>``` class, which enables you to work with a strongly typed list of objects.

```c#
// Create a list of strings.
var salmons = new List<string>();
salmons.Add("chinook");
salmons.Add("coho");
salmons.Add("pink");
salmons.Add("sockeye");

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook coho pink sockeye
```

## Kinds of Collections
- ```System.Collections.Generic``` classes
- ```System.Collections.Concurrent``` classes
- ```System.Collections``` classes

### System.Collections.Generic
A generic collection is useful when every item in the collection has the same data type. A generic collection enforces strong typing by allowing only the desired data type to be added.

| Class | Description |
|:----- | :-----      |
|Dictionary<TKey,TValue>|Represents a collection of key/value pairs that are organized based on the key.|
|List<T>|Represents a list of objects that can be accessed by index. Provides methods to search, sort, and modify lists.|
|Queue<T>|Represents a first in, first out (FIFO) collection of objects.|
|SortedList<TKey,TValue>|Represents a collection of key/value pairs that are sorted by key based on the associated IComparer<T> implementation.|
|Stack<T>|Represents a last in, first out (LIFO) collection of objects.|

### System.Collections.Concurrent

The classes in the ```System.Collections.Concurrent``` namespace should be used whenever multiple threads are accessing the collection concurrently.

### System.Collections
The classes in the System.Collections namespace do not store elements as specifically typed objects, but as objects of type ```Object```.

| Class | Description |
|:----- | :-----      |
|ArrayList|	Represents an array of objects whose size is dynamically increased as required.|
|Hashtable|	Represents a collection of key/value pairs that are organized based on the hash code of the key.|
|Queue|	Represents a first in, first out (FIFO) collection of objects.|
|Stack|	Represents a last in, first out (LIFO) collection of objects.|

#### Hint:
Whenever possible, you should use the generic collections in the ```System.Collections.Generic``` namespace or the ```System.Collections.Concurrent``` namespace instead of the legacy types in the ```System.Collections``` namespace.

<br>

## Implementing a Collection of Key/Value Pairs
The ```Dictionary<TKey,TValue>``` generic collection enables you to access to elements in a collection by using the key of each element. Each addition to the dictionary consists of a value and its associated key. Retrieving a value by using its key is fast because the ```Dictionary``` class is implemented as a hash table.


```c#
private static void IterateThruDictionary()
{
    Dictionary<string, Element> elements = BuildDictionary();

    foreach (KeyValuePair<string, Element> kvp in elements)
    {
        Element theElement = kvp.Value;

        Console.WriteLine("key: " + kvp.Key);
        Console.WriteLine("values: " + theElement.Symbol + " " +
            theElement.Name + " " + theElement.AtomicNumber);
    }
}

private static Dictionary<string, Element> BuildDictionary()
{
    return new Dictionary<string, Element>
    {
        {"K",
            new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},
        {"Ca",
            new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},
        {"Sc",
            new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},
        {"Ti",
            new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}
    };
}

public class Element
{
    public string Symbol { get; set; }
    public string Name { get; set; }
    public int AtomicNumber { get; set; }
}
```

The following example uses the ```ContainsKey``` method and the ```Item[]``` property of ```Dictionary``` to quickly find an item by key. The Item property enables you to access an item in the elements collection by using the ```elements[symbol]``` in C#.


```c#
private static void FindInDictionary(string symbol)
{
    Dictionary<string, Element> elements = BuildDictionary();

    if (elements.ContainsKey(symbol) == false)
    {
        Console.WriteLine(symbol + " not found");
    }
    else
    {
        Element theElement = elements[symbol];
        Console.WriteLine("found: " + theElement.Name);
    }
}
```

## Defining a Custom Collection
You can define a collection by implementing the ```IEnumerable<T>``` or ```IEnumerable``` interface.

The following example defines a custom collection class named ```AllColors```. This class implements the ```IEnumerable``` interface, which requires that the ```GetEnumerator``` method be implemented.

The ```GetEnumerator``` method returns an instance of the ```ColorEnumerator``` class. ```ColorEnumerator``` implements the ```IEnumerator``` interface, which requires that the ```Current``` property, ```MoveNext``` method, and ```Reset``` method be implemented.

```c#
private static void ListColors()
{
    var colors = new AllColors();

    foreach (Color theColor in colors)
    {
        Console.Write(theColor.Name + " ");
    }
    Console.WriteLine();
    // Output: red blue green
}

// Collection class.
public class AllColors : System.Collections.IEnumerable
{
    Color[] _colors =
    {
        new Color() { Name = "red" },
        new Color() { Name = "blue" },
        new Color() { Name = "green" }
    };

    public System.Collections.IEnumerator GetEnumerator()
    {
        return new ColorEnumerator(_colors);

        // Instead of creating a custom enumerator, you could
        // use the GetEnumerator of the array.
        //return _colors.GetEnumerator();
    }

    // Custom enumerator.
    private class ColorEnumerator : System.Collections.IEnumerator
    {
        private Color[] _colors;
        private int _position = -1;

        public ColorEnumerator(Color[] colors)
        {
            _colors = colors;
        }

        object System.Collections.IEnumerator.Current
        {
            get
            {
                return _colors[_position];
            }
        }

        bool System.Collections.IEnumerator.MoveNext()
        {
            _position++;
            return (_position < _colors.Length);
        }

        void System.Collections.IEnumerator.Reset()
        {
            _position = -1;
        }
    }
}

// Element class.
public class Color
{
    public string Name { get; set; }
}
```

## Sorting a Collection
The example sorts instances of the ```Car``` class that are stored in a ```List<T>``` The ```Car``` class implements the ```IComparable<T>``` interface, which requires that the ```CompareTo``` method be implemented.

Each call to the ```CompareTo``` method makes a single comparison that is used for sorting. User-written code in the ```CompareTo```     method returns a value for each comparison of the current object with another object. The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal. This enables you to define in code the criteria for greater than, less than, and equal.

In the ```ListCars``` method, the ```cars.Sort()``` statement sorts the list. This call to the Sort method of the ```List<T>``` causes the ```CompareTo``` method to be called automatically for the Car objects in the List.

```c#
private static void ListCars()
{
    var cars = new List<Car>
    {
        { new Car() { Name = "car1", Color = "blue", Speed = 20}},
        { new Car() { Name = "car2", Color = "red", Speed = 50}},
        { new Car() { Name = "car3", Color = "green", Speed = 10}},
        { new Car() { Name = "car4", Color = "blue", Speed = 50}},
        { new Car() { Name = "car5", Color = "blue", Speed = 30}},
        { new Car() { Name = "car6", Color = "red", Speed = 60}},
        { new Car() { Name = "car7", Color = "green", Speed = 50}}
    };

    // Sort the cars by color alphabetically, and then by speed
    // in descending order.
    cars.Sort();

    // View all of the cars.
    foreach (Car thisCar in cars)
    {
        Console.Write(thisCar.Color.PadRight(5) + " ");
        Console.Write(thisCar.Speed.ToString() + " ");
        Console.Write(thisCar.Name);
        Console.WriteLine();
    }

    // Output:
    //  blue  50 car4
    //  blue  30 car5
    //  blue  20 car1
    //  green 50 car7
    //  green 10 car3
    //  red   60 car6
    //  red   50 car2
}

public class Car : IComparable<Car>
{
    public string Name { get; set; }
    public int Speed { get; set; }
    public string Color { get; set; }

    public int CompareTo(Car other)
    {
        // A call to this method makes a single comparison that is
        // used for sorting.

        // Determine the relative order of the objects being compared.
        // Sort by color alphabetically, and then by speed in
        // descending order.

        // Compare the colors.
        int compare;
        compare = String.Compare(this.Color, other.Color, true);

        // If the colors are the same, compare the speeds.
        if (compare == 0)
        {
            compare = this.Speed.CompareTo(other.Speed);

            // Use descending order for speed.
            compare = -compare;
        }

        return compare;
    }
}
```

## Iterators
An *iterator* is used to perform a custom iteration over a collection. An iterator can be a method or a ```get``` accessor. An iterator uses a ```yield return``` statement to return each element of the collection one at a time.

You call an iterator by using a ```foreach``` statement. Each iteration of the foreach loop calls the iterator. When a yield return statement is reached in the iterator, an expression is returned, and the current location in code is retained. Execution is restarted from that location the next time that the iterator is called.

The following example uses an iterator method. The iterator method has a ```yield return``` statement that is inside a ```for``` loop. In the ```ListEvenNumbers``` method, each iteration of the foreach statement body creates a call to the iterator method, which proceeds to the next ```yield return``` statement.

```c#
private static void ListEvenNumbers()
{
    foreach (int number in EvenSequence(5, 18))
    {
        Console.Write(number.ToString() + " ");
    }
    Console.WriteLine();
    // Output: 6 8 10 12 14 16 18
}

private static IEnumerable<int> EvenSequence(
    int firstNumber, int lastNumber)
{
    // Yield even numbers in the range.
    for (var number = firstNumber; number <= lastNumber; number++)
    {
        if (number % 2 == 0)
        {
            yield return number;
        }
    }
}
```