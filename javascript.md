## Pitfalls
### 1. Hoisting and TDS (temporal dead space)
 - `var` variables are initialised with a value in TDS
 - `let` and `const` are technically hoisted as well but they are uninitialised in TDS and therefore cannot be used out of scope or out of order
### 2. `this`
 - `this` is dynamcially assigned and it depends on "where" the method is called
 - avoid using `this` in `=>` functions inside an object or class
 - `this` is `undefined` in basic functions. e.g. `hello()`
### 3. `object.call()` and `object.apply()`
 - are used to apply an object to `this` when calling a function that is in another object and has reference to `this` inside it 

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
