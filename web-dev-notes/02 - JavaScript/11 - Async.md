# Async JavaScript

## Synchronous vs Asynchronous

```js
// Synchronous (Blocking) — runs line by line
console.log("A");
console.log("B");
console.log("C");
// Output: A B C
```

```js
// Asynchronous (Non-Blocking)
setTimeout(() => {
  console.log("B");
}, 1000);

console.log("A");
// Output: A, B (after ~1s)
```

## JavaScript is Single Threaded

```
One Call Stack → One task at a time
```

Uses Event Loop + Web APIs + Event Queue to handle async tasks.

## Event Loop

```
Call Stack → Web APIs → Event Queue → Event Loop → Call Stack
```

## setTimeout() / setInterval()

```js
setTimeout(callback, delay);   // runs once after delay
setInterval(callback, delay);  // runs repeatedly every interval
```

---

## Promises

A Promise is an object representing the future result of an async operation.

### States

```
Pending ⏳ → Fulfilled ✅
          → Rejected ❌
```

### Creating a Promise

```js
const promise = new Promise((resolve, reject) => {
  resolve("Success");  // Pending → Fulfilled
  // reject("Error");  // Pending → Rejected
});
```

### Consuming Promises

```js
promise.then((value) => {
  console.log(value);
});
```

Success & failure handlers:

```js
promise.then(
  (value) => { console.log(value); },
  (error) => { console.log(error); }
);
```

### .catch()

```js
promise
  .then((value) => { console.log(value); })
  .catch((error) => { console.log(error); });
```

## Promise Chaining

```js
promise1()
  .then((result1) => {
    return promise2(result1);   // must return!
  })
  .then((result2) => {
    console.log(result2);
  });
```

Use when Task 2 depends on Task 1.

Common mistakes:

```js
// ❌ Nesting
.then(() => {
  promise2().then(...)
})

// ❌ Forgetting return
.then(() => {
  promise2();
})

// ✅ Correct
.then(() => {
  return promise2();
})
.then(...)
```

## Promise.all()

```js
const values = await Promise.all([p1, p2, p3]);
// Returns [value1, value2, value3]
```

If any promise fails → `Promise.all` rejects.

---

## async / await

```js
async function example() {
  // always returns a Promise
}
```

```js
const value = await promise;
// waits → promise resolves → returns value
```

| Without await | With await |
| --- | --- |
| `Promise { <pending> }` | Resolved value |

## Dependent Promises

```js
// Old style
promise1().then(...).then(...)

// New style
async function example() {
  const a = await promise1();
  const b = await promise2(a);
}
```

## Error Handling (async)

```js
async function example() {
  try {
    const result = await promise;
  } catch(err) {
    console.log(err);
  }
}
```

## Independent Promises

```js
// ❌ Slow — runs sequentially
await p1();
await p2();

// ✅ Better — starts both together
const p1Promise = p1();
const p2Promise = p2();
await p1Promise;
await p2Promise;
```

## await Promise.all()

```js
const results = await Promise.all([
  promise1(),
  promise2(),
  promise3()
]);
```

Best for independent promises.

## Quick Revision

```
setTimeout()      → Delay execution

Promise States:
  Pending / Fulfilled / Rejected

resolve()         → Success
reject()          → Failure

.then()           → Success handler
.catch()          → Failure handler

Promise Chaining  → Dependent tasks
Promise.all()     → Concurrent tasks

async             → Creates async function
await             → Wait for Promise result
try...catch       → Handle async errors

Independent Tasks → Promise.all()
Dependent Tasks   → Multiple awaits
```

---
## Related
- [[04 - Functions]]
- [[10 - Error Handling]]
- [[../05 - Backend/06 - Fetch API]]
