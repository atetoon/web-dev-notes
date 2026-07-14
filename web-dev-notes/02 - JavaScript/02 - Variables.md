# Variables

## Keywords

| Keyword | Behavior |
| --- | --- |
| `let` | Can change |
| `const` | Cannot change |
| `var` | Old — avoid |

```js
let age = 20;
const name = 'John';
```

Not assigned → `undefined`

## Operators

```js
age += 5; // same as age = age + 5
```

## String Concatenation

```js
let a = 'Hello';
let b = 'World';
console.log(a + ' ' + b);
```

## Template Literals (ES6)

```js
console.log(`Hello ${name}`);
```

## typeof

```js
console.log(typeof age); // 'number'
```

## ⚠️ Important — Hoisting

```js
console.log(test1);
const test1 = 'abc';
```

❌ Error → **cannot access before initialization**

> `let` & `const` are NOT hoisted like `var`.

---
## Related
- [[01 - Basics]]
- [[03 - Conditionals]]
