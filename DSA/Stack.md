# Stack
### First In Last Out, Last In First Out

A stack is a data structure that consists of Nodes. Each Node references the next Node in the stack, and it has a pointer references to last Node added.

Common terminology for a stack is

- **Push** Nodes or items that are put into the stack.
- **Pop** Nodes or items that are removed from the stack. When you attempt to pop an empty stack an exception will be raised.
- **Top** This is the top of the stack.
- **Peek** When you peek you will view the value of the top Node in the stack. When you attempt to peek an empty stack an exception will be raised.
- **IsEmpty** returns true when stack is empty otherwise returns false.

### Push O(1)
Pushing a Node onto a stack will always be an O(1) operation. This is because it takes the same amount of time no matter how many Nodes (n) you have in the stack.

```
ALOGORITHM push(value)
// INPUT <-- value to add, wrapped in Node internally
// OUTPUT <-- none
   node = new Node(value)
   node.next <-- Top
   top <-- Node
```

### Pop O(1)
Popping a Node off a stack is the action of removing a Node from the top. When conducting a pop, the top Node will be re-assigned to the Node that lives below and the top Node is returned to the user.

```
ALGORITHM pop()
// INPUT <-- No input
// OUTPUT <-- value of top Node in stack
// EXCEPTION if stack is empty

   Node temp <-- top
   top <-- top.next
   temp.next <-- null
   return temp.value
```

### Peek O(1)
When conducting a peek, you will only be inspecting the top Node of the stack.

```
ALGORITHM peek()
// INPUT <-- none
// OUTPUT <-- value of top Node in stack
// EXCEPTION if stack is empty

   return top.value
```

### IsEmpty O(1)

```
ALGORITHM isEmpty()
// INPUT <-- none
// OUTPUT <-- boolean

return top = NULL
```