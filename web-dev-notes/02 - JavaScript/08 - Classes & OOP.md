# Classes & OOP

## Core Concepts

| Concept | Syntax | Purpose |
| --- | --- | --- |
| Class | `class Dog {}` | Blueprint for objects |
| Constructor | `constructor()` | Runs automatically when object is created |
| Instance | `new Dog()` | Creates object from class |
| `this` | `this._name = name` | Refers to current object |
| Getter | `get name(){}` | Read property |
| Setter | `set name(value){}` | Update property |
| Method | `bark(){}` | Perform action |
| Inheritance | `extends` | Child inherits parent |
| Super | `super()` | Calls parent constructor |
| Static Method | `static method(){}` | Called on class itself |

## Class Template

```js
class Dog {
  constructor(name) {
    this._name = name;
  }

  get name() {
    return this._name;
  }

  set name(newName) {
    this._name = newName;
  }

  bark() {
    console.log('Woof');
  }

  static info() {
    console.log('Dog Class');
  }
}
```

## Creating Instances

```js
const dog1 = new Dog('Max');
```

Flow:

```
Class → new → Constructor runs → Object created
```

## this Keyword

```js
this._name = name; // current object's _name property
```

## Getters & Setters

```js
get name() {
  return this._name;
}
// usage: dog.name (no parentheses)

set name(newName) {
  this._name = newName;
}
// usage: dog.name = 'Rocky'
```

| Operation | Syntax |
| --- | --- |
| Read | `dog.name` |
| Update | `dog.name = 'Rocky'` |

## Inheritance

```js
class Animal {
  constructor(name) {
    this._name = name;
  }
}

class Cat extends Animal {
  constructor(name, usesLitter) {
    super(name);          // calls parent constructor
    this._usesLitter = usesLitter;
  }
}
```

Child automatically gets parent's properties, getters, setters, methods.

## super()

Calls the parent constructor. Rule: pass values needed by parent constructor.

```js
class Cat extends Animal {
  constructor(name, usesLitter) {
    super(name);
    this._usesLitter = usesLitter;
  }
}
```

Flow:

```
Cat constructor → super(name) → Animal constructor → _name initialized
→ Back to Cat constructor → _usesLitter initialized
```

Rule of thumb:

```
Parent properties → super()
Child properties  → this._property
```

## Static Methods

```js
class School {
  static pickSubstituteTeacher(teachers) {
    const index = Math.floor(Math.random() * teachers.length);
    return teachers[index];
  }
}

School.pickSubstituteTeacher([...]);  // called on class, not instance
```

| Normal Method | Static Method |
| --- | --- |
| `obj.method()` | `Class.method()` |
| Needs object | No object needed |
| Uses instance data | Usually utility/helper |

## Common Patterns

```js
// Toggle boolean
this._isCheckedOut = !this._isCheckedOut;

// Add item to array
this._ratings.push(rating);

// Average using reduce()
const total = this.ratings.reduce((sum, rating) => sum + rating, 0);
return total / this.ratings.length;
```

## OOP Master Flow

```
Class → Constructor → new → Instance/Object
→ Getter/Setter/Methods → Inheritance (extends) → super() → Static Methods
```

---
## Related
- [[04 - Functions]]
- [[06 - Objects]]
- [[09 - Modules]]
