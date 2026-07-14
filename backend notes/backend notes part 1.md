# CLI ~

- `pwd` outputs the name of the current working directory.
- `ls` lists all files and directories in the working directory.
- `cd` switches you into the directory you specify.
- `..` is used to represent the directory above when navigating.
- `mkdir` creates a new directory in the working directory.
- `touch` creates a new file inside the working directory.
- `clear` clears the terminal
- tab autocompletes the name of a file or directory
- ↑ and ↓ allow you to cycle through previous commands

# HTML ~

- <strong> for bold
- <em> for italic
- <h1><h6> for headings
- <div></div> for divisions (id=”xyz”)
- <p> for paragraph
- <br> (single) for line break.
- <ul>unodered list</ul> and <li></li> for bullet points inside <ul>
- <ol>Ordered List</ol> and <li></li> for numbered list inside <ol>
- <img src="URL" /> to add image to your HTML file.
- <img src="#" alt="A field of yellow sunflowers" /> alt attribute adds meaning to the images on our sites. The value of “alt” should be a discription of the image.
- <a href="#id"><img src="link"/></a> → to make a image clickable link.

1. The `<!DOCTYPE html>` declaration should always be the first line of code in your HTML files. This lets the browser know what version of HTML to expect.
2. The `<html>` element will contain all of your HTML code.
3. Information about the web page, like the title, belongs within the `<head>` of the page.
4. You can add a title to your web page by using the `<title>` element, inside of the head.
5. A webpage’s title appears in a browser’s tab.
6. Anchor tags (`<a>`) are used to link to internal pages, external pages or content on the same page.
7. You can create sections on a webpage and jump to them using `<a>` tags and adding `id`s to the elements you wish to jump to.
8. Whitespace between HTML elements helps make code easier to read while not changing how elements appear in the browser.
9. Indentation also helps make code easier to read. It makes parent-child relationships visible.
10. Comments are written in HTML using the following syntax: `<!-- comment -->`.

# CSS ~

- CSS syntax written for both inline styles and stylesheets.
    
- Some commonly used CSS terms, such as _ruleset_, _selector_, and _declaration_.
    
    ![CSS_Anatomy-v2-nobgfill.svg](attachment:eb5ad3c1-0a80-4e02-8fd4-ba5aed26fa7b:CSS_Anatomy-v2-nobgfill.svg)
    
- An internal stylesheet is written using the `<style>` element inside the `<head>` element of an HTML file.
    
- Internal stylesheets can be used to style HTML but are also not best practice.
    

```css
<head>
<style>
p {
color: red;
font-size: 20px;
}
</style>
</head>
```

- Inline styles can be used to style HTML, but it is not the best practice.
    
- CSS inline styles can be written inside the opening HTML tag using the `style` attribute.
    
    ```jsx
    <p style='color: red;'>I'm learning to code!</p>
    ```
    
- An external stylesheet separates CSS code from HTML, by using the `.css` file extension.
    
- External stylesheets are the best approach when it comes to using HTML and CSS.
    
- External stylesheets are linked to HTML using the `<link>` element.
    

```css
<link href='<https://www.codecademy.com/stylesheets/style.css>' rel='stylesheet'>

												or 

<link href='./style.css' rel='stylesheet'> (relative path)

```

---

- CSS can select HTML elements by **type, class, ID, and attribute**
    
    → Different ways to target elements.
    

```css
p { color: blue; }        /* type */
.box { color: red; }      /* class */
#main { color: green; }   /* ID */
input[type="text"] { border: 1px solid black; } /* attribute */
```

---

- (universal selector) selects **all elements**.

```css
* {
  margin: 0;
  padding: 0;
}
```

→ Used for reset.

---

- Pseudo-class selects an element in a **special state**.

```css
a:hover {
  color: red;
}
```

→ Changes when mouse is over link.

---

- Multiple classes can be applied to one element.

```html
<p class="red bold">Hello</p>
```

```css
.red { color: red; }
.bold { font-weight: bold; }
```

→ Both styles apply.

---

- Classes are reusable. IDs are unique.

```html
<div class="box"></div>
<div class="box"></div>   <!-- allowed -->

<div id="main"></div>
<div id="main"></div>     <!-- wrong -->
```

→ ID should be used once per page.

---

- Specificity order:

```
ID > Class > Type
```

```css
p { color: blue; }
.text { color: green; }
#para { color: red; }
```

If element has all three → **red wins**.

→ More specific = stronger priority.

---

- Chaining selectors increases specificity.

```css
div.box {
  background: yellow;
}
```

→ Selects `<div class="box">` only.

---

- Nested selection (descendant selector)

```css
div p {
  color: purple;
}
```

→ Selects `<p>` inside `<div>` only.

---

- Multiple unrelated selectors (comma)

```css
h1, p, .box {
  font-family: Arial;
}
```

→ Applies same style to all.

---

### Text Styling under CSS —>

- **font-family** → sets typeface

```css
p { font-family: Arial; }
```

---

- **font-size** → text size

```css
p { font-size: 20px; }
```

---

- **font-weight** → thickness of text

```css
p { font-weight: bold; }
```

---

- **text-align** → horizontal text position

```css
p { text-align: center; }
```

---

- **color** → text color
- **background-color** → color behind text

```css
p { color: white; background-color: black; }
```

---

- **opacity** → transparency (0–1)

```css
p { opacity: 0.5; }
```

---

- **background-image** → image behind element

```css
div { background-image: url("img.jpg"); }
```

---

- **!important** → forces style override (avoid)

```css
p { color: red !important; }
```

# JavaScript ~

## **BASICS ⚡~**

- `console.log()` → print output 🖥️
- **Comments** → `//` (single), `/* */` (multi) 📝

**Data Types (8):**

- Number, BigInt, String, Boolean, Null, Undefined, Symbol, Object

**Basics:**

- Number → no quotes
- String → `'text'`

**Operators:**

- `+ - * / %`
- `+` with strings → **concatenation**

**Properties & Methods:**

- `.length` → property 📏
- `.toUpperCase()` → method 🔧
- Use `.` (dot operator)

**Built-in Objects:**

- `Math.random()` → random number 🎲
- `Math.floor()` → round down

---

## **Variables ~**

- **Variables = storage with name** 📦
- Keywords:
    - `let` → can change 🔁
    - `const` → cannot change 🚫
    - `var` → old (avoid)

👉 Example:

```jsx
let age = 20;
const name = 'John';
```

- Not assigned → `undefined`

👉 Operators:

```jsx
age += 5; // same as age = age + 5
```

- **String concat:**

```jsx
let a = 'Hello';
let b = 'World';
console.log(a + ' ' + b);
```

- **Template literals (ES6):**

```jsx
console.log(`Hello ${name}`);
```

- **typeof:**

```jsx
console.log(typeof age); // number
```

---

**⚠️ Important (don’t ignore):**

```jsx
console.log(test1);
const test1 = 'abc';
```

❌ Error → **cannot access before initialization**

👉 `let` & `const` are NOT hoisted like `var`

---

## Conditional Statements ~

- `if` → runs if condition is **true** ✅
- `if...else` → 2 outcomes
- `else if` → multiple conditions

👉 Comparison:

- `< > <= >= === !==`

👉 Logical:

- `&&` → both true
- `||` → at least one true
- `!` → reverse (true ↔ false)

👉 Ternary (shortcut):

```jsx
condition ? value1 : value2;
```

👉 Switch:

```jsx
switch(x) {
  case 1: break;
}
```

---

## **Functions**

- **Function = reusable code block** 🔁

👉 **Declaration:**

```jsx
function greet() {
  console.log('Hello');
}
```

👉 **Call:**

```jsx
greet();
```

---

**Parameters & Arguments 🧠**

```jsx
function add(a, b) {
  return a + b;
}
```

---

**Types:**

1. **Function Expression**

```jsx
const add = function(a, b) {
  return a + b;
};
```

1. **Arrow Function (ES6)**

```jsx
const add = (a, b) => a + b;
```

---

**Key Concepts ⚡**

- `return` → gives output
- Default params:

```jsx
function greet(name = 'Guest') {}
```

---

## Arrays

### 🔹 1. Definition

👉 Array = ordered list of data

```jsx
let arr = [1, 2, 3];
```

---

### 🔹 2. Indexing

- Starts from **0**

```jsx
arr[0] // first element
```

---

### 🔹 3. Access & Update

```jsx
arr[1];       // access
arr[1] = 10;  // update
```

---

### 🔹 4. Length

```jsx
arr.length
```

👉 Total elements

👉 Last index = `length - 1`

---

### 🔹 5. Important Methods

### ✅ Mutating (change original)

```jsx
arr.push(x);    // add end
arr.pop();      // remove last
arr.shift();    // remove first
arr.unshift(x); // add start
arr.splice();   // add/remove anywhere
```

---

### ✅ Non-mutating

```jsx
arr.slice();    // copy part
arr.concat();   // merge arrays
arr.join();     // array → string
```

---

### 🔹 6. Return behavior

- `.push()` → returns **new length**
- `.pop()` → returns **removed element**

---

### 🔹 7. `let` vs `const`

```jsx
const arr = [1,2];
arr[0] = 5; // ✅ allowed
arr = [3,4]; // ❌ not allowed
```

---

### 🔹 8. Arrays in Functions

👉 Passed by reference

```jsx
function f(a){
  a.push(10);
}
```

👉 Original array changes

---

### 🔹 9. Nested Arrays

```jsx
arr[1][0]
```

---

### 🔹 10. Looping

```jsx
for (let i = 0; i < arr.length; i++) {
  console.log(arr[i]);
}
```

---

### ⚠️ Common Mistakes

- Using `<= arr.length` ❌
- Thinking index starts from 1 ❌
- Confusing return value of `.push()`

---

## Objects

---

### 🔹 What is an Object

👉 **One-line:** _An object is a collection of named data (key → value)._

```jsx
const obj = { name: 'John', age: 20 };
```

---

### 🔹 Properties & Methods

👉 **One-line:** _Properties store data, methods define behavior._

```jsx
const obj = {
  name: 'John',
  greet() {
    console.log('Hi');
  }
};
```

---

### 🔹 Accessing Values

👉 **One-line:** _Use dot for fixed keys, bracket for dynamic keys._

```jsx
obj.name        // 'John'
obj['name']     // 'John'

const key = 'name';
obj[key];       // 'John'
```

---

### 🔹 Add / Update

👉 **One-line:** _Objects can be modified anytime._

```jsx
obj.city = 'Delhi';
obj.age = 25;
```

---

### 🔹 Nested Objects

👉 **One-line:** _Objects can contain other objects._

```jsx
const obj = {
  inner: { value: 10 }
};

obj.inner.value; // 10
```

---

### 🔹 `this` Keyword

👉 **One-line:** `*this` refers to the object calling the method.*

```jsx
const obj = {
  name: 'John',
  greet() {
    console.log(this.name);
  }
};
```

---

### 🔹 Arrow Function Warning

👉 **One-line:** _Arrow functions don’t bind `this` to the object._

```jsx
const obj = {
  name: 'John',
  greet: () => console.log(this.name) // ❌ undefined
};
```

---

### 🔹 Mutability

👉 **One-line:** _Objects can change even if declared with `const`._

```jsx
const obj = { a: 1 };
obj.a = 2; // ✅
```

---

### 🔹 Pass by Reference

👉 **One-line:** _Objects share memory when passed to functions._

```jsx
function change(o) {
  o.a = 10;
}

const obj = { a: 1 };
change(obj);

console.log(obj.a); // 10
```

---

### 🔹 Looping (`for...in`)

👉 **One-line:** _Loops through object keys._

```jsx
for (let key in obj) {
  console.log(key, obj[key]);
}
```

---

### 🔹 Privacy (Convention)

👉 **One-line:** `*_` means “don’t modify directly” (just a convention).*

```jsx
const obj = { _value: 100 };
```

---

### 🔹 Getters

👉 **One-line:** _Getter = controlled way to read data._

```jsx
const obj = {
  _val: 10,
  get val() {
    return this._val;
  }
};

obj.val; // 10
```

---

### 🔹 Setters

👉 **One-line:** _Setter = controlled way to update data._

```jsx
const obj = {
  _val: 10,
  set val(x) {
    this._val = x;
  }
};

obj.val = 20;
```

---

### 🔹 Factory Functions

👉 **One-line:** _Functions that create and return objects._

```jsx
const createUser = (name) => {
  return { name };
};

const user = createUser('John');
```

---

### 🔹 Property Shorthand

👉 **One-line:** _If key and variable name are same, write once._

```jsx
const name = 'John';
const obj = { name };
```

---

### 🔹 Destructuring

👉 **One-line:** _Extract values from object into variables._

```jsx
const obj = { name: 'John' };
const { name } = obj;
```

---

### 🔹 Built-in Methods

👉 **One-line:** _Built-in functions to work with objects._

```jsx
Object.keys(obj);      // ['name']
Object.entries(obj);   // [['name','John']]
Object.assign({}, obj);
```

---

## ⚠️ Common Mistakes

- Using arrow function with `this` ❌
- Using dot instead of bracket for variables ❌
- Expecting objects to be ordered ❌

---

## Iterators ~

|Method|Syntax|Purpose|Returns|Special Case|Common Use|Example|
|---|---|---|---|---|---|---|
|`.forEach()`|`arr.forEach(cb)`|Executes code for every element|`undefined`|Cannot break/return new array|Printing, side effects|`arr.forEach(x => console.log(x))`|
|`.map()`|`arr.map(cb)`|Transforms elements|New array|Original array unchanged|Modify data|`arr.map(x => x * 2)`|
|`.filter()`|`arr.filter(cb)`|Keeps matching elements|Filtered array|Callback must return true/false|Filtering data|`arr.filter(x => x > 5)`|
|`.findIndex()`|`arr.findIndex(cb)`|Finds first matching index|Index / `-1`|Stops at first match|Searching position|`arr.findIndex(x => x < 10)`|
|`.reduce()`|`arr.reduce(cb, init)`|Reduces array → single value|Single value|2nd argument = initial accumulator|Sum, max, totals|`arr.reduce((a,b)=>a+b,0)`|
|`.some()`|`arr.some(cb)`|Checks if at least one matches|`true/false`|Stops at first true|Validation|`arr.some(x => x < 0)`|
|`.every()`|`arr.every(cb)`|Checks if all match|`true/false`|Stops at first false|Validation|`arr.every(x => x > 0)`|

---

### Callback Function ~

|Concept|Meaning|Example|
|---|---|---|
|Callback Function|Function passed into another function|`arr.map(x => x*2)`|
|Higher-Order Function|Function taking/returning function|`.map(), .filter()`|

---

### `.reduce()` Flow ~

|Iteration|accumulator|currentValue|Return|
|---|---|---|---|
|1|0|1|1|
|2|1|2|3|
|3|3|3|6|

```jsx
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

## DOM Manipulation~

|Purpose|Method|Example|Returns/Effect|
|---|---|---|---|
|Access DOM Root|`document`|`document`|Entire webpage DOM|
|Select First Matching Element|`querySelector()`|`document.querySelector('p')`|First `<p>`|
|Select by Class|`querySelector()`|`document.querySelector('.card')`|First element with class `card`|
|Select by ID|`querySelector()`|`document.querySelector('#logo')`|Element with id `logo`|
|Select by ID|`getElementById()`|`document.getElementById('logo')`|Single element|
|Select by Class|`getElementsByClassName()`|`document.getElementsByClassName('student')`|Collection of elements|
|Select by Tag|`getElementsByTagName()`|`document.getElementsByTagName('li')`|Collection of elements|
|Access Element from Collection|`[]`|`document.getElementsByTagName('li')[0]`|First `<li>`|
|Change Content|`innerHTML`|`element.innerHTML = 'Hello'`|Updates element content|
|Change Text|`textContent`|`element.textContent = 'Hello'`|Updates text only|
|Change Color|`style.color`|`element.style.color = 'red'`|Changes text color|
|Change Background|`style.backgroundColor`|`element.style.backgroundColor = 'black'`|Changes background|
|Change Font Size|`style.fontSize`|`element.style.fontSize = '30px'`|Changes font size|
|Change Font Family|`style.fontFamily`|`element.style.fontFamily = 'Roboto'`|Changes font|
|Create Element|`createElement()`|`document.createElement('p')`|Creates `<p>`|
|Set ID|`id`|`element.id = 'info'`|Adds ID|
|Append Element|`appendChild()`|`document.body.appendChild(p)`|Adds as last child|
|Remove Element|`removeChild()`|`parent.removeChild(child)`|Removes child|
|Get Children|`children`|`document.body.children`|Collection of direct children|
|Get First Child|`children[index]`|`document.body.children[0]`|First child element|
|Get Parent|`parentNode`|`element.parentNode`|Parent element|
|Click Event|`onclick`|`button.onclick = () => {}`|Runs on click|

### `querySelector()` Quick Reference

|HTML|JavaScript|
|---|---|
|`<p>`|`document.querySelector('p')`|
|`<h1>`|`document.querySelector('h1')`|
|`class="card"`|`document.querySelector('.card')`|
|`class="btn"`|`document.querySelector('.btn')`|
|`id="logo"`|`document.querySelector('#logo')`|
|`id="main"`|`document.querySelector('#main')`|

### Create → Modify → Insert Pattern

```jsx
const p = document.createElement('p');
p.innerHTML = 'Hello World';
document.body.appendChild(p);
```

**Flow:**

```
Create Element
↓
Add Content/Style
↓
Append to DOM
↓
Visible on Page
```

### Parent & Child Relationship

```html
<body>
  <h1>Hello</h1>
</body>
```

```jsx
document.body.children[0]    // <h1>
document.body.children[0].parentNode // <body>
```

### Memory Tricks

|Symbol|Meaning|
|---|---|
|`'p'`|Tag/Element|
|`'.card'`|Class|
|`'#logo'`|ID|

### Most used in real projects:

````jsx
document.querySelector()
document.querySelectorAll()
element.innerHTML
element.textContent
element.style
document.createElement()
element.appendChild()
``` 🚀
````

## HTML Forms ~

### Form Structure

```html
<form action="/submit" method="POST">

</form>
```

|Attribute|Purpose|
|---|---|
|`action`|Where form data goes|
|`method`|How data is sent (`GET` / `POST`)|

---

### Label + Input

```html
<label for="username">Username</label>
<input id="username" name="username" type="text">
```

#### Rule

```
for === id
```

Clicking the label focuses the input.

---

### id vs name vs value

```html
<input
  id="username"
  name="username"
  value="Captain"
>
```

|Attribute|Purpose|
|---|---|
|`id`|Locator (CSS, JS, Label)|
|`name`|Key sent to server|
|`value`|Actual data|

Form submits:

```
username=Captain
```

---

### Input Types

### Text

```html
<input type="text">
```

Used for:

```
Username
Name
City
```

---

### Password

```html
<input type="password">
```

Displays:

```
********
```

---

### Number

```html
<input
  type="number"
  min="1"
  max="10"
  step="1"
>
```

|Attribute|Purpose|
|---|---|
|`min`|Smallest value|
|`max`|Largest value|
|`step`|Increment amount|

---

### Range (Slider)

```html
<input
  type="range"
  min="0"
  max="100"
  step="1"
>
```

```
0 ----●---- 100
```

Used for:

```
Volume
Brightness
Ratings
```

---

### Checkbox

```html
<input
  type="checkbox"
  name="topping"
  value="cheese"
>
```

```
☑ Cheese
☑ Onion
☑ Mushroom
```

✅ Multiple selections allowed

---

### Radio Button

```html
<input
  type="radio"
  name="gender"
  value="male"
>
```

```
◉ Male
○ Female
```

✅ One selection only

#### Rule

```
Same name
↓
Same group
↓
Only one selected
```

---

### Dropdown

```html
<select name="food">
  <option value="pizza">Pizza</option>
  <option value="burger">Burger</option>
</select>
```

User sees:

```
Pizza
Burger
```

Server receives:

```
food=pizza
```

---

### Datalist

```html
<input list="cities">

<datalist id="cities">
  <option value="Tokyo">
  <option value="Paris">
</datalist>
```

Features:

```
Searchable
Suggestions
Can type custom value
```

#### Difference

|Select|Datalist|
|---|---|
|Must choose option|Can choose or type own value|
|No search|Search available|

---

### Textarea

```html
<textarea
  id="comment"
  name="comment"
  rows="5"
  cols="30">
</textarea>
```

Used for:

```
Comments
Reviews
Feedback
Blog Posts
```

### Default Text

```html
<textarea>
Write here...
</textarea>
```

---

### Submit Button

```html
<input
  type="submit"
  value="Send"
>
```

Flow:

```
Fill Form
↓
Click Submit
↓
Send Data
```

---

### Validation

#### Required

```html
<input required>
```

```
Empty?
↓
Cannot Submit ❌
```

---

### Min / Max

```html
<input
  type="number"
  min="1"
  max="10"
>
```

Allowed:

```
1–10
```

---

### Minlength / Maxlength

```html
<input
  minlength="3"
  maxlength="15"
>
```

Allowed:

```
3–15 characters
```

---

### Pattern (Regex)

```html
<input pattern="[0-9]{6}">
```

Valid:

```
123456 ✅
```

Invalid:

```
abc123 ❌
```

---

### Common Regex Patterns

#### 6 Digit PIN

```html
pattern="[0-9]{6}"
```

#### 5 Digit ZIP

```html
pattern="[0-9]{5}"
```

#### Credit Card

```html
pattern="[0-9]{14,16}"
```

#### Letters Only

```html
pattern="[a-zA-Z]+"
```

---

### Validation Order

```
required
↓
min/max
↓
minlength/maxlength
↓
pattern
↓
Pass?
↓
Submit ✅
```

---

### Most Important Interview/Revision Points

```
<form>      → Form container

<label>     → Describes input

for = id    → Connects label and input

id          → Locator

name        → Sent to server

value       → Actual data

Checkbox    → Many choices

Radio       → One choice

Select      → Dropdown

Datalist    → Searchable dropdown

Textarea    → Multiline input

Submit      → Sends form

required    → Cannot be empty

pattern     → Regex validation
```

## Classes & OOP 🚀

### Core Concepts

|Concept|Syntax|Purpose|
|---|---|---|
|Class|`class Dog {}`|Blueprint for objects|
|Constructor|`constructor()`|Runs automatically when object is created|
|Instance|`new Dog()`|Creates object from class|
|`this`|`this._name = name`|Refers to current object|
|Getter|`get name(){}`|Read property|
|Setter|`set name(value){}`|Update property|
|Method|`bark(){}`|Perform action|
|Inheritance|`extends`|Child inherits parent|
|Super|`super()`|Calls parent constructor|
|Static Method|`static method(){}`|Called on class itself|

---

### Class Template

```jsx
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

---

### Creating Instances

```jsx
const dog1 = new Dog('Max');
```

Flow:

```
Class
↓
new
↓
Constructor runs
↓
Object created
```

---

### Constructor

```jsx
constructor(name) {
  this._name = name;
}
```

Purpose:

```
Initialize object properties
```

Example:

```jsx
const dog = new Dog('Rocky');
```

Result:

```jsx
{
  _name: 'Rocky'
}
```

---

### this Keyword

```jsx
this._name = name;
```

Means:

```
Current object's _name property
```

Example:

```jsx
dog1._name
```

↓

```
'Max'
```

---

### Getters

#### Syntax

```jsx
get name() {
  return this._name;
}
```

Usage:

```jsx
dog.name
```

NOT:

```jsx
dog.name()
```

Getter automatically runs.

---

### Setters

#### Syntax

```jsx
set name(newName) {
  this._name = newName;
}
```

Usage:

```jsx
dog.name = 'Rocky';
```

Setter automatically runs.

---

### Getter vs Setter

|Operation|Syntax|
|---|---|
|Read|`dog.name`|
|Update|`dog.name = 'Rocky'`|

---

### Methods

#### Syntax

```jsx
bark() {
  console.log('Woof');
}
```

Usage:

```jsx
dog.bark();
```

Methods perform actions.

---

### Inheritance

#### Parent Class

```jsx
class Animal {
  constructor(name) {
    this._name = name;
  }
}
```

#### Child Class

```jsx
class Cat extends Animal {

}
```

Meaning:

```
Cat inherits Animal
```

---

### Extends

```jsx
class Cat extends Animal
```

Child automatically gets:

```
Properties ✅
Getters ✅
Setters ✅
Methods ✅
```

---

### super()

#### Syntax

```jsx
super(name);
```

Purpose:

```
Call parent constructor
```

Example:

```jsx
class Cat extends Animal {
  constructor(name, usesLitter) {
    super(name);
    this._usesLitter = usesLitter;
  }
}
```

Flow:

```
Cat constructor
↓
super(name)
↓
Animal constructor
↓
_name initialized
↓
Back to Cat constructor
↓
_usesLitter initialized
```

---

### What Goes Inside super()?

#### Rule

```
Pass values needed by parent constructor
```

Parent:

```jsx
constructor(name, level, students)
```

Child:

```jsx
super(name, level, students);
```

---

Example:

```jsx
super(name, 'primary', students);
```

because level is always primary.

---

### Child-Specific Properties

```jsx
class Cat extends Animal {
  constructor(name, usesLitter) {
    super(name);
    this._usesLitter = usesLitter;
  }
}
```

Rule:

```
Parent properties
↓
super()

Child properties
↓
this._property
```

---

### Static Methods

#### Syntax

```jsx
static generateName() {

}
```

Call:

```jsx
Animal.generateName();
```

NOT:

```jsx
const dog = new Animal();

dog.generateName(); // ❌
```

---

#### Example

```jsx
class School {
  static pickSubstituteTeacher(teachers) {
    const index =
      Math.floor(Math.random() * teachers.length);

    return teachers[index];
  }
}
```

Usage:

```jsx
School.pickSubstituteTeacher([...]);
```

---

### Static vs Normal Methods

|Normal Method|Static Method|
|---|---|
|`obj.method()`|`Class.method()`|
|Needs object|No object needed|
|Uses instance data|Usually utility/helper|

---

### Common Patterns

#### Toggle Boolean

```jsx
this._isCheckedOut = !this._isCheckedOut;
```

```
true → false
false → true
```

---

#### Add Item To Array

```jsx
this._ratings.push(rating);
```

```
Add at end of array
```

---

#### Average Using reduce()

```jsx
const total =
  this.ratings.reduce(
    (sum, rating) => sum + rating,
    0
  );

return total / this.ratings.length;
```

Flow:

```
Array
↓
reduce()
↓
Sum
↓
Divide by length
↓
Average
```

---

### OOP Master Flow

```
Class
↓
Constructor
↓
new
↓
Instance/Object
↓
Getter / Setter / Methods
↓
Inheritance (extends)
↓
super()
↓
Static Methods
```

---

## JavaScript Modules 📦

### Why Modules?

```
Large Program
↓
Break into small files
↓
Modules
```

Benefits:

- Better organization
- Reusable code
- Easier debugging
- Separation of concerns
- Avoid global namespace pollution

---

### Module Basics

A module is simply a JavaScript file that can:

```
Export code
↓
Import code
```

---

### export

Makes code available outside the current file.

### Export Variable

```jsx
export const age = 20;
```

### Export Function

```jsx
export const greet = () => {
  console.log('Hello');
};
```

### Export Class

```jsx
export class Dog {

}
```

---

### Named Exports

Allows multiple exports from one file.

### module.js

```jsx
export const greet = () => {
  console.log('Hello');
};

export const bye = () => {
  console.log('Bye');
};
```

### Import

```jsx
import { greet, bye } from './module.js';
```

---

### Alternative Named Export Syntax

### Export Later

```jsx
const greet = () => {};
const bye = () => {};

export { greet, bye };
```

---

### Named Import

### Syntax

```jsx
import { name } from './file.js';
```

Example:

```jsx
import { greet } from './module.js';
```

---

### Renaming Imports

Useful when two modules export the same name.

### Export

```jsx
export const greet = () => {};
```

### Import

```jsx
import { greet as hello } from './module.js';
```

Now use:

```jsx
hello();
```

---

### Default Export

Exports one main value from a module.

### Syntax

```jsx
export default value;
```

Example:

```jsx
const colors = ['red', 'blue', 'green'];

export default colors;
```

---

### Default Import

### Syntax

```jsx
import anythingYouWant from './module.js';
```

Example:

```jsx
import colors from './module.js';
```

or

```jsx
import myColors from './module.js';
```

Both work.

---

### Named vs Default Export

|Named Export|Default Export|
|---|---|
|Many per file|One per file|
|Uses `{}` when importing|No `{}`|
|Name must match|Any name works|
|`export const x = ...`|`export default x`|

---

### Exporting an Object

```jsx
const resources = {
  greet,
  bye
};

export default resources;
```

Import:

```jsx
import resources from './module.js';
```

Usage:

```jsx
resources.greet();
```

---

### Destructuring Imported Object

```jsx
import resources from './module.js';

const { greet, bye } = resources;
```

---

### Module Script

When using modules in HTML:

```html
<script type="module" src="./main.js"></script>
```

NOT:

```html
<script src="./main.js"></script>
```

---

### Relative Paths

### Same Folder

```jsx
import { greet } from './module.js';
```

### Parent Folder

```jsx
import { greet } from '../module.js';
```

Meaning:

```
./
↓
Current folder

../
↓
One folder up
```

---

### Module Flow

```
module.js
↓
export

main.js
↓
import

Use functions/classes/variables
```

---

## JavaScript Error Handling 🚨

### Why Error Handling?

There are two kinds of mistakes:

|Type|Program Runs?|
|---|---|
|Logic Error|✅ Yes|
|Runtime Error|❌ No|

Example Runtime Error:

```jsx
const age = 20;
age = 30;
```

Output:

```
TypeError: Assignment to constant variable.
```

Program stops.

---

### Error Handling Goal

```
Error occurs
↓
Handle it safely
↓
Program continues running
```

---

### Error Objects

JavaScript errors are objects.

Properties:

|Property|Purpose|
|---|---|
|name|Error type|
|message|Error description|

Example:

```jsx
const error = new Error('Weak password');

console.log(error.name);
console.log(error.message);
```

Output:

```
Error
Weak password
```

---

### Creating Custom Errors

### Syntax

```jsx
new Error('message')
```

or

```jsx
Error('message')
```

Example:

```jsx
const error =
  new Error('Password too weak');
```

Creates an error object.

Program still runs.

---

### Common Built-in Errors

### ReferenceError

Variable not found.

```jsx
console.log(age);
```

Output:

```
ReferenceError
```

---

### TypeError

Invalid operation.

```jsx
const age = 20;

age = 30;
```

Output:

```
TypeError
```

---

### throw Keyword

### Syntax

```jsx
throw Error('message');
```

Example:

```jsx
throw Error('Invalid Password');
```

Output:

```
Error: Invalid Password
```

Program stops immediately.

---

### Creating vs Throwing

### Creating

```jsx
new Error('Oops');
```

```
Creates error object
Program continues
```

---

### Throwing

```jsx
throw Error('Oops');
```

```
Throws error
Program stops
```

---

### try...catch

Used to handle errors.

### Syntax

```jsx
try {
  // risky code
} catch(e) {
  // handle error
}
```

---

### Example

```jsx
try {
  throw Error('Wrong password');
} catch(e) {
  console.log(e.message);
}

console.log('Program continues');
```

Output:

```
Wrong password
Program continues
```

---

### try...catch Flow

```
try
↓
Run code
↓
Error?
├─ No → Continue
└─ Yes
     ↓
   catch(e)
     ↓
 Handle error
     ↓
 Continue program
```

---

### Error Parameter

```jsx
catch(e)
```

`e` contains the error object.

Example:

```jsx
catch(e) {
  console.log(e.name);
  console.log(e.message);
}
```

---

### Handling Built-in Errors

```jsx
const text = 'Hello';

try {
  text = 'World';
} catch(e) {
  console.log(e.message);
}
```

Output:

```
Assignment to constant variable.
```

Program continues.

---

### Access Error Information

### Error Name

```jsx
e.name
```

Example:

```
TypeError
ReferenceError
Error
```

---

### Error Message

```jsx
e.message
```

Example:

```
Assignment to constant variable.
```

---

### Why Use try...catch?

Useful when working with:

```
User Input
API Data
Database Data
External Files
```

Because data may not be what you expect.

---

## Async JavaScript Notes 🚀

### 1. Synchronous vs Asynchronous

#### Synchronous (Blocking)

```jsx
console.log("A");
console.log("B");
console.log("C");
```

Output:

```
A
B
C
```

Runs line by line.

---

#### Asynchronous (Non-Blocking)

```jsx
setTimeout(() => {
  console.log("B");
}, 1000);

console.log("A");
```

Output:

```
A
B
```

JavaScript continues execution without waiting.

---

### 2. JavaScript is Single Threaded

```
One Call Stack
↓
One task at a time
```

Uses:

```
Event Loop
+
Web APIs
+
Event Queue
```

to handle async tasks.

---

### 3. Event Loop

```
Call Stack
↓
Web APIs
↓
Event Queue
↓
Event Loop
↓
Call Stack
```

---

### 4. setTimeout()

Syntax:

```jsx
setTimeout(callback, delay);
```

Example:

```jsx
setTimeout(() => {
  console.log("Hello");
}, 1000);
```

Runs after ~1 second.

---

### 5. setInterval()

Syntax:

```jsx
setInterval(callback, delay);
```

Example:

```jsx
setInterval(() => {
  console.log("Hello");
}, 1000);
```

Runs repeatedly every second.

---

### PROMISES

### 6. What is a Promise?

A Promise is an object representing the future result of an async operation.

---

### 7. Promise States

```
Pending ⏳
↓
Fulfilled ✅

OR

Rejected ❌
```

---

### 8. Creating a Promise

```jsx
const promise = new Promise((resolve, reject) => {

});
```

---

### 9. resolve()

```jsx
resolve("Success");
```

```
Pending
↓
Fulfilled
```

---

### 10. reject()

```jsx
reject("Error");
```

```
Pending
↓
Rejected
```

---

### 11. Executor Function

```jsx
const executor = (resolve, reject) => {

};

const promise = new Promise(executor);
```

Runs automatically.

---

### CONSUMING PROMISES

### 12. .then()

```jsx
promise.then((value) => {
  console.log(value);
});
```

Handles success.

---

### 13. Success & Failure Handlers

```jsx
promise.then(
  (value) => {
    console.log(value);
  },
  (error) => {
    console.log(error);
  }
);
```

```
resolve() → first callback
reject() → second callback
```

---

### 14. .catch()

```jsx
promise
  .then((value) => {
    console.log(value);
  })
  .catch((error) => {
    console.log(error);
  });
```

Handles failures.

---

### PROMISE CHAINING

### 15. Chaining

```jsx
promise1()
  .then((result1) => {
    return promise2(result1);
  })
  .then((result2) => {
    console.log(result2);
  });
```

Use when:

```
Task 2 depends on Task 1
```

---

### 16. Common Mistakes

#### ❌ Nesting

```jsx
.then(() => {
  promise2().then(...)
})
```

---

#### ❌ Forgetting return

```jsx
.then(() => {
  promise2();
})
```

---

#### ✅ Correct

```jsx
.then(() => {
  return promise2();
})
.then(...)
```

---

### PROMISE.ALL

### 17. Promise.all()

```jsx
Promise.all([
  promise1,
  promise2,
  promise3
]);
```

---

#### Success

```jsx
const values = await Promise.all([
  p1,
  p2,
  p3
]);
```

Returns:

```jsx
[value1, value2, value3]
```

---

#### Failure

```
Any Promise Fails
↓
Promise.all Rejects
```

---

### ASYNC / AWAIT

### 18. async Function

```jsx
async function example() {

}
```

Always returns a Promise.

---

### 19. await

```jsx
const value = await promise;
```

```
Wait
↓
Promise Resolves
↓
Return Value
```

---

#### Without await

```jsx
const value = promise();
```

Gets:

```
Promise { <pending> }
```

---

#### With await

```jsx
const value = await promise();
```

Gets:

```
Resolved Value
```

---

### 20. Dependent Promises

Old:

```jsx
promise1()
  .then(...)
  .then(...)
```

New:

```jsx
async function example() {
  const a = await promise1();
  const b = await promise2(a);
}
```

---

### 21. Error Handling

```jsx
async function example() {
  try {
    const result = await promise;
  } catch(err) {
    console.log(err);
  }
}
```

```
try   = success path
catch = error path
```

---

### 22. Independent Promises

#### ❌ Slow

```jsx
await p1();
await p2();
```

---

#### ✅ Better

```jsx
const p1Promise = p1();
const p2Promise = p2();

await p1Promise;
await p2Promise;
```

Starts both together.

---

### 23. await Promise.all()

```jsx
const results = await Promise.all([
  promise1(),
  promise2(),
  promise3()
]);
```

Best for:

```
Independent Promises
```

---

### Quick Revision Sheet

```
setTimeout()     → Delay execution

Promise States:
Pending
Fulfilled
Rejected

resolve()        → Success
reject()         → Failure

.then()          → Success handler
.catch()         → Failure handler

Promise Chaining → Dependent tasks

Promise.all()    → Concurrent tasks

async            → Creates async function

await            → Wait for Promise result

try...catch      → Handle async errors

Independent Tasks
↓
Promise.all()

Dependent Tasks
↓
Multiple awaits
```

# HTTP, APIs, JSON & REST Notes 🌐

## HTTP

### 1. What is HTTP?

**HTTP (HyperText Transfer Protocol)** is the protocol used for communication between a **client** (browser) and a **server**.

### Flow

```
Browser (Client)
      ↓ Request
Server
      ↓ Response
Browser
```

### Example

```
You type:
www.codecademy.com

Browser sends:
HTTP Request

Server sends:
HTTP Response
```

### Simple Definition

HTTP is the set of rules that allows a browser and server to communicate over the internet.

### Real-Life Example

```
You (Client)
↓ Order Food
Restaurant (Server)
↓ Sends Food
You receive Food
```

Similarly:

```
Browser
↓ Request Webpage
Server
↓ Sends Webpage
Browser displays it
```

Example:

```
You type:
www.codecademy.com

Browser sends:
HTTP Request

Server sends:
HTTP Response
```

---

### 2. HTTP Request & Response

### Request

```
GET / HTTP/1.1
Host: www.codecademy.com
```

### Response

```
HTTP/1.1 200 OK
Content-Type: text/html
```

---

### 3. HTTP vs HTTPS

### HTTP

```
Data is not encrypted ❌
```

### HTTPS

```
Data is encrypted ✅
```

Used for:

- Passwords
- Banking
- Credit cards
- Personal data

---

### 4. TCP

**TCP (Transmission Control Protocol)** establishes the connection between client and server.

```
HTTP = Communication Language
TCP = Connection Channel
```

---

## APIs

### 5. What is an API?

**API (Application Programming Interface)** allows one application to use another application's functionality or data.

Example:

```
Your App
   ↓
Weather API
   ↓
Weather Data
```

---

### 6. Types of APIs

### Browser APIs

Provided by browser.

Examples:

- Geolocation API
- Audio API
- Camera API

---

### Third-Party APIs

Provided by companies.

Examples:

- OpenWeather API
- Google Maps API
- Spotify API
- Facebook API

---

### 7. API Key

Many APIs require:

```
API Key
```

Used for:

- Authentication
- Rate limiting
- Tracking usage

Example:

```
<https://api.example.com?apikey=12345>
```

---

### 8. API Request Flow

```
App
↓
API Request
↓
Server
↓
JSON Response
↓
App Displays Data
```

---

## JSON

### 9. What is JSON?

**JSON (JavaScript Object Notation)** is a format used to store and exchange data.

Example:

```json
{
  "name": "Dhruv",
  "age": 19
}
```

---

### 10. JSON Rules

### Keys must use double quotes

✅

```json
{
  "name": "Dhruv"
}
```

❌

```json
{
  name: "Dhruv"
}
```

---

### No trailing commas

❌

```json
{
  "name": "Dhruv",
}
```

---

### 11. JSON Data Types

```
String
Number
Object
Array
Boolean
Null
```

Example:

```json
{
  "name": "Dhruv",
  "age": 19,
  "skills": ["C++", "JS"],
  "active": true,
  "college": null
}
```

---

### 12. JSON.parse()

Converts JSON → JavaScript Object

```jsx
const jsonData = '{"name":"Dhruv"}';

const obj = JSON.parse(jsonData);

console.log(obj.name);
```

Output:

```
Dhruv
```

---

### 13. JSON.stringify()

Converts JavaScript Object → JSON

```jsx
const obj = {
  name: "Dhruv"
};

const json = JSON.stringify(obj);
```

Output:

```json
{"name":"Dhruv"}
```

---

## REST API

### 14. What is REST?

**REST (Representational State Transfer)** is an architectural style used to build web APIs.

REST APIs are:

```
Stateless
Client-Server Based
Resource Based
```

---

### 15. REST Principles

### Separation of Client & Server

```
Frontend
↓
API
↓
Backend
```

Both can be developed independently.

---

### Statelessness

Server does not remember previous requests.

Each request contains all required information.

---

### 16. Resources

REST works with resources.

Examples:

```
/users
/products
/orders
/photos
```

Resources are nouns, not actions.

---

## HTTP Methods (Very Important)

### 17. GET

Retrieve data.

```
GET /users
```

Example:

```
Get all users
```

Success Code:

```
200 OK
```

---

### 18. POST

Create new resource.

```
POST /users
```

Example:

```
Create new user
```

Success Code:

```
201 CREATED
```

---

### 19. PUT

Update resource.

```
PUT /users/1
```

Example:

```
Update user 1
```

Success Code:

```
200 OK
```

---

### 20. DELETE

Delete resource.

```
DELETE /users/1
```

Example:

```
Delete user 1
```

Success Code:

```
204 NO CONTENT
```

---

## REST Paths

### Collection

```
GET /customers
```

Get all customers.

---

### Single Resource

```
GET /customers/123
```

Get customer with ID 123.

---

### Nested Resource

```
GET /customers/123/orders/12
```

Get order 12 of customer 123.

---

## MIME Types

### Common Content Types

```
text/html
text/css
application/json
image/png
image/jpeg
video/mp4
application/pdf
```

Example:

```
Content-Type: application/json
```

---

## Important Status Codes

### 200 OK

```
Request successful
```

---

### 201 CREATED

```
Resource created
```

---

### 204 NO CONTENT

```
Success but no data returned
```

---

### 400 BAD REQUEST

```
Invalid request
```

---

### 403 FORBIDDEN

```
No permission
```

---

### 404 NOT FOUND

```
Resource not found
```

---

### 500 INTERNAL SERVER ERROR

```
Server-side error
```

---

## Quick Revision Sheet

```
HTTP = Client ↔ Server communication

HTTPS = Secure HTTP

TCP = Connection channel

API = Access another application's data/functions

Browser API = Geolocation, Camera, Audio

Third Party API = Weather, Maps, Spotify

JSON = Data exchange format

JSON.parse() = JSON → JS Object

JSON.stringify() = JS Object → JSON

REST = API architecture

GET    = Read
POST   = Create
PUT    = Update
DELETE = Delete

200 = OK
201 = CREATED
204 = NO CONTENT
404 = NOT FOUND
500 = SERVER ERROR
```

# Requests with Fetch API 🚀

## Overview

This section taught how JavaScript communicates with APIs using:

- `fetch()`
- Promises
- `.then()`
- `.catch()`
- `async`
- `await`

---

## GET Requests

### Purpose

Retrieve data from a server.

Example:

```jsx
fetch(url)
```

Flow:

```
Client
↓ GET Request
Server
↓ Data
Client
```

---

### GET Request with Promises

```jsx
fetch(url)
  .then(response => {
    return response.json();
  })
  .then(data => {
    console.log(data);
  })
  .catch(error => {
    console.log(error);
  });
```

---

### GET Request with Async/Await

```jsx
async function getData() {
  try {
    const response = await fetch(url);
    const data = await response.json();

    console.log(data);
  } catch(error) {
    console.log(error);
  }
}
```

---

## POST Requests

### Purpose

Send data to a server.

Examples:

- Login
- Registration
- Forms
- Comments

---

### POST Request with Promises

```jsx
fetch(url, {
  method: 'POST',
  body: JSON.stringify({
    id: 200
  })
})
.then(response => response.json())
.then(data => {
  console.log(data);
})
.catch(error => {
  console.log(error);
});
```

---

### POST Request with Async/Await

```jsx
async function postData() {
  try {
    const response = await fetch(url, {
      method: 'POST',
      body: JSON.stringify({
        id: 200
      })
    });

    const data = await response.json();

    console.log(data);
  } catch(error) {
    console.log(error);
  }
}
```

---

## fetch()

### What is fetch()?

Used to make HTTP requests.

```jsx
fetch(url)
```

Returns:

```
Promise
```

---

### Request Lifecycle

```
fetch()
↓
Promise
↓
Response Object
↓
response.json()
↓
Actual Data
```

---

## Promises

### States

```
Pending
↓
Fulfilled
OR
Rejected
```

---

### Handling Promises

```jsx
.then()
.catch()
```

Example:

```jsx
fetch(url)
  .then(...)
  .catch(...);
```

---

## Response Object

### Important Properties

```jsx
response.ok
response.status
response.json()
```

---

### response.ok

```
true  → Success
false → Failure
```

Example:

```jsx
if(response.ok){
  return response.json();
}
```

---

### response.json()

Converts:

```json
{
  "name": "Dhruv"
}
```

↓

```jsx
{
  name: "Dhruv"
}
```

Returns a Promise.

---

## Error Handling

### Promise Style

```jsx
.catch(error => {
  console.log(error);
});
```

---

### Async/Await Style

```jsx
try {

} catch(error) {

}
```

---

## async Keyword

Creates an asynchronous function.

```jsx
async function getData() {

}
```

Async functions always return a Promise.

---

## await Keyword

Waits for a Promise to resolve.

```jsx
const data = await fetch(url);
```

Without await:

```jsx
const data = fetch(url);
```

Output:

```
Promise { <pending> }
```

With await:

```jsx
const data = await fetch(url);
```

Output:

```
Resolved Value
```

---

## GET vs POST

|GET|POST|
|---|---|
|Retrieve data|Send data|
|Read operation|Create operation|
|Usually no body|Requires body|

Example:

```jsx
// GET
fetch(url);
```

```jsx
// POST
fetch(url, {
  method: 'POST',
  body: JSON.stringify(data)
});
```

---

## Promise vs Async/Await

### Promise Style

```jsx
fetch(url)
  .then(...)
  .then(...)
  .catch(...)
```

---

### Async/Await Style

```jsx
try {
  const response = await fetch(url);
  const data = await response.json();
}
catch(error) {
  console.log(error);
}
```

---

## Quick Revision

```
fetch() → Makes HTTP Requests

GET → Retrieve Data

POST → Send Data

fetch() returns Promise

.then() → Handle Success

.catch() → Handle Errors

async → Create Async Function

await → Wait for Promise

response.ok → Check Success

response.json() → Convert JSON to JS Object

try...catch → Error Handling

POST requires:
method: 'POST'
body: JSON.stringify(data)
```

# Node.js

## 1. Introduction to Node.js

### 1.1 What is Node.js?

### Definition

- Node.js is a JavaScript Runtime Environment.
- Allows JavaScript to run outside the browser.
- Built on Chrome's V8 Engine.

### Running a JavaScript File

```bash
node app.js
```

---

### 1.2 REPL

### Definition

REPL =

```
Read
Evaluate
Print
Loop
```

### Starting REPL

```bash
node
```

### Example

```jsx
> 2 + 3
5
```

---

## 2. Modularity

### 2.1 Definition

### What is Modularity?

- Dividing a program into smaller modules/files.
- Each module handles a specific responsibility.

### Benefits

- Better organization
- Reusability
- Easier maintenance
- Scalability

---

### 2.2 Modules

### Definition

- A module is a file containing code.

### Importing Modules

```jsx
const moduleName = require('module_name');
```

### Example

```jsx
const events = require('events');
```

---

## 3. Core Modules

### 3.1 Definition

### What are Core Modules?

- Built into Node.js.
- No installation required.

### Examples

```
console
process
os
util
events
```

---

## 4. Console Module

### 4.1 Definition

### Purpose

- Used for terminal output and debugging.
- Global object (no import required).

---

### 4.2 Methods

### 4.2.1 console.log()

```jsx
console.log("Hello");
```

- Prints messages to terminal.

---

### 4.2.2 console.table()

```jsx
console.table(object);
```

- Displays data in table format.

---

### 4.2.3 console.assert()

```jsx
console.assert(false, "Error");
```

- Prints message when condition is false.

---

### 4.2.4 console.count()

```jsx
console.count("loop");
console.count("loop");
```

Output:

```
loop: 1
loop: 2
```

- Counts number of calls.

---

## 5. Process Module

### 5.1 Definition

### Purpose

- Provides information about the current Node.js process.
- Global object.

---

### 5.2 process.argv

### Purpose

Stores command-line arguments.

### Example

```bash
node app.js hello world
```

```jsx
console.log(process.argv);
```

Output:

```jsx
[
 '/usr/bin/node',
 '/app.js',
 'hello',
 'world'
]
```

### Important Indexes

```jsx
argv[0] // Node path
argv[1] // Current file path
argv[2+] // User arguments
```

---

### 5.3 process.env

### Purpose

Stores environment variables.

### Example

```jsx
console.log(process.env);
```

### Common Variable

```jsx
process.env.NODE_ENV
```

Values:

```
development
production
```

---

### 5.4 process.memoryUsage()

### Purpose

Returns memory usage statistics.

### Example

```jsx
console.log(process.memoryUsage());
```

### Important Property

```jsx
heapUsed
```

- Memory currently in use.

---

### 5.5 process.emitWarning()

### Purpose

Creates custom warnings.

### Example

```jsx
process.emitWarning("Testing warning");
```

---

## 6. OS Module

### 6.1 Definition

### Purpose

Provides information about:

- Operating System
- CPU Architecture
- Network Interfaces
- Host Machine

### Import

```jsx
const os = require('os');
```

---

### 6.2 Methods

### 6.2.1 os.type()

```jsx
os.type();
```

Returns:

```
Linux
Windows_NT
Darwin
```

---

### 6.2.2 os.arch()

```jsx
os.arch();
```

Returns:

```
x64
```

---

### 6.2.3 os.homedir()

```jsx
os.homedir();
```

Examples:

```
/home/dhruv
C:\Users\Dhruv
```

---

### 6.2.4 os.hostname()

```jsx
os.hostname();
```

Returns device/computer name.

---

### 6.2.5 os.uptime()

```jsx
os.uptime();
```

Returns seconds since last reboot.

---

### 6.2.6 os.networkInterfaces()

```jsx
os.networkInterfaces();
```

Returns:

- IP Address
- MAC Address
- Network Information

---

### 6.2.7 os.freemem()

```jsx
os.freemem();
```

Returns available RAM in bytes.

---

## 7. Util Module

### 7.1 Definition

### Purpose

Contains utility functions used for:

- Debugging
- Maintenance
- Type Checking

### Import

```jsx
const util = require('util');
```

---

### 7.2 util.types

### Purpose

Runtime type checking.

### Example

```jsx
util.types.isDate(new Date());
```

Output:

```
true
```

### Example

```jsx
util.types.isDate("April 22");
```

Output:

```
false
```

---

### 7.3 util.format()

### Purpose

Formats strings and objects.

### Example

```jsx
util.format("Hello %s", "Dhruv");
```

Output:

```
Hello Dhruv
```

---

### 7.4 util.promisify()

### Purpose

Converts callback-based functions into Promise-based functions.

### Example

```jsx
const getUserPromise =
util.promisify(getUser);
```

### Use Case

Used when converting older callback-style Node.js code into modern Promise-based code.

---

# Node.js Essentials 🟢

## 1. Modules

### Import Module

```jsx
const fs = require('fs');
```

### Idea

```
Module = Reusable code package
```

Examples:

```
fs
events
buffer
readline
```

---

## 2. Events

### Create EventEmitter

```jsx
const events = require('events');
const emitter = new events.EventEmitter();
```

### Listen

```jsx
emitter.on('login', callback);
```

### Trigger

```jsx
emitter.emit('login');
```

### Remember

```
.on()   → Listen

.emit() → Trigger
```

---

## 3. Input / Output

### Output

```jsx
console.log("Hello");
```

```jsx
process.stdout.write("Hello");
```

### Input

```jsx
process.stdin.on('data', (input) => {
  console.log(input.toString());
});
```

### Remember

```
stdin  → Input

stdout → Output
```

---

## 4. Errors

### Error Creation

```jsx
throw new Error("Oops");
```

### Error First Callback

```jsx
(err, data)
```

Example:

```jsx
readFile('file.txt', (err, data) => {
  if(err){
    console.log(err);
  }
});
```

### Remember

```
Async Node
↓
(err, data)
```

---

## 5. Buffers

### Create Empty Buffer

```jsx
Buffer.alloc(5);
```

### Create From String

```jsx
Buffer.from("hello");
```

### Convert To String

```jsx
buffer.toString();
```

### Merge Buffers

```jsx
Buffer.concat([buf1, buf2]);
```

### Remember

```
Buffer = Binary Data
```

---

## 6. FS Module

### Read File (Async)

```jsx
fs.readFile('file.txt', 'utf8', callback);
```

### Read File (Sync)

```jsx
fs.readFileSync('file.txt', 'utf8');
```

### Remember

```
fs = File System
```

---

## 7. Streams

### Create Stream

```jsx
fs.createReadStream('file.txt');
```

### Read Line By Line

```jsx
const readline = require('readline');

const myInterface = readline.createInterface({
  input: fs.createReadStream('file.txt')
});
```

### Listen

```jsx
myInterface.on('line', (line) => {
  console.log(line);
});
```

### Remember

```
readFile()
↓
Whole File

Stream
↓
Piece by Piece
```

---

## 8. Timers

### Run Once

```jsx
setTimeout(callback, 1000);
```

### Run Forever

```jsx
setInterval(callback, 1000);
```

### Run ASAP

```jsx
setImmediate(callback);
```

### Cancel

```jsx
clearTimeout(id);
clearInterval(id);
clearImmediate(id);
```

### Remember

```
Timeout  → Once

Interval → Repeat

Immediate → Next Event Loop
```

---

```
require()            → Import module

.on()                → Listen

.emit()              → Trigger

stdin                → Input

stdout               → Output

(err, data)          → Error-first callback

Buffer.alloc()       → Empty Buffer

Buffer.from()        → Buffer from string

buffer.toString()    → Buffer → Text

fs.readFile()        → Async file read

fs.readFileSync()    → Sync file read

createReadStream()   → Read gradually

setTimeout()         → Run once

setInterval()        → Run repeatedly

setImmediate()       → Run ASAP
```

# CommonJS Modules 🟢

## 1. What are Modules?

### 1.1 Definition

A module is a reusable file containing code.

```
One File
↓
Export Code
↓
Use In Other Files
```

### Why?

- Reuse code
- Avoid duplication
- Better organization
- Easier maintenance

---

## 2. CommonJS

### 2.1 Definition

Node.js uses **CommonJS Modules** by default.

Uses:

```jsx
module.exports
```

and

```jsx
require()
```

---

## 3. Exporting

### 3.1 Export Function

### shape-area.js

```jsx
function circleArea(radius) {
  return Math.PI * radius * radius;
}

module.exports.circleArea = circleArea;
```

---

### 3.2 Export Multiple Functions

```jsx
function circleArea(radius) {
  return Math.PI * radius * radius;
}

function squareArea(side) {
  return side * side;
}

module.exports.circleArea = circleArea;
module.exports.squareArea = squareArea;
```

---

### Remember

```
module.exports
↓
Send Outside File
```

---

## 4. Importing

### 4.1 Import Entire Module

### app.js

```jsx
const areaFunctions = require('./shape-area.js');
```

Use:

```jsx
areaFunctions.circleArea(5);
areaFunctions.squareArea(10);
```

---

### Flow

```
shape-area.js
     ↓
module.exports
     ↓
require()
     ↓
areaFunctions
```

---

## 5. Object Destructuring

### 5.1 Import Specific Functions

Instead of:

```jsx
const areaFunctions = require('./shape-area.js');

areaFunctions.circleArea();
```

Use:

```jsx
const { circleArea, squareArea } =
require('./shape-area.js');
```

Now:

```jsx
circleArea(5);
squareArea(10);
```

---

### Remember

```
Import Everything
↓
const obj = require()

Import Specific Things
↓
const { thing } = require()
```

---

## 6. Relative Paths

### Same Folder

```jsx
require('./shape-area.js');
```

Meaning:

```
Current Folder
```

---

### Parent Folder

```jsx
require('../shape-area.js');
```

Meaning:

```
Go Up One Folder
```

---

## 7. Example

### shape-area.js

```jsx
function squareArea(side) {
  return side * side;
}

module.exports.squareArea = squareArea;
```

### app.js

```jsx
const { squareArea } =
require('./shape-area.js');

console.log(squareArea(10));
```

Output:

```
100
```

---

## 8. Revision

### Export

```jsx
module.exports.name = value;
```

### Import All

```jsx
const obj = require('./file');
```

### Import One

```jsx
const { name } = require('./file');
```

---

### The 3 Lines To Remember 🚀

```jsx
// Export
module.exports.add = add;

// Import All
const math = require('./math');

// Import One
const { add } = require('./math');
```

### Mind Map

```
CommonJS
│
├── module.exports
│      ↓
│   Export
│
├── require()
│      ↓
│   Import
│
└── { }
       ↓
Object Destructuring
```

# Express.js 🚀

---

# 1. Setup

Install:

```bash
npm install express
```

Import:

```jsx
const express = require('express');
```

Create app:

```jsx
const app = express();
```

Start server:

```jsx
app.listen(4000, () => {
  console.log('Server running');
});
```

### Flow

```
Express
   ↓
express()
   ↓
app
   ↓
app.listen()
```

---

# 2. First Route

```jsx
app.get('/', (req, res) => {
  res.send('Hello');
});
```

Request:

```
GET /
```

Response:

```
Hello
```

---

# 3. Route Structure

```jsx
app.METHOD(PATH, CALLBACK)
```

Example:

```jsx
app.get('/users', callback)
app.post('/users', callback)
app.put('/users/:id', callback)
app.delete('/users/:id', callback)
```

---

# 4. HTTP Methods

|Method|Purpose|
|---|---|
|GET|Read|
|POST|Create|
|PUT|Update|
|DELETE|Delete|

---

# 5. GET

Get all:

```jsx
app.get('/users', (req, res) => {
  res.send(users);
});
```

Get one:

```jsx
app.get('/users/:id', (req, res) => {
  res.send(user);
});
```

---

# 6. Route Parameters

Route:

```jsx
app.get('/users/:id')
```

Request:

```
/users/5
```

Access:

```jsx
req.params.id
```

↓

```jsx
'5'
```

### Rule

```jsx
req.params.xxx
```

gets value from URL.

---

# 7. Query Parameters

Request:

```
/users?name=dhruv&age=19
```

Access:

```jsx
req.query
```

↓

```jsx
{
  name: 'dhruv',
  age: '19'
}
```

### Rule

```jsx
req.query.xxx
```

gets value after `?`.

---

# 8. Sending Response

```jsx
res.send(data);
```

JSON:

```jsx
res.json(data);
```

---

# 9. Status Codes

```jsx
res.status(200).send();
```

Common:

|Code|Meaning|
|---|---|
|200|OK|
|201|Created|
|204|Deleted|
|400|Bad Request|
|404|Not Found|

---

# 10. POST

Create resource:

```jsx
app.post('/users', (req, res) => {
  users.push(req.query);
  res.status(201).send(req.query);
});
```

---

# 11. PUT

Update resource:

```jsx
app.put('/users/:id', (req, res) => {
  user.name = req.query.name;
  res.send(user);
});
```

---

# 12. DELETE

```jsx
app.delete('/users/:id', (req, res) => {
  users.splice(index, 1);
  res.status(204).send();
});
```

---

# 13. indexOf()

```jsx
const index = arr.indexOf(item);
```

Returns:

```
Found     → 0,1,2...
Not Found → -1
```

Check:

```jsx
if (index !== -1)
```

---

# 14. Dot vs Bracket Notation ⭐

Fixed key:

```jsx
user.name
```

Variable key:

```jsx
const key = 'name';

user[key]
```

Express examples:

```jsx
users[req.params.id]

battlefields[req.params.name]

currencies[req.params.name]
```

---

# 15. Middleware

Syntax:

```jsx
app.use((req, res, next) => {
  next();
});
```

### next()

```
Go to next middleware/route
```

---

# 16. JSON Middleware

```jsx
app.use(express.json());
```

Enables:

```jsx
req.body
```

---

# 17. Static Files

```jsx
app.use(express.static('public'));
```

Folder:

```
public/
 ├─ index.html
 ├─ style.css
```

Accessible directly.

---

# 18. Router

Create:

```jsx
const router = express.Router();
```

Route:

```jsx
router.get('/', ...);
router.post('/', ...);
```

Export:

```jsx
module.exports = router;
```

---

# 19. Mount Router

```jsx
app.use('/users', userRouter);
```

Meaning:

```
/users/*
   ↓
userRouter
```

Example:

```
/users
/users/1
/users/abc
```

↓

Handled by:

```jsx
userRouter
```

---

# 20. Router Flow

```
Request
   ↓
app.js
   ↓
app.use('/users', userRouter)
   ↓
userRouter
   ↓
router.get(...)
```

---

# Final Mental Model 🚀

```
Client
   ↓
Request
   ↓
Express Server
   ↓
Route Match
   ↓
req.params / req.query
   ↓
Logic
   ↓
res.send()
   ↓
Response
```

### Express Cheatsheet

```jsx
app.listen()

app.get()
app.post()
app.put()
app.delete()

req.params
req.query

res.send()
res.json()
res.status()

app.use()

express.Router()

app.use('/path', router)
```

# 21. Middleware Stack

Multiple middleware can run for one route.

```jsx
app.post(
  '/users',
  authenticate,
  validate,
  createUser
);
```

Flow

```
Request
   ↓
authenticate
   ↓ next()
validate
   ↓ next()
createUser
   ↓
Response
```

---

# 22. Route-Level Middleware

Run middleware only for specific paths.

```jsx
app.use('/books', middleware);
```

Matches:

```
/books
/books/1
/books/history
```

Multiple paths:

```jsx
app.use(
  ['/books', '/authors'],
  middleware
);
```

---

# 23. app.param()

Avoid duplicate parameter lookup.

```jsx
app.param('id', (req, res, next, id) => {
  req.user = getUser(id);
  next();
});
```

Now every route using

```jsx
:id
```

can access

```jsx
req.user
```

---

# 24. mergeParams

Child router can access parent parameters.

```jsx
const router = express.Router({
  mergeParams: true
});
```

Example

```
/users/:userId/posts
```

Inside posts router:

```jsx
req.params.userId
```

---

# 25. CORS

CORS = Cross-Origin Resource Sharing

Allows browsers to access resources from another origin.

Install

```bash
npm install cors
```

Use

```jsx
const cors = require('cors');

app.use(cors());
```

---

# 26. Same Origin

Origin consists of

```
Protocol
Host
Port
```

Example

```
<http://localhost:3000>

↓

<http://localhost:4000>
```

Different port ⇒ Different origin.

---

# 27. Preflight Request

Browser sends

```
OPTIONS
```

before

```
PUT
PATCH
DELETE
```

to check permission.

---

# 28. Morgan

Logging middleware.

Install

```bash
npm install morgan
```

Use

```jsx
const morgan = require('morgan');

app.use(morgan('dev'));
```

---

# 29. Error Handling Middleware

Must be the last middleware.

```jsx
app.use((err, req, res, next) => {
  res.status(500).send(err.message);
});
```

Pass an error:

```jsx
next(error);
```

---

# 30. Open-Source Middleware

Common packages

```jsx
express.json()    // Body parsing

morgan()          // Logging

cors()            // CORS

errorhandler()    // Error handling
```

---

# 31. Request Object

```jsx
req.params   // Route params

req.query    // Query params

req.body     // Request body

req.method   // GET, POST...

req.path     // URL path
```

---

# 32. Response Object

```jsx
res.send()

res.json()

res.status()

res.sendStatus()
```

---

# 33. DRY Principle

**Don't Repeat Yourself**

Instead of repeating logic:

```jsx
findUser();
findUser();
findUser();
```

Use:

- Middleware
- `app.param()`
- Functions
- Routers

---

# 34. Request Lifecycle

```
Client
   ↓
Request
   ↓
Middleware
   ↓
Route
   ↓
Business Logic
   ↓
Response
```

---