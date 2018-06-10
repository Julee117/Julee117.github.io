---
layout: post
title:      "Spiral Matrix"
date:       2018-06-10 21:18:08 +0000
permalink:  spiral_matrix
---

Given an integer N, return a N x N spiral matrix.

For example, N = 4 

The output should be:

```
[
 [1, 2, 3, 4],
 [12, 13, 14, 5],
 [11, 16, 15, 6],
 [10, 9, 8, 7]
]
```

We are going to start from the number 1 and go around clockwise in a spiral fashion. The last number we will print is N^2. In this example where N is 4, the last number is 16. 

First, we need to create an empty array of N amount of subarrays.

```
function matrix(n) {
  const results = [];
  for (let i = 0; i < n; i++) {
    results.push([]);
  }
}
```

If we return results, the output would be: `[[], [], [], []]`.

We are going to create variables to keep track of counter, start column, end column, start row and end row. We are also going to create a `while` loop and a `for` loop from start column to end column to assign values for the top row:

```
function matrix(n) {
  const results = [];
  for (let i = 0; i < n; i++) {
    results.push([]);
  }

  let counter = 1;
  let startColumn = 0;
  let endColumn = n – 1;
  let startRow = 0;
  let endRow = n – 1; 

  while (startColumn <= endColumn && startRow <= endRow) {
    //Top row – going from left to right
    for (let i = startColumn; i <= endColumn; i++) {
      results[startRow][i] = counter;
      counter++;
    }
    startRow++;
}
```

We will create a for loop and iterate from start row to end row to assign values to the right column:

```
…
  //Right column – going from up to down
  for (let i = startRow; i <= endRow; i++) {
    results[i][endColumn] = counter;
    counter++;
  }
  endColumn--;
```

We are going to assign the values for the bottom row by iterating from the end column down to start column. 

```
…
  //Bottom row – going from right to left
  for (let i = endColumn; i >= startColumn; i--) {
    results[endRow][i] = counter;
    counter++;
  }
  endRow--;
```

Next, we are going to iterate from end row down to start row to assign values on left column:

```
…
  //Left column – going from down to up
  for (let i = endRow; i >= startRow; i--) {
    results[i][startColumn] = counter;
    counter++;
  }
  startColumn++;
```

Here is the code put together:

```
function matrix(n) {
  const results = [];
  for (let i = 0; i < n; i++) {
    results.push([]);
  }

  let counter = 1;
  let startColumn = 0;
  let endColumn = n – 1;
  let startRow = 0;
  let endRow = n – 1; 

  while (startColumn <= endColumn && startRow <= endRow) {
    //Top row
    for (let i = startColumn; i <= endColumn; i++) {
      results[startRow][i] = counter;
      counter++;
    }
    startRow++;

    //Right column
    for (let i = startRow; i <= endRow; i++) {
      results[i][endColumn] = counter;
      counter++;
    }
    endColumn--;

    //Bottom row
    for (let i = endColumn; i >= startColumn; i--) {
      results[endRow][i] = counter;
      counter++;
    }
    endRow--;

    //Left column
    for (let i = endRow; i >= startRow; i--) {
      results[i][startColumn] = counter;
      counter++;
    }
    startColumn++;
  }
  return results;
}
```

The `while`loop would execute again if the conditions are met and execute through the `for` loops. If not, we would exit out of the `while` loop and return the results.


