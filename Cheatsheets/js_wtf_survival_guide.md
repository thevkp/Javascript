
# 🧨 JavaScript WTF Survival Guide (aka How to Stay Sane)

> A brutally honest guide for developers who want to survive JavaScript's weirdness without losing their minds.

---

## 🧱 1. ❌ Avoid These Like the Plague

| Feature             | Why it's bad                                | What to do instead               |
|---------------------|----------------------------------------------|----------------------------------|
| `var`               | Function scoped, hoisting nightmares         | ✅ Use `let` or `const`          |
| `==` (double equals)| Type coercion hell (`0 == false` → true)     | ✅ Use `===` always              |
| `with` statement    | Scope pollution, banned in strict mode       | ❌ Just don’t                    |
| Implicit globals    | Accidentally creating global vars (`x = 10`) | ✅ Use `strict mode`             |
| `function` inside blocks | Hoisting behavior is inconsistent      | ✅ Use arrow functions / `let`   |
| `arguments` object  | Weird, array-like, not real array            | ✅ Use rest parameters `...args` |
| `new Object()`      | Verbose and pointless                        | ✅ Use `{}`                      |

---

## ✅ 2. Always Use These

| Feature            | Why it's better                                |
|--------------------|-------------------------------------------------|
| `let` / `const`    | Block scoped, no redeclarations                |
| `===`              | Strict equality, no type coercion surprises    |
| Arrow functions    | Clean syntax, lexical `this`                   |
| `for...of`         | Clean iteration over arrays                    |
| `Array.map`, `.filter`, `.reduce` | Functional style, fewer loops     |
| Template literals  | `${}` inside strings, multiline support        |
| `async/await`      | Cleaner async code vs nested callbacks         |
| Modules (`import`) | Proper encapsulation and organization          |

---

## 🚫 3. Know These Gotchas

### 🧠 Function vs Variable Hoisting

```js
console.log(foo); // undefined, not ReferenceError
var foo = 42;

console.log(bar); // ❌ ReferenceError
let bar = 42;
```

- `var` is hoisted and initialized as `undefined`
- `let`/`const` are hoisted but not initialized → Temporal Dead Zone (TDZ)

---

### 🤖 Coercion WTFs

```js
false == 0         // true ❌
"" == 0            // true ❌
null == undefined  // true ❗ (the only sane coercion)
[] == false        // true ❌
[] == ![]          // true ❌
```

✅ Use `===` and never `==` unless you're 1,000% sure.

---

### 🌀 typeof WTFs

```js
typeof null       // "object" ❌ (legacy bug)
typeof NaN        // "number" ✅ (but weird)
typeof []         // "object" ❌
typeof function(){} // "function" ✅
```

Use `Array.isArray()` to check for arrays.

---

## 💥 4. Dangerous Legacy APIs

Avoid these whenever possible:

- `setInterval(fn, 0)` → Janky timing
- `document.write()` → Destroys your DOM
- `alert()` / `confirm()` → Blocks JS thread
- `eval()` → Executes arbitrary strings (🚨 security hazard)

---

## 🔐 5. Safer Modern Patterns

| Goal                 | Safe Pattern                             |
|----------------------|-------------------------------------------|
| Private data         | Closures or class `#private` fields       |
| Async code           | `async` / `await`                         |
| DOM access           | `querySelector`, `addEventListener`       |
| Modules              | `import` / `export`                       |
| Loops                | `for...of`, `forEach`, `map`              |

---

## 🔍 6. Recognize Legacy vs Modern JavaScript

| Legacy (Avoid)               | Modern (Use Instead)            |
|------------------------------|----------------------------------|
| `function myFunc()`          | `const myFunc = () => {}`        |
| `var`                        | `let` / `const`                  |
| Callback Hell                | Promises / `async`/`await`       |
| Prototypes manually          | `class` syntax                   |
| Script tags only             | Modules / bundlers (Vite, etc.)  |

---

## ✨ 7. JavaScript Modes

### Use Strict Mode

```js
"use strict";
```

- Prevents silent errors
- Disallows undeclared vars
- Makes things less WTF

---

## 🧠 8. Mental Model Tips

| Rule                                             | Why                         |
|--------------------------------------------------|------------------------------|
| Everything happens in a scope                    | Block > Function > Global    |
| Functions capture variables (closures)           | They "remember" the context  |
| Hoisting happens during parse                    | Not during runtime           |
| JS is single-threaded                            | Use async, not threads       |
| `this` is dynamic unless arrow function is used  | Use arrow for safety         |

---

## 🚀 9. Tools That Save Your Sanity

| Tool            | Why It Helps                        |
|-----------------|-------------------------------------|
| ESLint          | Finds bad patterns automatically    |
| TypeScript      | Adds types and guards               |
| Prettier        | Code formatting                     |
| Babel           | Transpile modern JS for old browsers|
| MDN Docs        | The source of truth for JS behavior |

---

## 🧾 10. Final Advice

- JavaScript is a **messy but powerful** language.
- You can't avoid the bad parts — but you **can avoid using them**.
- Master **modern JS only** — and let linters and TypeScript scream at you if you touch anything cursed.

---

🧩 The more you learn what to avoid, the more you'll see JavaScript as a **practical tool**, not a chaotic mystery.

Stay strong. JS was made in 10 days — but you’re taking the time to truly learn it. 🫡
