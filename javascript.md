## Keys
### Hoisting and TDS (temporal dead space)
 - `var` variables are initialised with a value in TDS
 - `let` and `const` are technically hoisted as well but they are uninitialised in TDS and therefore cannot be used out of scope or out of order
### `this`
 - `this` is dynamcially assigned and it depends on "where" the method is called
 - avoid using `this` in `=>` functions inside an object or class
 - `this` is `undefined` in basic functions. e.g. `hello()`
### `object.call()` and `object.apply()`
 - are used to apply an object to `this` when calling a function that is in another object and has reference to `this` inside it 
### `entries()` vs `forEach()` in `Array`, `Map` and `Set`
 - `const [index, value] of array.entries`
 - `const [key, value] of map.entries` \
--- BUT ---
 - `array.forEach(function (value, index, array) {})`
 - `map.forEach(function (value, key, map) {})`
### Promise Combinators
 -  `await Promise.all([])` - returns after all have returned
 -  `await Promise.race([])` - returns as soon as one of them has returned
 -  `await Promise.allSettled([])` - returns results of all settled promises, but rejected promises are ignored
 -  `await Promise.any([])` - similar to `Promise.race([])` but rejected promises are ignored
### ES2022 features
 - `.at(-1)` to return the last item
 - top level `await` can be used in modules but it will block the entire module and the importing module
### The module pattern (Closure)
 ```javascript
 const aModule = (function() {
  function function1() {}
  function function2() {}
  function privateFunction1() {}
  return (
   function1,
   function2
  )
 })();
 aModule.function1();
 ```
### Others
 - Private class properties and function using `#`
 - Callback hell -> Promise hell -> async/await
 - Call stack + Call back queue + Microtask queue (Promise callbacks) + Event loop
  -   Microtask queue takes priority


## Working with vscode

### Settings
 - "Default Formatter"
 - Format on save
 - Prettier: Single quote
 - "Check JS"

``` 
  "editor.formatOnSave": true,
  "prettier.singleQuote": true,
  "prettier.jsxSingleQuote": true
  "js/ts.implicitProjectConfig.checkJs": true,
```

### Extensions
 - prettier
