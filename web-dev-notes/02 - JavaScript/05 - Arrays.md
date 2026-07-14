# Arrays

## Definition

An array is an ordered list of data.

```js
let arr = [1, 2, 3];
```

## Indexing

Starts from **0**.

```js
arr[0] // first element
```

## Access & Update

```js
arr[1];       // access
arr[1] = 10;  // update
```

## Length

```js
arr.length
```

Total elements. Last index = `length - 1`.

## Important Methods

### Mutating (change original)

```js
arr.push(x);    // add end
arr.pop();      // remove last
arr.shift();    // remove first
arr.unshift(x); // add start
arr.splice();   // add/remove anywhere
```

### Non-mutating

```js
arr.slice();    // copy part
arr.concat();   // merge arrays
arr.join();     // array → string
```

## Return Behavior

| Method | Returns |
| --- | --- |
| `.push()` | New length |
| `.pop()` | Removed element |

## let vs const

```js
const arr = [1, 2];
arr[0] = 5;   // ✅ allowed
arr = [3, 4]; // ❌ not allowed
```

## Arrays in Functions

Passed by reference.

```js
function f(a) {
  a.push(10);
}
// original array changes
```

## Nested Arrays

```js
arr[1][0]
```

## Looping

```js
for (let i = 0; i < arr.length; i++) {
  console.log(arr[i]);
}
```

## ⚠️ Common Mistakes

- Using `<= arr.length` ❌
- Thinking index starts from 1 ❌
- Confusing return value of `.push()`

---
## Related
- [[06 - Objects]]
- [[07 - Iterators]]
