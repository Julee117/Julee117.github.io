---
layout: post
title:      "Scope, Hoisting & this"
date:       2018-02-17 01:15:35 -0500
permalink:  scope_hoisting_and_this
---


I realize that I need to slow down a bit and really try to understand JavaScript. I would read through the lessons and think that I understood the concepts but really I did not. I will be discussing scope, hoisting and `this`. 

### Scope

Scope is where declared variables and methods are available within our code. Scopes can be defined globally or locally.

```
// Global Scope out here
function myFunction() {
  const foo = "Hello World"; // Local Scope in here
}
```

`myFunction`  is declared in the global scope and is available everywhere in your code. 

Each function that is defined has its own local scope. 

```
//Global Scope
function myFunction() {
  // Local Scope A
	function anotherFunction() {
	  // Local Scope B
  }
} 
```


### Block Scope

Variables declared with `const` and `let` are block scoped so they are only available inside the block. You cannot retrieve its value outside of the block. Variables declared with `var` are not block scoped and are accessible outside of the block. 

```
if (true) {
  const myVar = 2;
  let otherVar = 10;
}

myVar;  // ReferenceError: myVar is not defined 
otherVar;  // ReferenceError: otherVar is not defined

if (true) {
  var foo = 5;
}

foo;  // 5
```


### Lexical Scope

Whenever you see a function within another function, the inner function has access to the scope in the outer function.

Here is an example to illustrate this:

```
function a() {
  function b() {
	  console.log(num);
	}
	const num = 10;
	b();
}

a();  // 10
```


### Hoisting


```
b();

function b() { 
  console.log('Called b');
}
```

This would return 'Called b'.

```
console.log(a);
var a = 'Hello World'
```

I assumed this would return “Hello World’ just like how it worked as the example above but it actually returns `undefined`.

The JavaScript engine goes through two phases: compilation phase and execution phase. In the compilation phase, it sets the memory space for the variables and functions. The function in its entirety is placed into memory space. However, for variables, the engine does not know what their values would be until it starts executing the code. It instead puts a placeholder called `undefined`. In the execution phase, it is where it executes your code line by line. This is when the variable is assigned to its value. 

So, in the first line of this code, the identifier `a` is stored in memory as undefined during the compilation phase. The execution phase begins and steps through the code line by line. In the first line, `console.log(a);`, the value of `a` is still `undefined` and is what gets logged out to the console. In the second line, ‘Hello World’ is assigned to the variable `a`. From here on, all references to `a` in this scope will be ‘Hello World’.

However, we get a different outcome when using `const` and `let` vs `var`. 

```
function superhero() {
  console.log(marvel);  // ReferenceError: marvel is not defined
  console.log(dc);  // ReferenceError: dc is not defined
  let marvel = 'spiderman';
  const dc = 'batman';
}
```

Here, we get a `ReferenceError` as our output. `Var` is initialized with `undefined` but `const` and `let` remain uninitialized until their statements are run.

### this

It is important to know that `this` does not refer to the function itself.

```
let myFunc = function() {
  console.log(this)
}

myFunc();
```

The value of this is the `window` Object – the global scope. 

If `this` is referenced inside a method, it equals the object that received the method call. Method is a function that is associated with an object. 

```
let person = {
  first: 'Ada',
  last: 'Lovelace',
  greet: 'function() { 
	  console.log(this)
  }
}

person.full();  // Object {first: 'Ada', last: 'Lovelace', greet: function}
```

When we call constructor functions with the `new` keyword, `this` is bound to the new object being created. 

```
function User(name, age) {
  this.name = name
  this.age = age
}

let peter = new User('peter', 25)
console.log(peter);  // User{name: "peter", age: 25}
```

The value of `this` can also be set explicitly with `call()`, `bind()` and `apply()`.  `Call` and `apply` are each invoked immediately. The difference between `call` and `apply` is the way you pass arguments.  In `call`, `this` is the first argument followed by additional arguments. `Apply` only take two arguments: `this` and an array of arguments.

```
let names = {a: 'Sara', b: 'Dave'};

function myFunc(foodOne, foodTwo) {
  console.log(`${this.a} and ${this.b} want to eat ${foodOne} and ${foodTwo}`);
}

myFunc.call(names, 'cookies', 'cake');  // Sara and Dave want to eat cookes and cake
myFunc.apply(names, ['ice cream', 'candy']);  // Sara and Dave want to eat ice cream and candy
```

`Bind` is similar to `call` where `this` is the first argument followed by additional arguments but `bind` is not invoked immediately. `Bind` returns a function with the context of this bound already. 

```
let cooper = {name: 'Cooper'}

function myFunc(person) {
  console.log(`${person} named her puppy ${this.name}`);
}

let newFunc = myFunc.bind(cooper);
newFunc('Jill');  // Jill named her puppy Cooper
```

I have a better understanding now of these concepts after reading books, blogs and looking at various examples. There is definitely more to explore in JavaScript which I will continue to do so. 






