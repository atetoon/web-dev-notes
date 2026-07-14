# JavaScript Testing

---

## 1. Types of Testing

### Definition

**Testing** is the process of verifying that code behaves as expected before deploying it to users.

### Types

| Type | Tests | External Services |
| --- | --- | --- |
| Unit Tests | Smallest unit — single function | Mocked |
| Integration Tests | How units work together | Mocked (handling only) |
| End-to-End (E2E) | Full user flow through the app | Real (DB, APIs) |

### Unit Tests

- Test the **smallest piece of code** (e.g. a single function)
- External data is **mocked**
- Written first, before integration tests

### Integration Tests

- Test how **units work together**
- External services still mocked
- Test handling of delays, errors, invalid data

### End-to-End Tests

- Simulate a **real user's experience**
- Uses actual databases and APIs
- Most resource-intensive

### How They Relate

```
Unit Tests
     │
     ▼
Integration Tests
     │
     ▼
End-to-End Tests

↑ More scope, time, and cost
```

---

## 2. Testing Methodologies

### Definition

A **testing methodology** is a strategy for testing all pieces of software to ensure it behaves as expected.

### Why Use Them?

- Software errors cost money and users
- Testing results in better reliability
- Provides better end-user experience
- Failing tests indicate which part is broken

### Test-First Methodologies

| Methodology | Focus | Unit |
| --- | --- | --- |
| TDD | Individual functions/classes | Function / Class |
| BDD | User behavior | Feature |
| ATDD | Acceptance criteria | Feature |
| SBE | Specification by example | Feature |

### TDD (Test-Driven Development)

- Write **tests before code**
- Tests define the purpose and use case
- Short development cycles
- Benefits:
  - Better understanding of requirements
  - No unused code added
  - Reduced scope
  - Code written with testability in mind

### BDD (Behavior-Driven Development)

- Similar to TDD but focused on **user behavior**
- Written in plain language
- Collaborative — engineers + product owners + stakeholders
- Unit = a **feature**, not a function
- Changes only when product behavior changes

> Teams can mix methodologies at different stages.

---

## 3. Mocha — Setup & Structure

### Definition

**Mocha** is a JavaScript test framework used to organize and automate tests.

### Installation

```bash
npm init
npm install mocha -D
```

`-D` = dev dependency (not included in production)

### Running Tests

```bash
# After adding "test": "mocha" to package.json
npm test

# Single file
mocha test/index_test.js

# All test files recursively
mocha test/**/*_test.js
```

### Wildcard Breakdown

| Symbol | Meaning |
| --- | --- |
| `**` | Recursively search subdirectories |
| `*_test.js` | Any file ending in `_test.js` |

### Test Structure

```js
describe('Math', () => {
  describe('.max', () => {
    it('returns the highest value', () => {
      // test here
    });
    it('returns -Infinity when no arguments', () => {
      // test here
    });
  });
});
```

### describe() and it()

| Function | Purpose |
| --- | --- |
| `describe()` | Groups related tests |
| `it()` | Defines a single test |

Both accept: **string** (description) + **callback** (function)

---

## 4. The Four Phases of a Test

### Definition

Every well-written test should be divided into four clear phases.

### Phases

| Phase | Purpose |
| --- | --- |
| Setup | Create objects, variables, conditions |
| Exercise | Run the code being tested |
| Verify | Use assert to check the result |
| Teardown | Reset environment for the next test |

### Example

```js
it('removes last element', () => {
  // Setup
  const arr = [1, 2, 3];

  // Exercise
  arr.pop();

  // Verify
  assert.ok(arr.length === 2);

  // Teardown (if needed)
  // fs.unlinkSync(path);
});
```

### Teardown

Used when a test changes the environment:

- Altering files / directories
- Changing file permissions
- Editing database records

> Not every test needs teardown — only when environment state changes.

### Benefits of Teardown

- Tests don't interfere with each other
- Tests can run in **any order**

---

## 5. Hooks

### Definition

**Hooks** are Mocha functions that run setup/teardown code automatically, avoiding repetition.

### Types

| Hook | When it Runs |
| --- | --- |
| `before()` | Once, before the first test |
| `after()` | Once, after the last test |
| `beforeEach()` | Before every test |
| `afterEach()` | After every test |

### Syntax

```js
describe('example', () => {
  let val;

  before(() => { /* runs once before all */ });
  after(() => { /* runs once after all */ });
  beforeEach(() => { val = 5; }); // shared setup
  afterEach(() => { /* teardown */ });

  it('adds', () => {
    val += 5;
    assert.equal(val, 10);
  });

  it('multiplies', () => {
    val *= 5;
    assert.equal(val, 25);
  });
});
```

> Unique setup/teardown for a single test stays inside its `it()` block.

---

## 6. Assert Methods

### Definition

**Assert** methods compare expected vs actual values and throw errors when they don't match.

### Import

```js
// Node built-in
const assert = require('assert');

// Chai (more expressive)
const { assert } = require('chai');
```

### Node Assert Methods

| Method | Purpose | Operator |
| --- | --- | --- |
| `assert.ok(val)` | Checks if value is truthy | truthy |
| `assert.equal(a, b)` | Loose equality | `==` |
| `assert.strictEqual(a, b)` | Strict equality | `===` |
| `assert.deepStrictEqual(a, b)` | Deep equality for objects/arrays | `===` (deep) |
| `assert.throws(fn, err)` | Checks if function throws | — |

### Examples

```js
assert.ok(6 - 1 === 5);                    // passes
assert.equal(3, '3');                      // passes (loose ==)
assert.strictEqual(3, '3');                // fails — type mismatch
assert.deepStrictEqual({ a: 1 }, { a: 1 }); // passes
assert.throws(() => { fn(-1); }, RangeError);
```

### assert.ok()

```js
assert.ok(true);   // passes
assert.ok(false);  // throws AssertionError
```

### assert.equal() vs assert.strictEqual()

```js
const a = 3;
const b = '3';
assert.equal(a, b);       // passes — loose ==
assert.strictEqual(a, b); // fails — strict ===
```

> Always prefer `assert.strictEqual()` over `assert.equal()`.

### assert.deepStrictEqual()

```js
const a = { relation: 'twin', age: '17' };
const b = { relation: 'twin', age: '17' };

assert.equal(a, b);           // fails — different references
assert.strictEqual(a, b);     // fails — different references
assert.deepStrictEqual(a, b); // passes — compares values
```

Works for arrays too:

```js
assert.deepStrictEqual([1, 2, 3], [1, 2, 3]);    // passes
assert.deepStrictEqual([1, 2, 3], [1, 2, '3']);   // fails
```

### assert.throws()

```js
it('throws if input is not a string', () => {
  const exercise = () => { Phrase.initials(14); };
  assert.throws(exercise, /only use string/);
});
```

### Chai Methods

```js
assert.include(arr, 4);           // array contains 4
assert.include('foobar', 'bar');  // string contains 'bar'
assert.notInclude(arr, 99);       // value absent
```

---

## 7. TDD — Red Green Refactor Cycle

### Definition

The **Red-Green-Refactor** cycle is the core workflow of Test-Driven Development.

### Cycle

```
Write Failing Test (Red)
        │
        ▼
Write Minimum Code (Green)
        │
        ▼
Clean Up Code (Refactor)
        │
        ▼
Repeat
```

### Red

- Write a test that **describes** intended behavior
- Run it — it **must fail**
- The error message guides what to implement

### Green

- Write **just enough** code to pass the test
- Don't over-engineer
- Even hardcoded values are fine at first

### Refactor

- Clean up code
- Apply the 4 phases to tests
- Rename variables for clarity
- Tests must **stay green** throughout

### Example Progression

```js
// Red: test written, Phrase doesn't exist
assert.strictEqual(Phrase.initials('Nelson Mandela'), 'NM');

// Green: minimum code
const Phrase = {
  initials(phr) { return 'NM'; }
};

// More tests added → forces real logic
// Refactor: actual implementation
const Phrase = {
  initials(inputName) {
    return inputName
      .split(' ')
      .map(w => w.charAt(0))
      .join('');
  }
};
```

> Add more tests to force better implementation. Each cycle = one feature or edge case.

---

## 8. Edge Cases

### Definition

An **edge case** is a problem that occurs at an extreme or unexpected input parameter.

### Examples

- Passing a number instead of a string
- Empty array
- Negative values
- `null` or `undefined`

### Testing Edge Cases

```js
it('throws if input is not a string', () => {
  // Setup
  const nameInput = 14;

  // Exercise
  const exercise = () => { Phrase.initials(nameInput); };

  // Verify
  assert.throws(exercise, /only use string/);
});
```

### Implementation

```js
const Phrase = {
  initials(inputName) {
    if (typeof inputName !== 'string') {
      throw new Error('ERROR: only use string');
    }
    return inputName
      .split(' ')
      .map(w => w.charAt(0))
      .join('');
  }
};
```

> `/only use string/` is a **regex** — `assert.throws` checks if the error message matches it.

---

## 9. Server Testing Stack

### Definition

**Server tests** test backend responses directly — no browser or UI involved.

### Used For

- API responses
- HTTP status codes
- Error handling (sad paths)

### Tools

| Tool | Purpose |
| --- | --- |
| Chai | Expressive assertions |
| jsdom | Parse and query HTML responses like a DOM |
| supertest | Make HTTP requests to server in tests |
| async/await | Handle async server responses |

### Setup

```bash
npm install chai supertest
```

### Status Codes

```js
it('returns 200 status', async () => {
  const response = await request(app).get('/').send();
  assert.equal(response.status, 200);
});
```

### Common Status Codes

| Code | Meaning |
| --- | --- |
| `200` | OK |
| `201` | Created |
| `400` | Bad Request |
| `401` | Unauthorized |
| `404` | Not Found |
| `500` | Server Error |

### Supertest

```js
const request = require('supertest');

// GET request
const response = await request(app)
  .get('/')
  .send();

// POST request
await request(app)
  .post('/messages')
  .type('form')
  .send({ author, message });
```

### parseTextFromHTML (jsdom helper)

```js
const parseTextFromHTML = (htmlAsString, selector) => {
  const { document } = new JSDOM(htmlAsString).window;
  const selectedElement = document.querySelector(selector);
  if (selectedElement !== null) {
    return selectedElement.textContent;
  } else {
    throw new Error(`No element with selector ${selector} found`);
  }
};

// Usage
assert.include(
  parseTextFromHTML(response.text, '#page-title'),
  'Messaging App'
);
```

### Happy Path vs Sad Path

| Path | Description |
| --- | --- |
| Happy Path | Expected, valid inputs |
| Sad Path | Invalid or unexpected inputs |

```js
// Happy path
assert.equal(response.status, 200);

// Sad path
assert.equal(response.status, 400);
assert.notInclude(parseTextFromHTML(response.text, '#name'), 'Unknown');
```

> One happy path, many sad paths. Test sad paths at server level — faster than UI tests.

### Handlebars Templating

```js
// Controller
res.render('profile', { username });
```

```html
<!-- views/profile.handlebars -->
<h1 id="welcome-message">Welcome {{ username }}</h1>
```

### async/await in Tests

```js
it('returns a response', async () => {
  const response = await request(app).get('/').send();
  assert.equal(response.status, 200);
});
```

---

## 10. Code Coverage & Test Coverage

### Definitions

| Term | Definition |
| --- | --- |
| Code Coverage | % of application code executed during tests |
| Test Coverage | % of required features/specs that are tested |

### Code Coverage Criteria

| Criteria | Question |
| --- | --- |
| Function Coverage | Has each function been called? |
| Statement Coverage | Has each statement been executed? |
| Path Coverage | Has every branch (if/else) been taken? |
| Condition Coverage | Has each boolean been both true and false? |

### Example

```js
function numSum(x, y) {
  if (x && y) {
    return (x + y);
  } else {
    return null;
  }
}

numSum(1, 2);      // covers if branch
numSum(1, false);  // covers else branch
numSum(false, 1);  // covers x = false
numSum();          // covers both false
```

### The 100% Coverage Myth

100% coverage does **not** guarantee bug-free code.

```js
numSum('1', '2') // returns '12' instead of 3 — bug not caught by coverage
```

> Use coverage as a guideline, not a guarantee.

---

## 11. Mocking

### Definition

**Mocking** (also called stubbing) is creating a fake version of an external service for testing purposes.

### Why Mock?

- Isolate the unit being tested
- Remove dependency on external services
- Limit sources of potential bugs

### Mocking in Unit Tests

Mock freely — replace all external dependencies.

```
1. Fetch from DB     ← mock
2. Format data       ← mock
3. Render data       ← test this
```

### Mocking in Integration Tests

Mock external services only — test internal services together.

```
1. Fetch from DB     ← mock (external)
2. Format data       ← don't mock (internal)
3. Render data       ← don't mock (internal)
```

### Summary

| Test Type | Mock External? | Mock Internal? |
| --- | --- | --- |
| Unit Tests | Yes | Yes |
| Integration Tests | Yes | No |

---

## 12. Spies (Sinon.js)

### Definition

A **spy** is a function that observes and records information about another function's calls without changing its behavior.

### What Spies Record

- Arguments passed
- Return values
- `this` value
- Exceptions thrown

### Sinon.js

**Sinon.js** is a JavaScript library providing spies, stubs, and mocks.

```bash
npm install sinon
```

### Syntax

```js
sinon.spy(robot, 'greet');           // wrap spy around method

robot.greet('codey');                // call the method

robot.greet.called                   // → true
robot.greet.calledWith('codey')      // → true
robot.greet.returned('Hello codey')  // → true

robot.greet.restore();               // remove spy
```

### Spy Properties/Methods

| Property / Method | What it Checks |
| --- | --- |
| `.called` | Was the function called? |
| `.calledWith(arg)` | Was it called with this argument? |
| `.returned(val)` | Did it return this value? |
| `.restore()` | Remove the spy |

### Full Example

```js
const robot = {
  greet(name) {
    return 'Hello ' + name;
  }
};

test('greet should return hello codey', () => {
  sinon.spy(robot, 'greet');
  robot.greet('codey');

  expect(robot.greet.called).to.be.true;
  expect(robot.greet.calledWith('codey')).to.be.true;
  expect(robot.greet.returned('Hello codey')).to.be.true;

  robot.greet.restore();
});
```

---

## Quick Reference — Good Test Criteria

| Criterion | Meaning |
| --- | --- |
| Fast | Tests run quickly |
| Complete | Covers all cases including edge cases |
| Reliable | Same result every run |
| Isolated | Tests don't affect each other |
| Maintainable | Easy to update when code changes |
| Expressive | Readable, self-documenting |

---

## Execution Order (Full)

```
FROM / Setup
      │
      ▼
WHERE / Filter (beforeEach)
      │
      ▼
Exercise
      │
      ▼
Verify (assert)
      │
      ▼
Teardown (afterEach)
```


---
## Related
- [[../02 - JavaScript/11 - Async]]
- [[../02 - JavaScript/10 - Error Handling]]
- [[../05 - Backend/04 - Express.js]]
