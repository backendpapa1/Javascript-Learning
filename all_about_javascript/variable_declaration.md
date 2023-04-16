# Variable Declaration


## Var 

The var statement declares a variable in a  function-scoped or globally-scope optionally initializing it to a value. No initialization leads to `undefined`

```js
var x = 1;

if (x === 1) {
  var x = 2;

  console.log(x);
  // Expected output: 2
}

console.log(x);
// Expected output: 2

```


Variables can be created from destructuring an object or array;

```js
var { bar } = foo; // where foo = { bar:10, baz:12 };
/* This creates a variable with the name 'bar', which has a value of 10 */

```

`Var` declarations, wherever they occur, are processed before any code is executed. This is called `hoisting`.

The scope of a variable declared with var is its current execution context and closures thereof, which is either the enclosing function and functions declared within it, or, for variables declared outside any function, global. Duplicate variable declarations using var will not trigger an error, even in strict mode, and the variable will not lose its value, unless another assignment is performed.

```js
function foo() {
  var x = 1;
  function bar() {
    var y = 2;
    console.log(x); // 1 (function `bar` closes over `x`)
    console.log(y); // 2 (`y` is in scope)
  }
  bar();
  console.log(x); // 1 (`x` is in scope)
  console.log(y); // ReferenceError, `y` is scoped to `bar`
}

foo();


```

`Variables declared using var are created before any code is executed` in a process known as hoisting. Their initial value is undefined.
```js
console.log(x); // undefined (note: not ReferenceError)
console.log("still going..."); // still going...
var x = 1;
console.log(x); // 1
console.log("still going..."); // still going...
```


```js
foo = "f"; // In non-strict mode, assumes you want to create a property named `foo` on the global object
Object.hasOwn(globalThis, "foo"); // true
```

### Var Hoisting
Because var declarations are processed before any code is executed, declaring a variable anywhere in the code is equivalent to declaring it at the top.

```js

bla = 2;
var bla;

```

 IS INTERPRETED AS

```js
var bla;
bla = 2;
```

**NOTE:** It's important to point out that only a variable's declaration is hoisted, not its initialization. The initialization happens only when the assignment statement is reached. Until then the variable remains undefined (but declared):

```js
function do_something() {
  console.log(bar); // undefined
  var bar = 111;
  console.log(bar); // 111
}

```
 IS INTERPRETED AS
 
 ```js
 function do_something() {
  var bar;
  console.log(bar); // undefined
  bar = 111;
  console.log(bar); // 111
}

```

```js
var a = 0,
  b = 0;

// Assigning two variables with single string value
var a, b = a = 'A';

var x = y,
  y = "A";
console.log(x + y); // undefinedA
// x is yet to be initialized

```

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var



