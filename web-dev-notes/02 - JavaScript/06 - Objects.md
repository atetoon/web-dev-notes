# Objects

## What is an Object

An object is a collection of named data (key → value).

```js
const obj = { name: 'John', age: 20 };
```

## Properties & Methods

Properties store data, methods define behavior.

```js
const obj = {
  name: 'John',
  greet() {
    console.log('Hi');
  }
};
```

## Accessing Values

Use dot for fixed keys, bracket for dynamic keys.

```js
obj.name        // 'John'
obj['name']     // 'John'

const key = 'name';
obj[key];       // 'John'
```

## Add / Update

Objects can be modified anytime.

```js
obj.city = 'Delhi';
obj.age = 25;
```

## Nested Objects

```js
const obj = {
  inner: { value: 10 }
};

obj.inner.value; // 10
```

## `this` Keyword

`this` refers to the object calling the method.

```js
const obj = {
  name: 'John',
  greet() {
    console.log(this.name);
  }
};
```

## Arrow Function Warning

Arrow functions don't bind `this` to the object.

```js
const obj = {
  name: 'John',
  greet: () => console.log(this.name) // ❌ undefined
};
```

## Mutability

Objects can change even if declared with `const`.

```js
const obj = { a: 1 };
obj.a = 2; // ✅
```

## Pass by Reference

Objects share memory when passed to functions.

```js
function change(o) {
  o.a = 10;
}

const obj = { a: 1 };
change(obj);
console.log(obj.a); // 10
```

## Looping (for...in)

```js
for (let key in obj) {
  console.log(key, obj[key]);
}
```

## Privacy (Convention)

`_` means "don't modify directly" (just a convention).

```js
const obj = { _value: 100 };
```

## Getters

Getter = controlled way to read data.

```js
const obj = {
  _val: 10,
  get val() {
    return this._val;
  }
};

obj.val; // 10
```

## Setters

Setter = controlled way to update data.

```js
const obj = {
  _val: 10,
  set val(x) {
    this._val = x;
  }
};

obj.val = 20;
```

## Factory Functions

Functions that create and return objects.

```js
const createUser = (name) => {
  return { name };
};

const user = createUser('John');
```

## Property Shorthand

If key and variable name are the same, write once.

```js
const name = 'John';
const obj = { name };
```

## Destructuring

Extract values from object into variables.

```js
const obj = { name: 'John' };
const { name } = obj;
```

## Built-in Methods

```js
Object.keys(obj);      // ['name']
Object.entries(obj);   // [['name', 'John']]
Object.assign({}, obj);
```

## ⚠️ Common Mistakes

- Using arrow function with `this` ❌
- Using dot instead of bracket for variables ❌
- Expecting objects to be ordered ❌

---
## Related
- [[05 - Arrays]]
- [[08 - Classes & OOP]]
