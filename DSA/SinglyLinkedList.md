# Singly Linked List

A Linked List is a sequence of **Nodes** that are connected/linked to each other by a **Pointer**.

## A Vary Simple Linked List

```c#

class Node{
    int _data;
    Node _Next;

    Node(int data){
        _data = data;
    }
}

class LinkedList{
    Node Head;
}

class Program{
    public static void main(String[] args){

        Node head = new Node(0);
        Node n1 = new Node(1);
        Node n2 = new Node(2);
        Node n3 = new Node(3);

        // Head -> n1 -> n2 -> n3 -> null
        head.Next = n1;
        n1.Next = n2;
        n2.Next = 23;
        

    }
}

```

## Traversing Linked List *Big O(n)*

When traversing a linked list, you are not able to use a foreach or for loop. We depend on the Next value in each node to guide us where the next reference is pointing.

The best way to approach a traversal is through the use of a ```while()``` loop. This allows us to continually check that the Next node in the list is not ```null```. If we accidentally end up trying to traverse on a node that is ```null```, a ```NullReferenceException``` gets thrown and our program will crash/end.

```
ALGORITHM Includes (value)
// INPUT <-- integer value
// OUTPUT <-- boolean

  Current <-- Head

  WHILE Current is not NULL
    IF Current.Value is equal to value
      return TRUE

    Current <-- Current.Next

  return FALSE
```

## Adding At the begining *Big O(1)*

```
ALGORITHM Add(newValue)
// INPUT <-- Value to add
// OUTPUT <-- No output

  newNode <-- NEW Node
  newNode.Value <-- newValue
  newNode.Next <-- Head
  Head <-- newNode
```