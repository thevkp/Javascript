**The `var` statement declares function-scoped or globally scoped variables, optionally initializing each to a value.**

> Demo: var statement
```js
var x = 1;

if (x == 1) {
  var x = 2;
  console.log(x); // Exp output: 2
}

console.log(x);
// expected output: 2
```
- __Note:__ `var` in `if` block updates the `var` the outside the top `var`("a behavior of globally scoped variables)
- If var was not declared outside the top of `if` block then `console.log(x)` outside the `if` block will give `ReferenceError`.
- Redeclaration is a property of `var` variables. `let` and `const` variables do not support redeclaration.
- `var` is declared outside any function -> it's __global__, not function scoped. So it's accessible everywhere.


## Function Scoped
```js
function greet() {
  var name = "Alice";
  console.log(name); // "Alice"
}

greet();
console.log(name); // ReferenceError: name is not defined
```

- `name` exists only inside `greet()`
- Outside the `greet()` function, it doesn't exist.

### Misleading Example(Not inside a Function)
```js
var foo = "hello"; Global Scope

function sayHi() {
  console.log(foo); // Works: because foo is global
}

sayHi();
console.log(foo); // Works here too: still global;
```
- If some `foo` is updated inside `sayHi()`, the effects will be global.

### What if `var` is Inside a Block, Like `if`?
```js
if (true) {
  var test = "block scoped?";
}
console.log(test); "block scoped"
```

- You might expect this to fail, but it doesn't.
- That's because `var` is not block scoped, only function scoped.
- Blocks like `if`, `for`, `while`, `{}` don't create new scope for `var`.

- So if `var` is blocked scoped, it's hoisted to functio/global scope.


# Important Note
- Other block constructs, including `bloc statements`, `try...catch`, `switch`, headers of one of the `for` statements, do not create scope for `var`, and variables declared with `var` inside such a block can continue to be referenced outside the block.
```js
for (var a of [1, 2, 3]);
console.log(a); // 3
```

## Hoisting
`var` declarations, wherever they occur in a script, are processed before any code within the script is executed. Declaring a variable anywhere in the code is equivalent to declared it at the top. This also means that a variable can appear to be used before it's declared. This behavior is called ___hoisting___, as it appears that the variable declaration is moved to the top of the function, static initialization block, or script source in which it occurs.

- Only a variable's declaration is hoisted, not its initialization. The initialization happens only when the assignment statement is reached. Until then the variable remains `undefined`(but declared)