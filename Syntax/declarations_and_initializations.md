## Declaring variables
**Variables cana be declared in two ways**
- With the keyword var. For example, var x = 42. This syntax can be used to declare both local and global variables, depending on the execution context.

- With the keyword const or let. For example, let y = 13. This syntax can be used to declare a block-scope local variable. (See Variable scope below.)


## Declaration and initialization
- In a statement like __let x = 42__, the __let x__ part is called a __declaration__, and the __= 42__ part is called an __initializer__. The declaration allows the variable to be accessed later in code without throwing a ReferenceError, while the initializer assigns a value to the variable. In var and let declarations, the initializer is optional. If a variable is declared without an initializer, it is assigned the value __undefined__.

```
let x = 42;
console.log(x); // logs "undefined"

let y;
y = 43;
```

### `const` declarations ###
**`const` declarations always need an initializer, because they forbid any kind of assignment after declaration, and implicitly initializing it with undefined is likely a programmer mistake.**

```
const x; // SyntaxError: Missing initializer in const declaration
```

## Varibale Scope

**A variable may belong to one of the following scopes:**
- __Global scope:__ The default scope for all code running in the script mode.

- Variables declared outside of any function or block have global scope.

- They are accessible __anywhere__ in the code after their declaration.

```
var globalVar = "I'm global";

function showVar() {
  console.log(globalVar); // works
}
```

__Function Scope:__ Variables declared with `var` inside a function are function scoped.

```
function functionScoped() {
  var localVar = "I'm local";
  console.log(localVar); // works
}
console.log(localVar); // Error: localVar is not defined
```

__Block Scope:__ Variables declared with `let` or `const` have block scope.

- They're only accessible within the enclosing `{}` block.

```
if (true) {
  let blockVar = "I'm block-scoped";
  const anotherBlockVar = "Me too!";
}

console.log(blockVar); //Error
```

__Module Scope:__ When using JavaScript modules (import/export), variables declared at the top level of a module are module-scopedl
- They are not added to the global objec.

```
// In a module
let moduleVar = "Only accessible in this module";
```

# ⚠️ Important Notes
- `var` is function-scoped, not block-scoped, which can lead to unexpected behavior:

```
if (true) {
  var x = 10;
}
console.log(x);
//10 - cause 'var' ignores the block
```