# JavaScript Error Handling

## Why Error Handling?

| Type | Program Runs? |
| --- | --- |
| Logic Error | ✅ Yes |
| Runtime Error | ❌ No |

```js
const age = 20;
age = 30;
// TypeError: Assignment to constant variable.
// Program stops.
```

Goal: catch the error and let the program continue running.

## Error Objects

JavaScript errors are objects.

| Property | Purpose |
| --- | --- |
| `name` | Error type |
| `message` | Error description |

```js
const error = new Error('Weak password');
console.log(error.name);     // 'Error'
console.log(error.message);  // 'Weak password'
```

## Common Built-in Errors

| Error | Cause |
| --- | --- |
| `ReferenceError` | Variable not found |
| `TypeError` | Invalid operation (e.g. reassigning `const`) |

## Creating vs Throwing

```js
// Creating — program continues
new Error('Oops');

// Throwing — program stops immediately
throw Error('Oops');
```

## try...catch

```js
try {
  // risky code
} catch(e) {
  // handle error
}
```

```js
try {
  throw Error('Wrong password');
} catch(e) {
  console.log(e.message);
}
console.log('Program continues');

// Output:
// Wrong password
// Program continues
```

## try...catch Flow

```
try → run code → error?
  No  → continue
  Yes → catch(e) → handle error → continue program
```

## Error Parameter

```js
catch(e) {
  console.log(e.name);
  console.log(e.message);
}
```

## Handling Built-in Errors

```js
const text = 'Hello';

try {
  text = 'World';
} catch(e) {
  console.log(e.message);
  // 'Assignment to constant variable.'
}
// Program continues.
```

## Why Use try...catch?

Useful when working with data that may not be what you expect:

- User Input
- API Data
- Database Data
- External Files

---
## Related
- [[11 - Async]]
- [[../03 - JavaScript Testing/JS Testing]]
