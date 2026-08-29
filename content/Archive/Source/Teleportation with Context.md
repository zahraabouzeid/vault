## React Context

React Context solves the problem of passing props through deeply nested components by teleporting data.
## How to use it?
1. **Creating the ~~teleporter~~ Context**
 ```jsx
import * as React from "react"

const delorean = React.createContext()

export default delorean
```
2. **Deciding what we want to teleport and to where**
Creating a `Provider` that accepts a `value` prop which is the data that you want to teleport to any component in `Provider`'s subtree.
```jsx
import * as React from "react"
import delorean from "./delorean"
import EighteenEightyFive from "./EighteenEightyFive"
import NineteenFiftyFive from "./NineteenFiftyFive"
import NineteenEightyFive from "./NineteenEightyFive"
import TwoThousandFifteen from "./TwoThousandFifteen"

export default function App () {
  const marty = {
    name: "Marty McFly",
    age: 17,
    occupation: "High School Student",
    catchphrase: "Whoa, this is heavy.",
  }

  return (
    <delorean.Provider value={marty}>
      <TwoThousandFifteen />
      <NineteenEightyFive />
      <NineteenFiftyFive />
      <EighteenEightyFive />
    </delorean.Provider>
  )
}
```
3. **Getting what we teleported from inside a component**
To get access to what was passed to the `Provider`'s `value` prop, you use React's `useContext` hook, passing it the Context as the first argument.
```jsx
import * as React from "react"
import delorean from "./delorean"

export default function Cafe80s () {
  const marty = React.useContext(delorean)

  return (
    <div className="location">
      <h3>Cafe80s</h3>
      <p>Step back in time and join us at Cafe 80's for a blast from the past!</p>
      <h4>Current Guests</h4>
      <ul>
        <li>{marty.name}: Age {marty.age}. {marty.occupation}.</li>
      </ul>
    </div>
  )
}
```
## What if there is no `Provider` component above it in the component tree?
In that case, it'll get its value from the first argument that was passed to `createContext` when the Context object was created.

```jsx
const MyContext = React.createContext("defaultValue")
```

