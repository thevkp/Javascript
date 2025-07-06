
# 🔁 JavaScript Iteration Methods: Complete Comparison

| Method | Syntax | Data Type | Supports `break`/`continue` | Mutates Original? | Description & Use Case | Example |
|--------|--------|-----------|------------------------------|--------------------|------------------------|---------|
| **`for`** | `for (let i = 0; i < arr.length; i++) {}` | Arrays, any iterable | ✅ Yes | ✅ Can mutate | Classic loop with full control over index, breaking, and mutation. | ```js
for (let i = 0; i < arr.length; i++) {
  console.log(arr[i]);
}
``` |
| **`while`** / **`do...while`** | `while (condition) {}` | Any | ✅ Yes | ✅ Can mutate | Loop continues while condition is true; good for unknown loop lengths. | ```js
let i = 0;
while (i < arr.length) {
  console.log(arr[i++]);
}
``` |
| **`for...of`** | `for (let val of iterable) {}` | Arrays, Strings, Sets, Maps | ✅ Yes | ❌ (by default) | Simplified syntax for iterables. Cannot access index directly. | ```js
for (let item of arr) {
  console.log(item);
}
``` |
| **`for...in`** | `for (let key in obj) {}` | Objects, Arrays (enumerable keys) | ✅ Yes | ❌ (unless mutated manually) | Iterates over object keys. Avoid on arrays due to index issues. | ```js
for (let key in obj) {
  console.log(key, obj[key]);
}
``` |
| **`forEach()`** | `arr.forEach((val, i) => {})` | Arrays | ❌ No | ❌ (but can mutate elements) | Clean functional syntax for side-effects. No break/continue. | ```js
arr.forEach((val, i) => {
  console.log(i, val);
});
``` |
| **`map()`** | `arr.map((val, i) => newVal)` | Arrays | ❌ No | ❌ | Creates a new array with transformed values. | ```js
const doubled = arr.map(x => x * 2);
``` |
| **`filter()`** | `arr.filter(val => condition)` | Arrays | ❌ No | ❌ | Returns new array with only matching values. | ```js
const evens = arr.filter(x => x % 2 === 0);
``` |
| **`reduce()`** | `arr.reduce((acc, val) => acc + val, init)` | Arrays | ❌ No | ❌ | Accumulates a single return value. Great for totals. | ```js
const sum = arr.reduce((a, b) => a + b, 0);
``` |
| **`some()`** | `arr.some(val => condition)` | Arrays | ❌ No | ❌ | Returns `true` if **any** element passes. Stops early. | ```js
const hasEven = arr.some(x => x % 2 === 0);
``` |
| **`every()`** | `arr.every(val => condition)` | Arrays | ❌ No | ❌ | Returns `true` if **all** elements pass the test. | ```js
const allPositive = arr.every(x => x > 0);
``` |
| **`find()`** | `arr.find(val => condition)` | Arrays | ❌ No | ❌ | Returns **first** matching element, or `undefined`. | ```js
const match = arr.find(x => x > 10);
``` |
| **`findIndex()`** | `arr.findIndex(val => condition)` | Arrays | ❌ No | ❌ | Returns index of first match, or `-1`. | ```js
const index = arr.findIndex(x => x > 10);
``` |
| **`flatMap()`** | `arr.flatMap(val => [...])` | Arrays | ❌ No | ❌ | Like `map()` + `flat()`. Returns flattened result. | ```js
const result = arr.flatMap(x => [x, x * 2]);
``` |

---

## 🔍 When to Use Which?

| Goal | Recommended Method(s) |
|------|------------------------|
| Simple iteration with index | `for`, `forEach()` |
| Loop through object keys | `for...in` |
| Loop through array values | `for...of`, `forEach()` |
| Early exit (break/continue needed) | `for`, `for...of` |
| Transform array | `map()`, `flatMap()` |
| Filter elements | `filter()` |
| Search for value or index | `find()`, `findIndex()` |
| Accumulate value (sum, total, object) | `reduce()` |
| Test any/all match | `some()`, `every()` |
