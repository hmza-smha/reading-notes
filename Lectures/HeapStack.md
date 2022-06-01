# Heap & Stack

Both the *stack* and *heap* help us run our code. They reside in the operating memory on our machine and contain the pieces of information we need to make it all happen.

## What's the difference between Stack & Heap?

The ***Stack*** is more or less responsible for keeping track of what's executing in our code (or what's been "called").
The ***Heap*** is more or less responsible for keeping track of our objects.

The ***Stack*** is LIFO of excution (keep track of excution).
The ***Heap*** holding information (not keep track of execution most of the time) so anything in our Heap can be accessed at any time.

The ***Stack*** is self-maintaining, meaning that it basically takes care of its own memory management.  When the top element is no longer used, it's thrown out.
The ***Heap***, has to worry about *Garbage collection (GC)*, which deals with how to keep the Heap clean.

<br>

***
[GarbageCollection](./GarbageCollection.md)
