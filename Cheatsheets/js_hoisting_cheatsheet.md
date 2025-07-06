
# 📌 JavaScript Hoisting Cheatsheet

---

## 🔍 What is Hoisting?

> Hoisting is JavaScript's behavior of moving **declarations** (not initializations) to the top of the scope during the compilation phase.

---

## 📊 Hoisting Behavior Summary

| Declaration Type     | Hoisted? | Initialized?        | Access Before Declaration        |
|----------------------|----------|----------------------|----------------------------------|
| `var`                | ✅ Yes   | ✅ As `undefined`    | ✅ Allowed, returns `undefined`  |
| `let`                | ✅ Yes   | ❌ No (TDZ applies)  | ❌ ReferenceError                |
| `const`              | ✅ Yes   | ❌ No (TDZ applies)  | ❌ ReferenceError                |
| Function Declaration | ✅ Yes   | ✅ Yes               | ✅ Allowed                       |
| Function Expression (`var`) | ✅ Yes (as var) | ✅ `undefined` | ❌ TypeError (not a function)  |
| Arrow Function (`const`)    | ✅ Yes (as const) | ❌ No           | ❌ ReferenceError                |

---

## 🧠 Temporal Dead Zone (TDZ)

`let` and `const` are hoisted but placed in a **Temporal Dead Zone** between:
- entering the scope
- the line where the variable is defined

```js
{
  console.log(myVar); // ❌ ReferenceError
  let myVar = 10;     // TDZ ends here
}
```

---

## 🧪 Examples

### ✅ `var` Hoisting

```js
console.log(x); // undefined
var x = 5;
```

Internally becomes:

```js
var x;
console.log(x);
x = 5;
```

---

### ❌ `let` and `const` in TDZ

```js
console.log(y); // ❌ ReferenceError
let y = 10;
```

---

### ✅ Function Declaration Hoisting

```js
sayHi(); // "Hi!"
function sayHi() {
  console.log("Hi!");
}
```

---

### ❌ Function Expression Not Hoisted

```js
sayHello(); // ❌ TypeError: sayHello is not a function
var sayHello = function () {
  console.log("Hello");
};
```

---

### ❌ Arrow Function with `const`

```js
greet(); // ❌ ReferenceError
const greet = () => console.log("Hey");
```

---

## 🧩 Best Practices

- ✅ Prefer `let` and `const` — avoid surprises with `var`
- 🚫 Don't rely on hoisting
- 🧼 Always declare variables at the top of their scope
- ⛔ Avoid using variables before declaring them

---

## 🧭 Visual Aid

```plaintext
Scope Start
↓
[TDZ] — accessing let/const here throws ReferenceError
↓
Declaration Line (TDZ ends)
↓
Safe usage of variable
```

---

## 🧾 Summary

| Keyword  | Scope Type     | Hoisted | TDZ  | Initial Value Before Init |
|----------|----------------|---------|------|----------------------------|
| `var`    | Function-scope | ✅ Yes  | ❌ No | `undefined`                |
| `let`    | Block-scope    | ✅ Yes  | ✅ Yes | ❌ Error (uninitialized)   |
| `const`  | Block-scope    | ✅ Yes  | ✅ Yes | ❌ Error (uninitialized)   |

---

👨‍💻 Understanding hoisting makes your code safer, cleaner, and easier to debug!
