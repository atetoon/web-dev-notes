# CommonJS Modules

## What are Modules?

A module is a reusable file containing code — export from one file, use in others. Why? Reuse code, avoid duplication, better organization, easier maintenance.

## CommonJS

Node.js uses **CommonJS Modules** by default — uses `module.exports` and `require()`.

## Exporting

```js
// shape-area.js
function circleArea(radius) {
  return Math.PI * radius * radius;
}

function squareArea(side) {
  return side * side;
}

module.exports.circleArea = circleArea;
module.exports.squareArea = squareArea;
```

> `module.exports` → send outside the file

## Importing

```js
// app.js
const areaFunctions = require('./shape-area.js');

areaFunctions.circleArea(5);
areaFunctions.squareArea(10);
```

Flow:

```
shape-area.js → module.exports → require() → areaFunctions
```

## Object Destructuring

Instead of:

```js
const areaFunctions = require('./shape-area.js');
areaFunctions.circleArea();
```

Use:

```js
const { circleArea, squareArea } = require('./shape-area.js');

circleArea(5);
squareArea(10);
```

```
Import Everything → const obj = require()
Import Specific   → const { thing } = require()
```

## Relative Paths

| Path | Meaning |
| --- | --- |
| `./shape-area.js` | Current folder |
| `../shape-area.js` | Go up one folder |

## Full Example

```js
// shape-area.js
function squareArea(side) {
  return side * side;
}
module.exports.squareArea = squareArea;

// app.js
const { squareArea } = require('./shape-area.js');
console.log(squareArea(10)); // 100
```

## The 3 Lines To Remember

```js
// Export
module.exports.add = add;

// Import All
const math = require('./math');

// Import One
const { add } = require('./math');
```

## Mind Map

```
CommonJS
├── module.exports → Export
├── require()      → Import
└── { }            → Object Destructuring
```

---
## Related
- [[02 - Node.js Essentials]]
- [[04 - Express.js]]
- [[../02 - JavaScript/09 - Modules]]
