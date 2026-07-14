# Requests with Fetch API

## Overview

How JavaScript communicates with APIs using `fetch()`, Promises, `.then()`, `.catch()`, `async`/`await`.

## GET Requests

### Promise Style

```js
fetch(url)
  .then(response => response.json())
  .then(data => {
    console.log(data);
  })
  .catch(error => {
    console.log(error);
  });
```

### Async/Await Style

```js
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

## POST Requests

Used for: login, registration, forms, comments.

### Promise Style

```js
fetch(url, {
  method: 'POST',
  body: JSON.stringify({ id: 200 })
})
.then(response => response.json())
.then(data => { console.log(data); })
.catch(error => { console.log(error); });
```

### Async/Await Style

```js
async function postData() {
  try {
    const response = await fetch(url, {
      method: 'POST',
      body: JSON.stringify({ id: 200 })
    });
    const data = await response.json();
    console.log(data);
  } catch(error) {
    console.log(error);
  }
}
```

## fetch()

Makes HTTP requests, returns a **Promise**.

### Request Lifecycle

```
fetch() → Promise → Response Object → response.json() → Actual Data
```

## Response Object

```js
response.ok        // true → success, false → failure
response.status     // status code
response.json()     // parses body to JS object (returns a Promise)
```

```js
if (response.ok) {
  return response.json();
}
```

## GET vs POST

| GET | POST |
| --- | --- |
| Retrieve data | Send data |
| Read operation | Create operation |
| Usually no body | Requires body |

```js
// GET
fetch(url);

// POST
fetch(url, {
  method: 'POST',
  body: JSON.stringify(data)
});
```

## Promise vs Async/Await Style

```js
// Promise style
fetch(url)
  .then(...)
  .then(...)
  .catch(...)

// Async/Await style
try {
  const response = await fetch(url);
  const data = await response.json();
} catch(error) {
  console.log(error);
}
```

## Quick Revision

```
fetch()          → Makes HTTP Requests
GET              → Retrieve Data
POST             → Send Data
fetch() returns Promise

.then()          → Handle Success
.catch()         → Handle Errors

async            → Create Async Function
await            → Wait for Promise

response.ok      → Check Success
response.json()  → Convert JSON to JS Object
try...catch      → Error Handling

POST requires:
  method: 'POST'
  body: JSON.stringify(data)
```

---
## Related
- [[05 - HTTP, APIs & REST]]
- [[../02 - JavaScript/11 - Async]]
