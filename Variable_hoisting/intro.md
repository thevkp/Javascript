## Variable hoisting

`var`-declared variables are hoisted, meaning you can refer to the variable anywhere in its scope, even if its declaration isn't reached yet. You can see `var` declarations as being "lifted" to the top of its function or global scope. However, if you access a variable before it's declared, the value is always `undefined`, because only its declaration and default initialization (with `undefine`) is hoisted, but not its value assignment.

```
console.lof(x); // undefiend
console.log(x === undefined); // true
var x = 3;

(function () {
  console.log(x); // undefined
  var x = "local value";
})
```

Whether `let` and `const` are hoisted is a matter of definition debate. Referencing the variable in the block before the variable declaration always results in a `ReferenceError`, because the variable is in a "__temporal dead zone__" fromt the start of the block until the declaration is processed.

```
console.log(x); // ReferenceError
const x = 3;

console.log(y); // ReferenceError
```

# Important Notes
- Unlike var declarations, which only hoist the declaration but not its value, function declarations are hoisted entirely — you can safely call the function anywhere in its scope. See the hoisting glossary entry for more discussion.

## Temporal Dead Zone:
- A variable declared with `let`, `const`, or `class` is said to be in a "temporal dead zone" (TDZ) from the start of the block until code execution reaches the place where the variable is declared and initialized.
- While inside the TDZ, the variable has not been initialized with a value, and any attempt to access it will result in a ReferenceError. The variable is initialized with a value when execution reaches the place in the code where it was declared. If no initial value was specified with the variable declaration, it will be initialized with a value of undefined.


```
{
  // TDZ starts at beginning of scope
  console.log(bar); // "undefined"
  console.log(foo); // ReferenceError: Cannot access 'foo' before initialization
  var bar = 1;
  let foo = 2; // End of TDZ (for foo)
}
```

- The term "temporal" is used because the zone depends on the order of execution (time) rather than the order in which the code is written (position). For example, the code below works because, even though the function that uses the `let` variable appears before the variable is declared, the function is called outside the TDZ.

```
{
  // TDZ starts at beginning of scope
  const func = () => console.log(letVar); // OK

  // Within the TDZ letVar access throws `ReferenceError`

  let letVar = 3; // End of TDZ (for letVar)
  func(); // Called outside TDZ!
}
```

## Redeclarations
- `let` declarations cannot be in the same scope as any other declaration, including `let`, `const`, `class`, `function`, `var`, and `import` declaration.

```
{
  let foo;
  let foo; // SyntaxError: Identifier 'foo' has already been declared
}

```

- A `let` declaration within a function's body cannot have the same name as a parameter. A `let` declaration within a `catch` block cannot have the same name as the catch-bound identifier.

```
function foo(a) {
  let a = 1; // SyntaxError: Identifier 'a' has already been declared
}

try{
}
catch (e) {
  let e; //SyntaxError: identifier 'e' has already been declared
}
```

## Redclaration and `switch` case
- You may encounter errors in `switch` statements because there is only one block.

```
let x = 1;

switch (x) {
  case 0:
    let foo;
    break;
  case 1:
    let foo; // SyntaxErro: Identifier 'foo' has already been declared
    break;
}
```

To avoid the error, wrap each case in a new block statement.

```
let x = 1;

switch(x) {
  case 0: {
    let foo;
    break;
  }
  case 1: {
    let foo;
    break;
  }
}

```