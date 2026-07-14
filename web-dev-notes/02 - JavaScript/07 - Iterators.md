# Iterators

## Array Methods

| Method | Syntax | Purpose | Returns | Special Case |
| --- | --- | --- | --- | --- |
| `.forEach()` | `arr.forEach(cb)` | Executes code for every element | `undefined` | Cannot break/return new array |
| `.map()` | `arr.map(cb)` | Transforms elements | New array | Original array unchanged |
| `.filter()` | `arr.filter(cb)` | Keeps matching elements | Filtered array | Callback must return true/false |
| `.findIndex()` | `arr.findIndex(cb)` | Finds first matching index | Index / `-1` | Stops at first match |
| `.reduce()` | `arr.reduce(cb, init)` | Reduces array → single value | Single value | 2nd argument = initial accumulator |
| `.some()` | `arr.some(cb)` | Checks if at least one matches | `true/false` | Stops at first true |
| `.every()` | `arr.every(cb)` | Checks if all match | `true/false` | Stops at first false |

## Examples

```js
arr.forEach(x => console.log(x));
arr.map(x => x * 2);
arr.filter(x => x > 5);
arr.findIndex(x => x < 10);
arr.reduce((a, b) => a + b, 0);
arr.some(x => x < 0);
arr.every(x => x > 0);
```

## Callback Function

| Concept | Meaning | Example |
| --- | --- | --- |
| Callback Function | Function passed into another function | `arr.map(x => x*2)` |
| Higher-Order Function | Function taking/returning function | `.map()`, `.filter()` |

## .reduce() Flow

| Iteration | accumulator | currentValue | Return |
| --- | --- | --- | --- |
| 1 | 0 | 1 | 1 |
| 2 | 1 | 2 | 3 |
| 3 | 3 | 3 | 6 |

```js
const cart = [
  { item: 'Laptop', price: 50000 },
  { item: 'Mouse', price: 1000 },
  { item: 'Keyboard', price: 2000 }
];

const totalPrice = cart.reduce((accumulator, currentItem) => {
  return accumulator + currentItem.price;
}, 0); // -> Initializer

console.log(totalPrice);
```

---
## Related
- [[05 - Arrays]]
