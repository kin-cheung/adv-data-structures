# Nodejs
## Internals
 - nodejs is built using JS and C++ using V8 (JS/C++) and libuv (C++)
 - V8 is a JS engine that interprets/compiles JS into machine coding using JIT 
 - libuv is a C++ library that provide OS access
   - Event Loop, Thread Pool, Async IO
 - nodejs connects JS and C++ using `process.binding()`, e.g. PBKDF2
## Event Loop
 - it is provided by libuv, **not** V8
### Microtask queue vs Marcotask queue
 - two event queues for two types of tasks, microtasks and macrotasks
 - microtasks take priority over macrotasks
 - microtasks include `Promise.then()` and `process.nextTick()`
 - macrotasks include `setTimeout()`, I/O callbacks, etc.
## Architecture
```mermaid
flowchart LR;
  your_js["JS we write"]
  nodejs_js["Node JS API"]
  binding[" Node C++ Bindings"]
  cpp_addons["C++ Add-ons"]

  your_js --> nodejs_js --> binding
  binding --> V8
  binding --> libuv
  binding --> cpp_addons
```
