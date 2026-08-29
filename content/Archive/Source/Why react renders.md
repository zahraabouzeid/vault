## Rendering process
- The view (v) is a function of the state (f(s)).
- Rendering in React means calling the function component to update the view.
- During rendering React creates a snapshot of the component, capturing props, state, event handlers, and a UI description and uses UI description to update the view.
- React will only re-render when the state of a component changes

## Create root
React performs an initial render starting at the root of the application to generate the starting UI. The root refers to the HTML element where the React app is mounted.

```javascript
import { createRoot } from "react-dom/client";
import App from "./App";

const rootElement = document.getElementById("root");
const root = createRoot(rootElement);

root.render(<App />);
```

## Batching
Whenever React encounters multiple invocations of the same updater function, it will keep track of each of them, but only the result of the last invocation will be used as the new state.

```javascript
const handleClick = () => {
  setCount(1)
  setCount(2)
  setCount(3)
}
```

## StrictMode
- Whenever you have `StrictMode` enabled, React will re-render your components an extra time.
- `StrictMode` makes sure your app is resilient to re-renders and that your components are pure. If not, it'll become obvious when React renders the 2nd time.

```javascript
import { StrictMode } from 'react';

import { createRoot } from 'react-dom/client';

const root = createRoot(
  document.getElementById('root')
);

root.render(
  <StrictMode>
    <App />
  </StrictMode>
);
```

> [!info]
> It doesn't have performance implications because React will only respect `StrictMode` when you're in `development` mode. In `production`, it'll be ignored.

## React.memo
`React.memo` is a function that takes in a React component as an argument and returns a new component that will only re-render if its props change.

```javascript
import * as React from "react"
function Wave () {
  console.count('Rendering Wave')
  return (
    <span role="img" aria-label="hand waving">
      👋
    </span>
  )
}
export default React.memo(Wave)
```

- **Without `React.memo`**: A component will re-render when its parent re-renders, even if the component’s props haven't changed.
- **With `React.memo`**: React will skip rendering the component if the props are the same as the last render, saving performance on unnecessary renders.