# Typescript
## Special keywords
### `nerver`
```typescript
 function setValue(value: number) : never {
   this.value = value;
   // illegal to return anything
 }
```

### `private` and `readonly` fields
```typescript
 class Person {
   _privateValue: number;          // semantic only
   readonly privateValue: number;  // typescript only
   private value: number;          // typescript only ad most preferred
   #privateValue: number;          // ES2022
 }
```

### Class Constructor Shortcuts
```typescript
  function Person {
    // No longer necessary
    // private name: string
    // private age:  number
    constructor(private name: string, private age: number) {
      // No longer necessary
      //this.name = name;
      //this.age = age;
    }
    get name(): string {
      return this.name;
    }
    set name(newName: string) {
      this.name = newName;
    }
  }
```

### webpack
 - webpack-dev-server is like nodemon
 - enable source map during development
 - clean-webpack-plugin - [contenthash].bundle.js is commonly used to generate a unique bundle for each build but it also creates a new bundle file everytime you build. `clean-webpack-plugin` is used to clean up the `/dist` folder before each build

### Others
 - protected
 - abstact classes
 - `import type` for Babel to safely assume the type can be removed in javascript code
 - [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) contains @types commonly used declaration files
