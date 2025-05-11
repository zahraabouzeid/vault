## useDeferredValue 
- Delays updates to lower-priority values.
- Input field + expensive component, the input feels smooth because React prioritizes updating the text first, then renders the heavy component afterward.
- Comparable to debouncing, but smarter and more responsive to the user's context.

## startTransition
- Marks updates as "non-urgent."
- React performs them in the background and prioritizes more important tasks (like user input).

## useTransition 
- A hook version of `startTransition` that also provides an `isPending` state.
- Enables visual feedback (e.g. loading indicators) while a transition is in progress.
