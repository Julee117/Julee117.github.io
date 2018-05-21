---
layout: post
title:      "Linked List"
date:       2018-05-21 21:43:08 +0000
permalink:  linked_list
---


A linked list is a linked list of nodes. The head is the first node in the list and the tail is the last one. The data contained in the node can be a string, a number, an array or an object. In a singly-linked list, the nodes each have one pointer to the next node. 

Here is a node class:

```
class Node {
  constructor (data, next=null) {
    this.data = data;
    this.next = next;
  }
}

const nodeOne = new Node(12) 
nodeOne.data  // 12
nodeOne.next  // null 
const nodeTwo = new Node(5, nodeOne) 
nodeTwo.next  // returns nodeOne
```

Linked list constructor:

```
class LinkedList {
  constructor() {
    this.head = null;
  }
}
```

We can create a new Node and insert it as the first item in the list by having it point to the previous head:

```
insertFirst(data) {
  this.head = new Node(data, this.head); 
}
```

We can return the first node:

```
getFirstNode() {
  return this.head;
}
```

We can return the last node. If the list is empty, we will return null. If it is not, we will iterate through the list. If `node.next` does not exist, it means that we are at the end of the list and will return the current node.

```
getLastNode() {
  if (!this.head) {
    return null;
  }
  let node = this.head;
  while (node) {
    if (!node.next) {
      return node;
    }
    node = node.next
  }
}
```

We can go through the list and add the new item after the last node. We will utilize the `getLastNode()` method to retrieve the last node and have it point to the new item. If the list is empty, we will set the new item to the head property.

```
insertLast(data) {
  const last = this.getLastNode();
  if (last) {
    last.next = new Node(data);
  } else {
    this.head = new Node(data);
  }
}
```

We can remove the first node where the list’s head is now the second element.

```
removeFirstNode() {
  if (!this.head) {
    return;
  }
  this.head = this.head.next;
}
```

We can also remove the last node.

```
removeLastNode() {
  if (!this.head) {
    return;
  }
  if (!this.head.next) {
    this.head = null;
    return;
  }
  let previous = this.head;
  let node = this.head.next;
  while (node.next) {
    previous = node;
    node = node.next;
  }
  previous.next = null;
}
```

### Advantages of linked lists:

Linked lists require constant time when inserting and deleting nodes from any position by just changing the pointers. Arrays require O(n) time to insert and delete because we would have to move each element over 1 index. Linked lists also have no fixed size while arrays usually do.  

### Disadvantage of linked lists:

It requires O(n) time to retrieve an element by an index since each node can live at any address and we need to visit each node to see where the next node lives. Arrays on the other hand require constant time when retrieving an element. 

There are other kinds of linked lists such as doubly linked list where each node keeps a pointer to the next node and the previous one. There is the circular linked list where the last node's pointer points to the first node. 



