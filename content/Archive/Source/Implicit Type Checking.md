## Type Inference

- TypeScript can automatically guess types based on assigned values.
- Assigning an incompatible type causes a type error:`
- When destructuring object properties, the types are preserved:
- Array literals are also inferred
## Contextual Type Inference
- TypeScript infers types based on context, such as in array methods
- Transformations are also inferred
## Losing Type Inference

- If a function is defined separately and passed to `.map`, TypeScript can't infer its parameter types.  
- Without type annotations, parameters become `any`
## noImplicitAny
- When `noImplicitAny` is enabled, TypeScript gives an error if a variable or parameter defaults to `any`
- Implicit `any` disables type checking
