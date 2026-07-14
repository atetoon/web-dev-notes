# Node.js

## What is Node.js?

A JavaScript Runtime Environment — allows JavaScript to run outside the browser. Built on Chrome's V8 Engine.

```bash
node app.js
```

## REPL

```
Read → Evaluate → Print → Loop
```

```bash
node
> 2 + 3
5
```

## Modularity

Dividing a program into smaller modules/files, each handling a specific responsibility.

Benefits: better organization, reusability, easier maintenance, scalability.

## Modules

A module is a file containing code.

```js
const moduleName = require('module_name');
const events = require('events');
```

## Core Modules

Built into Node.js — no installation required.

```
console, process, os, util, events
```

---

## Console Module

Global object, used for terminal output and debugging.

```js
console.log("Hello");           // prints message

console.table(object);          // displays data in table format

console.assert(false, "Error"); // prints message when condition is false

console.count("loop");          // counts number of calls
console.count("loop");
// loop: 1
// loop: 2
```

---

## Process Module

Global object — provides info about the current Node.js process.

### process.argv

Stores command-line arguments.

```bash
node app.js hello world
```

```js
console.log(process.argv);
// ['/usr/bin/node', '/app.js', 'hello', 'world']
```

| Index | Meaning |
| --- | --- |
| `argv[0]` | Node path |
| `argv[1]` | Current file path |
| `argv[2+]` | User arguments |

### process.env

Stores environment variables.

```js
console.log(process.env);
process.env.NODE_ENV  // 'development' or 'production'
```

### process.memoryUsage()

```js
console.log(process.memoryUsage());
// heapUsed → memory currently in use
```

### process.emitWarning()

```js
process.emitWarning("Testing warning");
```

---

## OS Module

Provides info about OS, CPU architecture, network interfaces, host machine.

```js
const os = require('os');

os.type();               // 'Linux', 'Windows_NT', 'Darwin'
os.arch();                // 'x64'
os.homedir();              // '/home/dhruv'
os.hostname();             // device name
os.uptime();               // seconds since last reboot
os.networkInterfaces();    // IP/MAC address info
os.freemem();              // available RAM in bytes
```

---

## Util Module

Utility functions for debugging, maintenance, type checking.

```js
const util = require('util');

util.types.isDate(new Date());     // true
util.types.isDate("April 22");     // false

util.format("Hello %s", "Dhruv");  // 'Hello Dhruv'

// Converts callback-based functions to Promise-based
const getUserPromise = util.promisify(getUser);
```

---
## Related
- [[02 - Node.js Essentials]]
- [[03 - CommonJS]]
