What we need is a way to tell React that we want to preserve a value across renders, but that value has nothing to do with the view, and therefore, React doesn't need to re-render when it changes.

## useRef
- Creates a value that is preserved across renders, but won't trigger a re-render when it changes
- If you have a side effect that is synchronizing your component with some outside system, put it inside of `useEffect`. If you need to preserve a value across renders, but that value has nothing to do with the view, and therefore, React doesn't need to re-render when it changes, put it in a `ref` using `useRef`.

