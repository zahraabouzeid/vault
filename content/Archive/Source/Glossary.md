## Compile Time vs Runtime
- _Compile Time_ is before the code runs.
    
- _Runtime_ is everything that happens after execution.
    

## Dynamic Types vs Static Types
- _Static types_: (Java, C++) variables stay the same type after declaration.
- _Dynamic types_: (JavaScript, Python) Types can change at runtime.
## Type Error
- Happens when a value of one type is used where another was expected.
- Example: using a number instead of a string, or calling something that’s actually `undefined`.

## Type Safety
- Prevents type errors by only using types in correct places.
- Usually involves compiler warnings.
- Can be rigid (low error chance) or flexible (higher error chance).

## Static Analysis / Static Validation
- Tool checks code **without running it**.
- Warns about errors, suggests improvements.
## Compiler
- Transforms code into another format.
- Typical: into machine code.
- TypeScript: into another programming language.
## Type Annotations
Bits of code that tell TypeScript what type a value or variable is.

## Type Declaration
`.d.ts` files that hold only type definitions for a JS library.
    