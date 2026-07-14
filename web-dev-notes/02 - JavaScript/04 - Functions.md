# Functions

A function is a reusable code block.

## Declaration & Call

```js
function greet() {
  console.log('Hello');
}

greet();
```

## Parameters & Arguments

```js
function add(a, b) {
  return a + b;
}
```

## Types

```js
// Function Expression
const add = function(a, b) {
  return a + b;
};

// Arrow Function (ES6)
const add = (a, b) => a + b;
```

## Key Concepts

```js
return;  // gives output

// Default params
function greet(name = 'Guest') {}
```

---
## Related
- [[03 - Conditionals]]
- [[08 - Classes & OOP]]
- [[11 - Async]]
