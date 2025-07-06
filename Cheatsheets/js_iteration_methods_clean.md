
# 🔁 JavaScript Iteration Methods: Complete Comparison

## 📋 Iteration Table

| Method               | Syntax Example                                       | Data Type                        | Supports `break`/`continue` | Mutates Original? | Description & Use Case                                  |
|----------------------|------------------------------------------------------|----------------------------------|------------------------------|--------------------|----------------------------------------------------------|
| **`for`**            | `for (let i = 0; i < arr.length; i++) {}`           | Arrays, any iterable             | ✅ Yes                       | ✅ Can mutate      | Classic loop with full control.                         |
| **`while`**          | `while (condition) {}`                               | Any                              | ✅ Yes                       | ✅ Can mutate      | Loop with condition-first checking.                     |
| **`do...while`**     | `do { ... } while (condition);`                      | Any                              | ✅ Yes                       | ✅ Can mutate      | Condition-checked after first run.                      |
| **`for...of`**       | `for (let val of iterable) {}`                       | Arrays, Strings, Sets, Maps      | ✅ Yes                       | ❌ (by default)    | Simplified loop for iterable values.                    |
| **`for...in`**       | `for (let key in obj) {}`                            | Objects, Arrays (keys)           | ✅ Yes                       | ❌ (unless manual) | Used for object keys (not recommended for arrays).      |
| **`forEach()`**      | `arr.forEach((val, i) => {})`                        | Arrays                           | ❌ No                        | ❌ (can mutate)    | Functional loop for side-effects.                       |
| **`map()`**          | `arr.map(val => newVal)`                             | Arrays                           | ❌ No                        | ❌                | Transforms each element into a new array.              |
| **`filter()`**       | `arr.filter(val => condition)`                       | Arrays                           | ❌ No                        | ❌                | Filters array based on condition.                      |
| **`reduce()`**       | `arr.reduce((acc, val) => acc + val, init)`         | Arrays                           | ❌ No                        | ❌                | Reduces array to single value.                         |
| **`some()`**         | `arr.some(val => condition)`                         | Arrays                           | ❌ No                        | ❌                | Checks if any element passes test.                     |
| **`every()`**        | `arr.every(val => condition)`                        | Arrays                           | ❌ No                        | ❌                | Checks if all elements pass test.                      |
| **`find()`**         | `arr.find(val => condition)`                         | Arrays                           | ❌ No                        | ❌                | Returns first element that matches condition.          |
| **`findIndex()`**    | `arr.findIndex(val => condition)`                    | Arrays                           | ❌ No                        | ❌                | Returns index of first matching element.               |
| **`flatMap()`**      | `arr.flatMap(val => [...])`                          | Arrays                           | ❌ No                        | ❌                | Maps and flattens results one level deep.              |

---

## 💡 Code Examples

### `for`
```js
for (let i = 0; i < arr.length; i++) {
  console.log(arr[i]);
}
```

### `while`
```js
let i = 0;
while (i < arr.length) {
  console.log(arr[i++]);
}
```

### `for...of`
```js
for (let item of arr) {
  console.log(item);
}
```

### `for...in`
```js
for (let key in obj) {
  console.log(key, obj[key]);
}
```

### `forEach()`
```js
arr.forEach((val, i) => {
  console.log(i, val);
});
```

### `map()`
```js
const doubled = arr.map(x => x * 2);
```

### `filter()`
```js
const evens = arr.filter(x => x % 2 === 0);
```

### `reduce()`
```js
const sum = arr.reduce((a, b) => a + b, 0);
```

### `some()`
```js
const hasEven = arr.some(x => x % 2 === 0);
```

### `every()`
```js
const allPositive = arr.every(x => x > 0);
```

### `find()`
```js
const match = arr.find(x => x > 10);
```

### `findIndex()`
```js
const index = arr.findIndex(x => x > 10);
```

### `flatMap()`
```js
const result = arr.flatMap(x => [x, x * 2]);
```

---

## 🧭 When to Use What?

| Goal                          | Recommended Method(s)     |
|-------------------------------|---------------------------|
| Need full control / index     | `for`, `while`            |
| Iterate over object keys      | `for...in`                |
| Iterate over iterable values  | `for...of`, `forEach()`   |
| Transform values              | `map()`, `flatMap()`      |
| Filter by condition           | `filter()`                |
| Aggregate to a value          | `reduce()`                |
| Check any/all match condition| `some()`, `every()`       |
| Find value or index           | `find()`, `findIndex()`   |
| Require early exit            | `for`, `for...of`         |
