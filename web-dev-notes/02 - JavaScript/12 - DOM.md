# DOM Manipulation

## Core Methods

| Purpose | Method | Example | Returns/Effect |
| --- | --- | --- | --- |
| Access DOM Root | `document` | `document` | Entire webpage DOM |
| Select First Matching | `querySelector()` | `document.querySelector('p')` | First `<p>` |
| Select by Class | `querySelector()` | `document.querySelector('.card')` | First element with class `card` |
| Select by ID | `querySelector()` | `document.querySelector('#logo')` | Element with id `logo` |
| Select by ID | `getElementById()` | `document.getElementById('logo')` | Single element |
| Select by Class | `getElementsByClassName()` | `document.getElementsByClassName('student')` | Collection of elements |
| Select by Tag | `getElementsByTagName()` | `document.getElementsByTagName('li')` | Collection of elements |
| Access from Collection | `[]` | `document.getElementsByTagName('li')[0]` | First `<li>` |
| Change Content | `innerHTML` | `element.innerHTML = 'Hello'` | Updates element content |
| Change Text | `textContent` | `element.textContent = 'Hello'` | Updates text only |
| Change Color | `style.color` | `element.style.color = 'red'` | Changes text color |
| Change Background | `style.backgroundColor` | `element.style.backgroundColor = 'black'` | Changes background |
| Change Font Size | `style.fontSize` | `element.style.fontSize = '30px'` | Changes font size |
| Change Font Family | `style.fontFamily` | `element.style.fontFamily = 'Roboto'` | Changes font |
| Create Element | `createElement()` | `document.createElement('p')` | Creates `<p>` |
| Set ID | `id` | `element.id = 'info'` | Adds ID |
| Append Element | `appendChild()` | `document.body.appendChild(p)` | Adds as last child |
| Remove Element | `removeChild()` | `parent.removeChild(child)` | Removes child |
| Get Children | `children` | `document.body.children` | Collection of direct children |
| Get First Child | `children[index]` | `document.body.children[0]` | First child element |
| Get Parent | `parentNode` | `element.parentNode` | Parent element |
| Click Event | `onclick` | `button.onclick = () => {}` | Runs on click |

## querySelector() Quick Reference

| HTML | JavaScript |
| --- | --- |
| `<p>` | `document.querySelector('p')` |
| `<h1>` | `document.querySelector('h1')` |
| `class="card"` | `document.querySelector('.card')` |
| `class="btn"` | `document.querySelector('.btn')` |
| `id="logo"` | `document.querySelector('#logo')` |
| `id="main"` | `document.querySelector('#main')` |

## Create → Modify → Insert Pattern

```js
const p = document.createElement('p');
p.innerHTML = 'Hello World';
document.body.appendChild(p);
```

Flow:

```
Create Element
↓
Add Content/Style
↓
Append to DOM
↓
Visible on Page
```

## Parent & Child Relationship

```html
<body>
  <h1>Hello</h1>
</body>
```

```js
document.body.children[0]              // <h1>
document.body.children[0].parentNode   // <body>
```

## Memory Tricks

| Symbol | Meaning |
| --- | --- |
| `'p'` | Tag/Element |
| `'.card'` | Class |
| `'#logo'` | ID |

## Most Used in Real Projects

```js
document.querySelector()
document.querySelectorAll()
element.innerHTML
element.textContent
element.style
document.createElement()
element.appendChild()
```

---
## Related
- [[../01 - Web Fundamentals/02 - HTML]]
- [[13 - Forms]]
