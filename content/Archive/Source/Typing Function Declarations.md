## Typing Parameters

- Type annotations for function parameters are written after the parameter name with a colon and type.    
- Type mismatch in parameters will throw a TypeScript error.
- Works the same with arrow functions, but parameters must be wrapped in parentheses.
## Destructuring Parameters
- You cannot annotate individual destructured values directly.
    ```ts
    // Invalid
    function getFruitName({ name: string }) { ... }
    ```
- You must annotate the entire object instead.
    
    ```ts
    // Valid
    function getFruitName({ name }: { name: string }) {
      return name;
    }
    ```
    
- It's allowed to pass objects with extra properties as long as the required ones are present.

## Typing Return Values
- Functions can have annotated return types:

```ts
function headsOrTails(): boolean {
  return Math.random() > 0.5;
}
```

- In arrow functions, the return type goes before the arrow.

```ts
const headsOrTails = (): boolean => Math.random() > 0.5;
```


## Async Functions

- Async functions always return a `Promise`.
- Use `Promise<type>` to annotate return values.
```ts
async function getFruitList(): Promise<string[]> { ... }
```
- Using just `string[]` instead of `Promise<string[]>` will result in an error.

## Function Type Expressions

- When a function receives another function as a parameter (callback), you can annotate the function signature like this:

```ts
function mapNumberToNumber(
  list: number[],
  callback: (item: number) => number
) {
  // implementation
}
```    
- TypeScript will validate the passed callback against this type.
## Optional and Default Parameters
- TypeScript expects all parameters to be passed unless marked optional.
- Use `?` to make a parameter optional:
```ts
function logOutput(message: string, yell?: boolean) { ... }
```
- Or use a default value:
```ts
function logOutput(message: string, yell = true) { ... }
```
- TypeScript will infer the type from the default.
    
## Rest Parameters
- Use `...` to collect an unknown number of parameters.
- Annotate rest parameters with an array type:
```ts
function logManyOutput(...messages: string[]) {
  messages.forEach((message) => logOutput(message));
}
```

