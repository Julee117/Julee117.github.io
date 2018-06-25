---
layout: post
title:      "Selection Sort"
date:       2018-06-25 01:00:38 +0000
permalink:  selection_sort
---


In selection sort, we are going to iterate through the elements in the array starting at `i = 0`. We are going to assume that the element at `i` has the lowest value and set `i` to the variable `indexOfMin`. We are going create an inner `for` loop to iterate from `i + 1` to the end of the array to see if there is an element with a lower value. If there is, we would update the value of `indexOfMin`. After we get to the last element in the inner loop, we see if the index of the current element and `indexOfMin` is the same. If they are not, we swap them. 

```
function selectionSort(arr) {
  for (let i = 0; i < arr.length; i++) {
    let indexOfMin = i;

    for (let j = i + 1; j < arr.length; j++) {
      if (arr[j] < arr[indexOfMin]) {
        indexOfMin = j;
      }
    }

    if (indexOfMin !== i) {
      let smallerNum = arr[indexOfMin];
      arr[indexOfMin] = arr[i];
      arr[i] = smallerNum;
    }
  }
  return arr;
}
```
