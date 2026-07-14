# HTTP, APIs, JSON & REST

## HTTP

**HTTP (HyperText Transfer Protocol)** is the protocol used for communication between a client (browser) and a server.

```
Browser (Client) → Request → Server → Response → Browser
```

### Request & Response Example

```
GET / HTTP/1.1
Host: www.codecademy.com
```

```
HTTP/1.1 200 OK
Content-Type: text/html
```

### HTTP vs HTTPS

| HTTP | HTTPS |
| --- | --- |
| Data not encrypted ❌ | Data encrypted ✅ |

Used for passwords, banking, credit cards, personal data.

### TCP

**TCP** establishes the connection between client and server.

```
HTTP = Communication Language
TCP  = Connection Channel
```

---

## APIs

**API (Application Programming Interface)** allows one application to use another application's functionality or data.

```
Your App → Weather API → Weather Data
```

### Types

| Type | Examples |
| --- | --- |
| Browser API | Geolocation, Audio, Camera |
| Third-Party API | OpenWeather, Google Maps, Spotify, Facebook |

### API Key

Used for authentication, rate limiting, tracking usage.

```
https://api.example.com?apikey=12345
```

### API Request Flow

```
App → API Request → Server → JSON Response → App Displays Data
```

---

## JSON

**JSON (JavaScript Object Notation)** is a format used to store and exchange data.

```json
{
  "name": "Dhruv",
  "age": 19,
  "skills": ["C++", "JS"],
  "active": true,
  "college": null
}
```

### Rules

- Keys must use double quotes ✅
- No trailing commas ❌

### JSON.parse() / JSON.stringify()

```js
// JSON → JS Object
const jsonData = '{"name":"Dhruv"}';
const obj = JSON.parse(jsonData);
console.log(obj.name); // 'Dhruv'

// JS Object → JSON
const obj2 = { name: "Dhruv" };
const json = JSON.stringify(obj2);
// '{"name":"Dhruv"}'
```

---

## REST API

**REST (Representational State Transfer)** is an architectural style for building web APIs — stateless, client-server based, resource based.

### Separation of Client & Server

```
Frontend → API → Backend
```
Both can be developed independently.

### Statelessness

Server doesn't remember previous requests. Each request contains all required info.

### Resources

REST works with resources — nouns, not actions.

```
/users
/products
/orders
/photos
```

## HTTP Methods

| Method | Purpose | Example | Success Code |
| --- | --- | --- | --- |
| GET | Retrieve data | `GET /users` | 200 OK |
| POST | Create resource | `POST /users` | 201 CREATED |
| PUT | Update resource | `PUT /users/1` | 200 OK |
| DELETE | Delete resource | `DELETE /users/1` | 204 NO CONTENT |

## REST Paths

```
GET /customers               → get all customers
GET /customers/123           → get customer with ID 123
GET /customers/123/orders/12 → get order 12 of customer 123
```

## MIME Types

```
text/html
text/css
application/json
image/png
image/jpeg
video/mp4
application/pdf
```

## Status Codes

| Code | Meaning |
| --- | --- |
| 200 | OK — request successful |
| 201 | CREATED — resource created |
| 204 | NO CONTENT — success, no data returned |
| 400 | BAD REQUEST — invalid request |
| 403 | FORBIDDEN — no permission |
| 404 | NOT FOUND — resource not found |
| 500 | INTERNAL SERVER ERROR |

## Quick Revision

```
HTTP  = Client ↔ Server communication
HTTPS = Secure HTTP
TCP   = Connection channel

API = Access another application's data/functions
Browser API = Geolocation, Camera, Audio
Third Party API = Weather, Maps, Spotify

JSON = Data exchange format
JSON.parse()     = JSON → JS Object
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

---
## Related
- [[04 - Express.js]]
- [[06 - Fetch API]]
