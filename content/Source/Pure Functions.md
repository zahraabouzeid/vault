To make apps more predictable by making functions more predictable aka **Pure Functions**. What makes a function unpredictable are **side effects** and **inconsistent outputs**. A pure function:
- always returns the same output for a given input
- is composable
- is cacheable
- is testable
- is usually more readable

## Side Effects
This occurs when a function doesn't necessarily create an observable change to the program, but it does rely on state other than the input value it receives (state from an external API still counts).
```javascript
function getGithubProfile(username) {
  return fetch(
    `https://api.github.com/users/${username}`
  ).then((res) => res.json());
}
```
Moreover, a function has a side effect when it creates an observable change to the program without necessarily relying on state other than the input value it receives, but we by creating an observable change to the program itself.
```javascript
function updateDocumentTitle(title) {
  document.title = title;
}
```

## Inconsistent outputs
- If a function doesn't have a return value, it's unpredictable.
- Similarly, if a function, given the same input, doesn't consistently return the same output, it's also unpredictable.

## Predictable Function
This is an example of a predictable function:
```javascript
let primeCache = {
  1: false
}

const isPrime = (n) => {
  if (typeof primeCache[n] === 'boolean') {
    return primeCache[n];
  }

  for (let i = 2; i <= Math.sqrt(n); i++) {
    if (n % i === 0) {
      primeCache[n] = false;
      return false;
    }
  }

  primeCache[n] = true
  return true
}


```
When a function is predictable, its result can be cashed and reused.
```javascript
export default isPrime
import isPrime from "./isPrime"

isPrime(997) // true
isPrime(997) // true (from cache)
isPrime(997) // true (from cache)
```