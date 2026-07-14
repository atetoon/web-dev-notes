# Node.js Essentials

## Modules

```js
const fs = require('fs');
```

Module = reusable code package. Examples: `fs`, `events`, `buffer`, `readline`.

## Events

```js
const events = require('events');
const emitter = new events.EventEmitter();

emitter.on('login', callback);  // listen
emitter.emit('login');          // trigger
```

```
.on()   → Listen
.emit() → Trigger
```

## Input / Output

```js
// Output
console.log("Hello");
process.stdout.write("Hello");

// Input
process.stdin.on('data', (input) => {
  console.log(input.toString());
});
```

```
stdin  → Input
stdout → Output
```

## Errors

```js
throw new Error("Oops");
```

### Error-First Callback

```js
(err, data)
```

```js
readFile('file.txt', (err, data) => {
  if (err) {
    console.log(err);
  }
});
```

## Buffers

```js
Buffer.alloc(5);              // create empty buffer
Buffer.from("hello");         // create from string
buffer.toString();            // convert to string
Buffer.concat([buf1, buf2]);  // merge buffers
```

> Buffer = Binary Data

## FS Module

```js
fs.readFile('file.txt', 'utf8', callback);   // async
fs.readFileSync('file.txt', 'utf8');          // sync
```

> fs = File System

## Streams

```js
fs.createReadStream('file.txt');

const readline = require('readline');
const myInterface = readline.createInterface({
  input: fs.createReadStream('file.txt')
});

myInterface.on('line', (line) => {
  console.log(line);
});
```

```
readFile() → whole file
Stream     → piece by piece
```

## Timers

```js
setTimeout(callback, 1000);     // run once
setInterval(callback, 1000);    // run forever
setImmediate(callback);         // run ASAP

clearTimeout(id);
clearInterval(id);
clearImmediate(id);
```

```
Timeout   → Once
Interval  → Repeat
Immediate → Next Event Loop
```

## Quick Reference

```
require()            → Import module
.on()                → Listen
.emit()               → Trigger
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

---
## Related
- [[01 - Node.js]]
- [[03 - CommonJS]]
