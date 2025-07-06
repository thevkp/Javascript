
# 🔥 JavaScript Lexical Declaration Traps Cheat Sheet (`let` / `const`)

> When JavaScript says “SyntaxError” for something that looks totally legal.

---

## ❌ 1. Lexical Declarations Not Allowed in Single-Statement Contexts

```js
if (true) let a = 1; // ❌ SyntaxError
```

### ✅ Fix:
```js
if (true) {
  let a = 1;
}
```

🧠 **Why?**  
`let` and `const` must appear in a **block**, not in places where a single expression is expected.

---

## ❌ 2. `let` / `const` in `if`, `for`, or `while` without braces

```js
while (true) const a = 5; // ❌ SyntaxError
```

✅ Always use blocks:

```js
while (true) {
  const a = 5;
}
```

---

## ✅ 3. Allowed: `var` in those same places

```js
if (true) var a = 1; // ✅ Works
```

⚠️ But remember: `var` is function scoped and hoisted — probably not what you want.

---

## ❌ 4. TDZ (Temporal Dead Zone) Gotchas

```js
console.log(x); // ❌ ReferenceError
let x = 10;
```

✅ Safe usage:
```js
let x = 10;
console.log(x); // ✅ 10
```

---

## ❌ 5. Duplicate Declarations (Redeclaring `let`)

```js
let a = 5;
let a = 10; // ❌ SyntaxError
```

✅ Okay only in separate scopes:

```js
let a = 5;
{
  let a = 10; // ✅ Different scope
}
```

---

## ✅ 6. Using `let` in `for` loops creates new bindings per iteration

```js
for (let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 100);
}
// ✅ Output: 0 1 2
```

✅ This avoids the classic `var` closure trap.

---

## 🧠 Pro Tips

| 🔥 Trap                          | ✅ What to Do                   |
|----------------------------------|----------------------------------|
| `let` without `{}` in `if`/`for` | Always use braces `{}`          |
| TDZ error                        | Declare before accessing         |
| Can't redeclare `let` in scope  | Use unique names or new scope    |
| `var` works in single statements | But avoid using it altogether    |

---

## ✅ General Rule of Thumb

If you're using `let` or `const`:
- Always wrap logic in `{}`
- Declare variables at the top of the block
- Never rely on hoisting
- Use linters (like ESLint) to catch these traps

---

🧯 JavaScript’s syntax rules might feel overprotective, but they’re designed to save you from subtle bugs. Think of them as **guardrails**, not handcuffs.

Stay curly. Use `{}`. Save lives. 💪

