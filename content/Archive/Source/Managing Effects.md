## Side Effects
- The function `v = f(s)` in React that calculates the View needs to be a pure calculation.
- When a React calls a component, it should get the UI description without running into side effects.
- Anytime that a function does anything else, than taking some input and returning a value, it has side effects.
- In React, when a component does anything else than returning the View, it has side effects. That means API calls, manual DOM manipulation, using browser APIs like `local Storage` or `setTimeout`.

## How to manage Side Effects?
 If a side effect is triggered by an event, put that side effect in an event handler.
```javascript
const handleClick = () => {
    const nextIndex = index === greetings.length - 1
      ? 0
      : index + 1
    setIndex(nextIndex)
  }

  localStorage.setItem("index", index)
```


 ```javascript
const handleClick = () => {
    const nextIndex = index === greetings.length - 1
      ? 0
      : index + 1
    setIndex(nextIndex)

    localStorage.setItem("index", nextIndex)
  }
```

 If a side effect is triggered by an event, put that side effect in an event handler.
 ```javascript
import * as React from "react"

export default function BatteryLevel() {
  const [level, setLevel] = React.useState(0)

  React.useEffect(() => {
    console.log("Getting battery level...")
    navigator.getBattery().then(battery => {
      const newLevel = Math.round(battery.level * 100)

      if (newLevel !== level) {
        setLevel(newLevel)
      }
    })
  }, [])

  console.log("Rendering")
  return (
    <p>{level}%</p>
  )
}
```


## useEffect
The second argument in `useEffect` tells React **when** to invoke the effect, by giving React **all the dependencies** that effect needs to run:
```javascript
React.useEffect(() => {
  document.title = `Welcome, ${name}`
}, [name])
```

## Reactive Values
A reactive value is any value that can change between re-renders. Props, state, or any variables defined inside of a component are all reactive values – and therefore, always need to be included in the dependency array if they're used in the effect.


>[!info]
>### Rule #1
>If a side effect is triggered by an event, put that side effect in an event handler
> ### Rule #2
> If a side effect is synchronizing your component with some outside system, put that side effect inside useEffect
> ### Rule #3
If a side effect is synchronizing your component with some outside system and that side effect needs to run *before* the browser paints the screen, put that side effect inside useLayoutEffect
> ### Rule #4
If a side effect is subscribing to an external store, use the useSyncExternalStore hook