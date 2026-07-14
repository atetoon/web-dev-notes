# Express.js

## Setup

```bash
npm install express
```

```js
const express = require('express');
const app = express();

app.listen(4000, () => {
  console.log('Server running');
});
```

Flow: `Express → express() → app → app.listen()`

## First Route

```js
app.get('/', (req, res) => {
  res.send('Hello');
});
```

## Route Structure

```js
app.METHOD(PATH, CALLBACK)

app.get('/users', callback)
app.post('/users', callback)
app.put('/users/:id', callback)
app.delete('/users/:id', callback)
```

## HTTP Methods

| Method | Purpose |
| --- | --- |
| GET | Read |
| POST | Create |
| PUT | Update |
| DELETE | Delete |

## GET

```js
// Get all
app.get('/users', (req, res) => {
  res.send(users);
});

// Get one
app.get('/users/:id', (req, res) => {
  res.send(user);
});
```

## Route Parameters

```js
app.get('/users/:id')
```

Request: `/users/5`

```js
req.params.id   // '5'
```

## Query Parameters

Request: `/users?name=dhruv&age=19`

```js
req.query
// { name: 'dhruv', age: '19' }
```

## Sending Responses

```js
res.send(data);
res.json(data);
res.status(200).send();
```

| Code | Meaning |
| --- | --- |
| 200 | OK |
| 201 | Created |
| 204 | Deleted |
| 400 | Bad Request |
| 404 | Not Found |

## POST / PUT / DELETE

```js
// POST — create
app.post('/users', (req, res) => {
  users.push(req.query);
  res.status(201).send(req.query);
});

// PUT — update
app.put('/users/:id', (req, res) => {
  user.name = req.query.name;
  res.send(user);
});

// DELETE
app.delete('/users/:id', (req, res) => {
  users.splice(index, 1);
  res.status(204).send();
});
```

## indexOf()

```js
const index = arr.indexOf(item);
// Found → 0,1,2...
// Not Found → -1

if (index !== -1) { }
```

## Dot vs Bracket Notation

```js
user.name        // fixed key

const key = 'name';
user[key]        // variable key

// Express examples
users[req.params.id]
battlefields[req.params.name]
```

## Middleware

```js
app.use((req, res, next) => {
  next();  // go to next middleware/route
});
```

## JSON Middleware

```js
app.use(express.json());  // enables req.body
```

## Static Files

```js
app.use(express.static('public'));
```

```
public/
 ├─ index.html
 ├─ style.css
```

## Router

```js
const router = express.Router();

router.get('/', ...);
router.post('/', ...);

module.exports = router;
```

## Mount Router

```js
app.use('/users', userRouter);
```

```
/users, /users/1, /users/abc → handled by userRouter
```

## Middleware Stack

```js
app.post('/users', authenticate, validate, createUser);
```

Flow:

```
Request → authenticate → next() → validate → next() → createUser → Response
```

## Route-Level Middleware

```js
app.use('/books', middleware);           // matches /books, /books/1, etc.
app.use(['/books', '/authors'], middleware); // multiple paths
```

## app.param()

Avoid duplicate parameter lookup.

```js
app.param('id', (req, res, next, id) => {
  req.user = getUser(id);
  next();
});
```

## mergeParams

Child router can access parent parameters.

```js
const router = express.Router({ mergeParams: true });
// route: /users/:userId/posts
// inside posts router: req.params.userId
```

## CORS

Cross-Origin Resource Sharing — allows browsers to access resources from another origin.

```bash
npm install cors
```

```js
const cors = require('cors');
app.use(cors());
```

Origin = Protocol + Host + Port. Different port = different origin.

### Preflight Request

Browser sends `OPTIONS` before `PUT`/`PATCH`/`DELETE` to check permission.

## Morgan (Logging)

```bash
npm install morgan
```

```js
const morgan = require('morgan');
app.use(morgan('dev'));
```

## Error Handling Middleware

Must be the last middleware.

```js
app.use((err, req, res, next) => {
  res.status(500).send(err.message);
});

next(error); // pass an error
```

## Common Open-Source Middleware

```js
express.json()    // Body parsing
morgan()          // Logging
cors()            // CORS
errorhandler()    // Error handling
```

## Request Object

```js
req.params   // Route params
req.query    // Query params
req.body     // Request body
req.method   // GET, POST...
req.path     // URL path
```

## Response Object

```js
res.send()
res.json()
res.status()
res.sendStatus()
```

## DRY Principle

**Don't Repeat Yourself.** Use middleware, `app.param()`, functions, or routers instead of repeating logic.

## Request Lifecycle

```
Client → Request → Middleware → Route → Business Logic → Response
```

## Express Cheatsheet

```js
app.listen()
app.get() / app.post() / app.put() / app.delete()
req.params / req.query
res.send() / res.json() / res.status()
app.use()
express.Router()
app.use('/path', router)
```

---
## Related
- [[03 - CommonJS]]
- [[05 - HTTP, APIs & REST]]
- [[../04 - Database/07 - PostgreSQL]]
