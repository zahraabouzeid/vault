## useReducer Hook

- Returns `[state, dispatch]`.
- `dispatch(action)` invokes the reducer to update the state.
- a functional programming pattern that processes a collection into a single value.
- - Centralizes state update logic in the reducer function.
- Makes it easy to manage interdependent state properties.
- Cleaner and more declarative compared to multiple `useState` calls.

```js
function reducer(state, value) {
  return state + value;
}

const initialState = 0;

export default function Counter() {
  const [count, dispatch] = React.useReducer(reducer, initialState);

  const increment = () => dispatch(1);
  const decrement = () => dispatch(-1);

  return (
    <main>
      <h1>{count}</h1>
      <button onClick={increment}>+</button>
      <button onClick={decrement}>-</button>
    </main>
  );
}
```

## Complex State with Objects

```js
const initialState = { count: 0, step: 1 };

function reducer(state, action) {
  switch (action.type) {
    case "increment":
      return { ...state, count: state.count + state.step };
    case "decrement":
      return { ...state, count: state.count - state.step };
    case "updateStep":
      return { ...state, step: action.step };
    default:
      throw new Error("Unsupported action type");
  }
}

export default function Counter() {
  const [state, dispatch] = React.useReducer(reducer, initialState);

  const increment = () => dispatch({ type: "increment" });
  const decrement = () => dispatch({ type: "decrement" });
  const updateStep = (step) => dispatch({ type: "updateStep", step });

  return (
    <main>
      <h1>{state.count}</h1>
      <button onClick={increment}>+</button>
      <button onClick={decrement}>-</button>
      <input
        type="number"
        value={state.step}
        onChange={(e) => updateStep(Number(e.target.value))}
      />
    </main>
  );
}
```
## useReducer vs useState

- Complex state logic, such as dependent properties.
- When state updates are triggered by specific **actions**.
- Prefer `useReducer` when multiple related states need to be managed together.
- Use `useState` for simple, isolated states.
