# Queue
### First In First Out, Last In Last Out

Common terminology for a queue is

- **Enqueue** Nodes or items that are added to the queue.
- **Dequeue** Nodes or items that are removed from the queue. If called when the queue is empty an exception will be raised.
- **Front** This is the front/first Node of the queue.
- **Rear** This is the rear/last Node of the queue.
- **Peek** When you peek you will view the value of the front Node in the queue. If called when the queue is empty an exception will be raised.
- **IsEmpty** returns true when queue is empty otherwise returns false.

### Enqueue O(1)
When you add an item to a queue, you use the enqueue action. This is done with an O(1) operation in time because it does not matter how many other items live in the queue (n); it takes the same amount of time to perform the operation.

```
ALGORITHM enqueue(value)
// INPUT <-- value to add to queue (will be wrapped in Node internally)
// OUTPUT <-- none
   node = new Node(value)
   rear.next <-- node
   rear <-- node
```

### Dequeue O(1)
When you remove an item from a queue, you use the dequeue action. This is done with an O(1) operation in time because it doesn’t matter how many other items are in the queue, you are always just removing the front Node of the queue.

```
ALGORITHM dequeue()
// INPUT <-- none
// OUTPUT <-- value of the removed Node
// EXCEPTION if queue is empty

   Node temp <-- front
   front <-- front.next
   temp.next <-- null

   return temp.value
```

### Peek O(1)
When conducting a peek, you will only be inspecting the front Node of the queue.

```
ALGORITHM peek()
// INPUT <-- none
// OUTPUT <-- value of the front Node in Queue
// EXCEPTION if Queue is empty

   return front.value
```

### IsEmpty O(1)

```
ALGORITHM isEmpty()
// INPUT <-- none
// OUTPUT <-- boolean

return front = NULL
```