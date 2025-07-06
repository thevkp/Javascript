
# 🧠 JavaScript Closures Cheatsheet

---

## 📌 What is a Closure?

> A **closure** is the combination of a **function** and the **lexical environment** within which that function was declared.  
It means the function remembers variables from its outer(enclosing) scope, even after the outer function has finished executing.

---

## 🧪 Basic Closure Example

```js
function outer() {
  let secret = "I know something!";

  return function inner() {
    console.log(secret);
  };
}

const fn = outer();
fn(); // "I know something!"
```

✅ `inner()` still has access to `secret` after `outer()` has finished.

---

## 📊 Closure Characteristics

| Feature               | Closure Behavior                                                                 |
|------------------------|----------------------------------------------------------------------------------|
| Memory of outer scope  | ✅ Remembers variables from when it was defined                                  |
| Outer function done?   | ✅ Still works — closure maintains reference                                     |
| Scope chain access     | ✅ Full access to variables in its creation context                              |
| Encapsulation          | ✅ Useful for data privacy and stateful functions                                |

---

## 🔐 Use Case 1: Data Privacy

```js
function createCounter() {
  let count = 0;
  return function () {
    return ++count;
  };
}

const counter = createCounter();
console.log(counter()); // 1
console.log(counter()); // 2
```

---

## 🏭 Use Case 2: Function Factories

```js
function greeter(name) {
  return function (msg) {
    console.log(`${msg}, ${name}`);
  };
}

const greetJohn = greeter("John");
greetJohn("Hello"); // Hello, John
```

---

## ⏳ Use Case 3: Asynchronous Closures

```js
function delayedLog(message) {
  setTimeout(function () {
    console.log(message);
  }, 1000);
}

delayedLog("This is closure magic!");
```

---

## ⚠️ Common Pitfall: `var` in Loops

```js
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 1000);
}
// Output: 3, 3, 3 ❌
```

### ✅ Fix with `let` (block scope)

```js
for (let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 1000);
}
// Output: 0, 1, 2 ✅
```

---

## 🧠 How Closures Work Internally

- JavaScript creates a **lexical environment** for every function.
- The inner function keeps a **reference** to this environment.
- This allows it to **access outer variables**, even after the outer function has returned.

---

## 🎯 Practical Applications

| Use Case               | Description                                 |
|------------------------|---------------------------------------------|
| Private variables      | Hide internal values                        |
| Stateful functions     | Maintain state without global vars          |
| Event handlers         | Retain access to DOM/data context           |
| Callback factories     | Custom behavior in async scenarios          |

---

## 🧾 Closure Visualization

```plaintext
outer() environment
└── secret = "hidden"
    └── inner() closes over this environment
```

---

## 🧪 Nested Closures

```js
function first() {
  let one = 1;
  return function second() {
    let two = 2;
    return function third() {
      console.log(one + two);
    };
  };
}

first()()(); // 3
```

---

## ❗ Caveat: Closures Can Cause Memory Leaks

- Long-lived closures (e.g. in global scope or event listeners) may **hold on to memory**
- Clean up listeners, timers, and unused closures when possible

---

## 📎 TL;DR

| Feature            | Closure Power                              |
|--------------------|---------------------------------------------|
| Definition         | Function + remembered outer variables       |
| Useful for         | Privacy, factories, async logic             |
| Trap to avoid      | `var` in loops                              |
| Pro-tip            | Use `let`/`const` and return inner function |

---

🧩 Mastering closures unlocks deeper JS skills like currying, async control, and custom abstractions.
