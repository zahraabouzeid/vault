- JavaScript and TypeScript share the same type system
- `typeof` operator gives the type as a string
- **Primitive types** and **Structural types**

## Primitive Types (Immutable)
#### Boolean
- `true`, `false`  
- Used in conditionals and logical operations (`&&`, `||`, `!`)  
- Falsy values include: `false`, `0`, `""`, `null`, `undefined`, `NaN`
#### Number 
- One type for integers and floats  
- Includes special values like `Infinity`, `-Infinity`, `NaN`  
- `NaN` is still of type `"number"`  
- `Number.isNaN()` to check for `NaN`  
- `0` and `NaN` are falsy

#### BigInt
- For large integers  
- Created by adding `n` to a number (example: `1337n`)  
- `0n` is falsy
#### String
- Stores text  
- Created using `'`, `"`, or `` ` ``  
- Strings are immutable  
- Only the empty string `""` is falsy
#### Symbol  
- Unique and immutable values  
- Two symbols with the same description are not equal  
- Used for special keys in objects
#### undefined
- Its own type  
- Represents uninitialized values  
- Falsy
#### null
- Represents absence of value  
- `typeof null` returns `"object"` (known bug)  
- Falsy  
- `null === null` is true

## Structural Types

#### Object
- Key-value structure  
- Keys are usually strings or symbols  
- Values can be any type  
- Objects are compared by reference, not by value  
- Two objects with the same properties are not equal
#### Array
- Technically an object, but uses numeric indexing  
- Data is ordered  
- Use `Array.isArray()` to check if a value is an array  
- `typeof array` returns `"object"`
#### Function
- Blocks of reusable code  
- Can be passed around like values  
- `typeof` a function returns `"function"`
#### Class
- Defined with `constructor`, uses `this`  
- `typeof Class` is `"function"`  
- Instances of classes are of type `"object"`  
- Use `instanceof` to check class instances
