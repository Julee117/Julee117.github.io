---
layout: post
title:      "Implement a Queue with Two Stacks"
date:       2018-06-19 02:25:54 +0000
permalink:  implement_a_queue_with_two_stacks
---


I will be going over an interview question on how to implement a queue using two stacks.  For example, if we push “a”, “b”, “c” to a stack, and we want to implement a queue, we call the dequeue method three times to have the elements come out in the order of “a”, “b”, “c”. 

A stack stores items in a last-in, first-out (LIFO) order. An example of this is a deck of cards where we remove the card from the top of the deck. 

A queue stores items in a first-in, first-out (FIFO) order. You can think of it like waiting on line. The first person on the line is the first one served. 

Adding an item to the queue is known as enqueue and removing the item from the front of the queue is known as dequeue.

```
class QueueWithTwoStacks {
  constructor() {
    this.stackIn = [];
    this.stackOut = []; 
  }

  enqueue(item) {
    this.stackIn.push(item);
  }

  dequeue() {
    if (this.stackOut.length === 0) {
      while (this.stackIn.length > 0) {
        const newItem = this.stackIn.pop();
        this.stackOut.push(newItem);  // This moves items from stackIn to stackOut and reverses the items
      }

      if (this.stackOut.length === 0) {
        throw new Error(“Can’t dequeue from an empty queue”);
      }
    }
    return this.stackOut.pop();
  }
}
```

