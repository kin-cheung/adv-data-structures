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

### Others
 - protected
 - abstact classes
 - [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) contains @types commonly used declaration files
