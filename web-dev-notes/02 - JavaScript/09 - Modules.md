# JavaScript Modules (ES6)

## Why Modules?

Break a large program into small files. Benefits: better organization, reusable code, easier debugging, separation of concerns, avoids global namespace pollution.

A module is a JS file that can **export** code and **import** code from other files.

## export

```js
export const age = 20;                 // variable

export const greet = () => {           // function
  console.log('Hello');
};

export class Dog {}                    // class
```

## Named Exports

Allows multiple exports from one file.

```js
// module.js
export const greet = () => { console.log('Hello'); };
export const bye = () => { console.log('Bye'); };
```

```js
// import
import { greet, bye } from './module.js';
```

Alternative syntax — export later:

```js
const greet = () => {};
const bye = () => {};

export { greet, bye };
```

## Renaming Imports

Useful when two modules export the same name.

```js
export const greet = () => {};
```

```js
import { greet as hello } from './module.js';
hello();
```

## Default Export

Exports one main value from a module.

```js
// module.js
const colors = ['red', 'blue', 'green'];
export default colors;
```

```js
// import — any name works
import colors from './module.js';
import myColors from './module.js';
```

## Named vs Default Export

| Named Export | Default Export |
| --- | --- |
| Many per file | One per file |
| Uses `{}` when importing | No `{}` |
| Name must match | Any name works |
| `export const x = ...` | `export default x` |

## Exporting an Object

```js
const resources = { greet, bye };
export default resources;
```

```js
import resources from './module.js';
resources.greet();
```

Destructuring imported object:

```js
import resources from './module.js';
const { greet, bye } = resources;
```

## Module Script (HTML)

```html
<script type="module" src="./main.js"></script>
```

## Relative Paths

| Path | Meaning |
| --- | --- |
| `./module.js` | Current folder |
| `../module.js` | One folder up |

## Module Flow

```
module.js → export → main.js → import → Use functions/classes/variables
```

---
## Related
- [[08 - Classes & OOP]]
- [[../05 - Backend/CommonJS]]
