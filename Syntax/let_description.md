# `let` variables
The `let` declaration declares re-assignable, block-scoped local variables, optionally initializing each to a value.

> # Demo: `let` declaration
```js
let x = 1;

if (x === 1) {
  let x = 2;

  console.log(x);  // 2
}

console.log(x); // 1
```

### Description
The scope of a variable declared with `let` is one of the following curly-brace-enclosed syntaxes that most closely contains the `let` declaration:
- `Block` statement
- `switch` statement
- `try...catch`  statement
- Body of one of the `for` statements, if the `let` is in the header of the statement
- Function body
- Static initialization block

**Or if none of the above applies:**
- The current `module`, for code running in module mode
- The global scope, for code running in script mode.

Copared with `var`, `let` declarations have the following differences:

- 'let` declarations are scoped to blocks as well as functions.
- `let` declarations can only be accessed after the place of declaration is reached(TDZ ends here). For this reasion, `let` declarations are commonly regarded as `non-hoisted`.
- `let` declarations do not create properties on `globalThis` when declared at the top level of a script.
- `let` declarations cannot be redeclared by any other declaration in the same scope.
- `let` begins declarations, not statements. That means you cannot use a lone `let` declaration as the body of a block(which makes sense, since there's no way to access the variable).
```js
if (true) let a = 1; // SyntaxError: Lexical declaration cannot appear in a single-statement context
```
- The `if` statement expects a single statement or a block {}, and let (or const) is not allowed as a standalone statement there without curly braces.
- Reason: `let` is block scoped, so it's expects a block(`{}`);