---
layout: post
title:      "JavaScript Promise and Async/Await"
date:       2018-05-16 03:50:47 +0000
permalink:  javascript_promise_and_async_await
---

### Promise

Promise is a promise for a future value. It is in 1 of 3 states:

- Pending: not yet fulfilled or rejected
- Fulfilled: operation completed successfully
- Rejected: operation failed

A Promise is created using the new Promise constructor. 

```
let getData = new Promise((resolve, reject) => {
  setTimeout(function(){
    resolve(“Success!”);
  }, 1000);
});
```

If everything is successful, the promise is fulfilled by calling `resolve()` else if there is an error, `reject()` is called.

When using Promises, it has a method called `then()`, which accepts a function that will be invoked when the promise has been fulfilled. There is also a `catch()` function  which can be used to handle promise rejection.

```
getData.then(message) => {
  console.log(message + “ has been received”);
}).catch((error) => {
  console.log(“Error occurred”, error);
});
```

### Async/Await

Async/Await statements are built on top of promises. Async declares an asynchronous function and returns a Promise when it is called. The keyword async is placed before a function.

```
async function two() {
  return 2;
}
```

Await only works inside async functions. It is used to wait for a promise to be fulfilled. Errors are handled using `try/catch` block. 

```
async function doSomething() {
  try {
    let result = await asyncCall();
    console.log(result);
  }
  catch(error) {
    //error will be caught here
    console.log(error);
  }
}
```

Using async/await allows us to write code that runs asynchronously but looks synchronous. This is nice because the code is easier to read. 

