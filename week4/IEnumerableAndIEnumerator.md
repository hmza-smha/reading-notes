# IEnumerable & IEnumerator

### The IEnumerable interface is the base interface for many collections in c#, and its job is to provide a way of iteration through a collection.

### Anything that you can iterate over *(Array, List, ...)* in .NET implements IEnumerable

- In Simple words, when a collection class implements the IEnumerable interface it becomes countable.
> Collections are classes that we can use to store a collection of Objects.

IEnumerable interface contains a single method that you must implement, this method is GetEnumerator(), which return an IEnumerator object.

The returned IEnumerator object provides the ability to iterate through the collection by exposing the Current properity that points at the object we are currently at in the collection.

```c#
// How foreach actully works?
var array = new int[] {1,2,3,4,5,6};
var enumerator = array.GetEnumerator();
While(enumerator.NextMove()){
    Consoel.WriteLine(enumerator.Current);
}
```

```c#
//return defferent IEnumerable rtypes

IEnumerable<int> GetCollection(int option){

    List<int> list = new List<int>(){1,2,3,4,5,6,7,8,9};
    Stack<int> stack = new Stack<int>(){1,2,3,4,5,6,7,8,9};
    Queue<int> q = new Queue<int>(){1,2,3,4,5,6,7,8,9};

    switch(option){
        case 1: 
            return list;
        case 2:
            return stack;
        case 3: 
            return q;
        default
            throw new Exception("Invalid Input!");
    }
}
```


For a list, the most basic and famous solution is the ```for``` loop. We can use a local integer variable to keep track of the current position of the element in a list.

```c#
for (int i = 0; i < 5; i++) {
   object current = myList[i]
}
```

One drawback of the ```for``` look is that it only works for the collection that can be indexed, such as an array or list. There are many other data structures that don’t have indexes, like a ```binary tree```.

Even with an indexed list or array, what about if they are infinite or the size are unknown?

## Why Can’t The Collection Manage Its Own Traversal
Instead of using the index to traverse the collection, which is limited to the kind of data structure. We probably can use an interval private pointer which is stored inside the class itself to keep track of the current element. This class might also have some additional methods to help for the traversal.


## .NET Iterator Design Pattern Implementation
We assume that a class includes a collection of elements, and other properties or methods. Instead of use the collection itself, we define another object to take the responsibility for traversal. This specialised object is only responsible to traverse the collection in a particular way.
For instance, this specialised object might contain a pointer to keep track of the current element, and possibly some other methods to implement the traversal logic.


the iterator pattern is already supported by using **two interface types** of the ```System.Collections``` namespace.

- **IEnumerator**: *the exact specialised object responsible for the traversal*

```c#
public interface IEnumerator
{
    object Current
    {
        get;
    }
    bool MoveNext();
    void Reset();
}
```

- **IEnumberable**: *a data structure which can be traversed*

```c#
public interface IEnumerable
{
   IEnumerator GetEnumerator();
}
```

## How IEnumerator Works
The ```IEnumerator``` interface is really the essence of the pattern, which defines the simplest possible way to traverse over a data structure. An enumerator object holds the ```Current``` item in the traversal process. And when you tell it to move to the next item by using the ```MoveNext``` bool flag, the ```Current``` will point to the next element. When we have run out of items to continue (reached to the last one in the collection), the ```MoveNext``` would become false.

We can notice that the ```IEnumerator``` interface makes no assumptions at all about the data structure, internally detailed implementations or the size of the collections. It’s perhaps the purest notion of a ‘sequence’ I can think of.

If a collection or sequence includes an enumerator, theoretically we can iterate over any kind of aggregate data structure. This this where the ```IEnumberable``` interface comes into play.

## What Is IEnumerable
The ```IEnumerable``` interface defines a standardised way to get an enumerator object. In order to get an instance of an enumerator, all the collection or sequence class needs to implement the ```IEnumerable``` interface and provides its own implementation about how the enumerator should look like.

So, for an enumerable object, you can always call the ```GetEnumerator()``` to get a nice enumerator object which you can use to traverse the object’s elements.

In .NET, all collections types have implemented the ```IEnumerable``` interface, and even the ```String``` class.


## How to use them ?

```c#
string firstame = "Colton";
IEnumerator firstNameEnumerator = firstame.GetEnumerator();
while (firstNameEnumerator.MoveNext())
{
    Console.WriteLine(firstNameEnumerator.Current);
}
```

### C# Language Support
It enumerator design pattern is quite simple which is just obtaining the enumerator from the class and call the MoveNext in a loop. The enumerator object takes the full responsibility of the traversal. As this usage pattern is so common that C# language formalise it with a foreach keyword, which is a purely syntactic sugar.

The following code is identical to the previous example.

```c#
string firstame = "Colton";

foreach (char s in firstame)
{
    Console.WriteLine(s);
}
```

The C# compiler will simply compile the foreach syntax to the exact same code (intermediate language) with the previous example

### Conclusion
All in all, understanding where the enumerator design pattern comes from is very useful. I hope this has been informative and you found what you are looking for.