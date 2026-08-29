## Implicit vs Explicit Typing

- TypeScript infers types automatically
- But if no value is assigned, TypeScript can’t infer the type it defaults to `any`
- Use explicit type annotations to avoid this
## Syntax Notes
- Use **lowercase** for primitive types: `string`, `number`, `boolean`
- Avoid using `String`, `Number`, `Boolean` (capitalized) — these are object wrappers
## Unassigned Variables
- Declared but unassigned variables have the value `undefined` in JavaScript
- TypeScript expects them to be initialized before usage
- Use the non-null assertion (`!`) to bypass this check:

```ts
let floralArrangement!: string;
console.log(floralArrangement); // undefined
```

## Arrays
- Preferred syntax: `string[]`
- Alternative (not recommended): `Array<string>`
## Objects
Define object shape with property type annotations
## null and undefined
- Can be used as types but are rarely useful alone
- Will be more useful with union types
## Assigning any to Typed Variable
- Helps recover type safety
- TypeScript trusts the provided type, even if it doesn't match the real data
- Can lead to runtime errors
