---
layout: post
title:      "Binary Search Tree"
date:       2018-05-29 16:20:01 +0000
permalink:  binary_search_tree
---


A Binary Search tree is a tree data structure. There is a root node. The node can have at most two children. Each left child has a value that is less than the parent’s value and each right child has a value greater to the parent’s value. I will be going over a few methods such as `add(data)`, `findMinNode()`, `findMaxNode()` and `search(value)`.

In order to create a tree, we need a node. Here is an example of a Node class:

```
class Node {
  constructor(data) {
    this.data = data;
    this.left = null;
    this.right = null;
  }
}

```

We will create a Binary Search Tree class:

```
class BinarySearchTree {
  constructor() {
    this.root = null;
  }
}

```

We are going to create an add method to add value to the binary search tree. If there is no root, the root would be set to the new value. If the value is less than the currentNode's value, we would go left until there is no left node. The new value becomes the left node. If the value is greater than the currentNode's value, we would go right until there is no right node and the new value becomes the right node.

```
add(data) {
  if (!this.root) {
    this.root = new Node(data);
    return;
  }

  let currentNode = this.root;
  while (currentNode) {
    if (data < currentNode.data) {
      if (!currentNode.left) {
        currentNode.left = new Node(data);
        return;
      } else {
        currentNode = currentNode.left;
      }
    } else { 
      if (!currentNode.right) {
        currentNode.right = new Node(data);
        return;
      } else {
        currentNode = currentNode.right;
      }
    }
  }
}
```

We are going to find the node with the minimum value by going through the left nodes:

```
findMinNode() {
  let current = this.root;
  while (current.left !== null) { 
    current = current.left;
  } 
  return current.data;
}
```

We are going to find the node with the maximum value by going through the right nodes:

```
findMaxNode() {
  let current = this.root;
  while (current.right !== null) {
    current = current.right;
  }
  return current.data;
}
```

We will search for the node with the specified value:

```
search(value) {
  let current = this.root;
  if (current.data === value) {
    return current;
  } else if (value < current.data && current.left !== null) {
    current.left.search(value);
  } else if (value > current.data && current.right !== null) {
    current.right.search(value);
  }
  return null;
}
```
