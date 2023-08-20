# Nodejs
## Internals
 - nodejs is built using JS and C++ using V8 (JS/C++) and libuv (C++)
 - V8 is a JS engine that interprets/compiles JS into machine coding using JIT 
 - libuv is a C++ library that provide OS access
   - Event Loop, Thread Pool, Async IO
 - nodejs connects JS and C++ using `process.binding()`, e.g. PBKDF2
### Dependency

```mermaid
flowchart TD;
  your_js["JS we write"]
  nodejs_js["Node JS API"]
  cpp_addons["C++ Add-ons"]

  your_js --> nodejs_js
  nodejs_js -- binding --> V8
  nodejs_js -- binding --> libuv --> OS
  nodejs_js -- binding --> cpp_addons
```
