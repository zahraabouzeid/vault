The **`useEffect` hook** in React is used to handle side effects in components. A side effect is any operation that interacts with external systems or modifies the application outside of React's rendering flow (e.g., updating the DOM, making API calls, or managing timers). It ensures the effect runs only when specified dependencies change without the need to include unnecessary variables in the dependency array.

```jsx
export default function App() {
  const [count, setCount] = React.useState(0);
  const [delay, setDelay] = React.useState(100);
  const [step, setStep] = React.useState(1);

  const handleDelayChange = (d) => setDelay(d);
  const handleStepChange = (s) => setStep(s);

  React.useEffect(() => {
    const id = window.setInterval(() => {
      setCount((c) => c + step); 
    }, delay);

    return () => window.clearInterval(id);
  }, [delay, step]);
```

Including `step` in the dependency array causes the interval to reset unnecessarily when `step` changes. Excluding it makes React issue a warning. To avoid resetting the interval, we abstract the reactive value (`step`) using `useEffectEvent`:

```jsx
const onStepUpdate = React.useEffectEvent((currentStep) => {
  setCount((c) => c + currentStep);
});

React.useEffect(() => {
  const id = window.setInterval(() => {
    onStepUpdate(step);
  }, delay);

  return () => window.clearInterval(id);
}, [delay]);
```

### When?
When you need to use reactive but **non-synchronizing values** in `useEffect`, use `useEffectEvent` to abstract the logic and avoid unnecessary re-runs.