## Hooks
- are special functions.
- are special because they have few limitations.
- must be prepended with `use`.
- can't be called inside conditions, loops, or other nested functions.
## useState
```javascript
const stateArray = React.useState("initial state value")
const state = stateArray[0]
const setState = stateArray[1]
console.log(state) // "initial state value"
setState('new state value')
```
- is a way to preserve a value across component renders.
- is built-in with React and can be accessed via `React.useState`.

**Using Array Destructuring**
```javascript
import * as React from "react"

export default function Counter() {
  const [count, setCount] = React.useState(0)
  const handleClick = () => setCount(count + 1)
  return (
    <button onClick={handleClick}>
      {count}
    </button>
  )
}
```