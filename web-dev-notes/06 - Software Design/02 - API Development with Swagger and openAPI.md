# API Development — Practical Cheat Sheet

## API Design Rules (Actually Follow These)

**Use nouns for URLs, not verbs:**

```
❌ /retrieveEveryPhoto
✅ /photos
✅ /photos/1
```

**HTTP methods = CRUD:**

|Verb|Use|Example|
|---|---|---|
|GET|Retrieve|`GET /photos/1`|
|POST|Create|`POST /photos`|
|PUT|Full update|`PUT /photos/34`|
|PATCH|Partial update|`PATCH /photos/4`|
|DELETE|Delete|`DELETE /photos/12`|

**Use query params for filtering/limiting:**

```
GET /photos?location=boston&hashtag=winter&limit=10
```

**Status codes to actually use:**

|Code|Use it when|
|---|---|
|200|Success (GET/PUT)|
|201|Created (POST)|
|204|Deleted, no content to return|
|400|Bad request from client|
|401|Not authenticated|
|404|Resource not found|
|500|Server error|

---

## YAML Syntax (for OpenAPI specs / config files)

```yaml
# comment
key: value

nested:
  key: value

list:
  - item1
  - item2

inline_list: [item1, item2, item3]

string: "quoted if it needs escaping like \n"
number: 42
float: 4.2
boolean: true
nothing: null
```

**Rules:** spaces only (no tabs), `key: value` needs a space after the colon.

---

## OpenAPI Spec Skeleton (copy-paste starter)

```yaml
openapi: 3.0.1
info:
  title: My API
  version: 1.0.0
  description: A short description of the API.

servers:
  - url: http://localhost:3000
    description: Local dev server

paths:
  /orders:
    get:
      summary: Get all orders
      responses:
        '200':
          description: Successful response
          content:
            application/json:
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/Order'

  /orders/{id}:
    get:
      summary: Get one order
      parameters:
        - name: id
          in: path
          required: true
          schema:
            type: string
      responses:
        '200':
          description: Successful response
        '404':
          description: Order not found

    put:
      summary: Update an order
      parameters:
        - name: id
          in: path
          required: true
          schema:
            type: string
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/Order'
      responses:
        '200':
          description: Updated successfully

    delete:
      summary: Delete an order
      parameters:
        - name: id
          in: path
          required: true
          schema:
            type: string
      responses:
        '204':
          description: Deleted successfully

  /orders:
    post:
      summary: Create a new order
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/Order'
      responses:
        '201':
          description: Created successfully

components:
  schemas:
    Order:
      type: object
      properties:
        id:
          type: string
        name:
          type: string
        state:
          type: string
```

**Parameter locations you'll actually use:**

```yaml
in: path     # /users/{id}
in: query    # /users?role=admin
in: header   # X-MyHeader: Value
```

---

## Express.js — Matching Code for the Spec Above

```js
const express = require('express');
const fs = require('fs');
const app = express();

app.use(express.json()); // needed to parse req.body

// GET all
app.get('/orders', (req, res) => {
  res.json(orderData);
});

// GET one
app.get('/orders/:id', (req, res) => {
  const order = orderData.orders.find(o => o.id === req.params.id);
  if (!order) return res.status(404).send('Not found');
  res.json(order);
});

// POST create
app.post('/orders', (req, res) => {
  orderData.orders.push(req.body);
  fs.writeFileSync('orders.json', JSON.stringify(orderData));
  res.status(201).send('Created');
});

// PUT update
app.put('/orders/:id', (req, res) => {
  const order = orderData.orders.find(o => o.id === req.params.id);
  if (!order) return res.status(404).send('Not found');
  order.state = req.body.state;
  fs.writeFileSync('orders.json', JSON.stringify(orderData));
  res.send('Updated');
});

// DELETE
app.delete('/orders/:id', (req, res) => {
  orderData.orders = orderData.orders.filter(o => o.id !== req.params.id);
  fs.writeFileSync('orders.json', JSON.stringify(orderData));
  res.status(204).send();
});
```

---

## Swagger Tools — What They're Actually For

|Tool|When to use it|
|---|---|
|**Swagger Editor**|Write your OpenAPI YAML spec, see live preview + errors|
|**Swagger UI**|Auto-generated interactive docs for your API (paste your spec, get a testable UI)|
|**Swagger Codegen**|Skip only if the project is small — otherwise generates boilerplate server/client code from your spec|

**Quick workflow for a real project:**

1. Write your endpoints in YAML (OpenAPI spec) — decide routes/methods/responses **before** coding
2. Paste spec into [Swagger Editor](https://editor.swagger.io/) to validate + preview docs
3. Build the actual Express routes matching the spec
4. Host the Swagger UI docs alongside your API (use `swagger-ui-express` npm package) so others can test it

```bash
npm install swagger-ui-express yamljs
```

```js
const swaggerUi = require('swagger-ui-express');
const YAML = require('yamljs');
const swaggerDocument = YAML.load('./openapi.yaml');

app.use('/api-docs', swaggerUi.serve, swaggerUi.setup(swaggerDocument));
```

Now visiting `/api-docs` shows live interactive documentation for your API.

---

## Design First vs Code First — Which to Pick

|Use Design First when...|Use Code First when...|
|---|---|
|Others (frontend team, external users) will consume your API|Only you/your team uses it internally|
|API is public-facing or client-facing|Small project, few endpoints|
|Team needs to agree on structure before coding|Speed matters more than polish|

**For your solo projects → Code First is usually fine.** Use Design First when building something others will integrate with.