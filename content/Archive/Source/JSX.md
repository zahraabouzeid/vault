## One top-level element
A JSX Component must be wrapped in an enclosing tag. Instead we can use a fragment element:
```javascript
import * as React from "react"

export default function Authors () {
  return (
    <React.Fragment>
      <h2>Authors</h2>
      <ul>
        <li>Tyler McGinnis</li>
        <li>Ben Adam</li>
        <li>Alex Brown</li>
      </ul>
    </React.Fragment>
  )
}
```
**Shorthand Syntax**
```javascript
export default function Authors () {
  return (
    <>
      <h2>Authors</h2>
      <ul>
        <li>Tyler McGinnis</li>
        <li>Ben Adam</li>
        <li>Alex Brown</li>
      </ul>
    </>
  )
}
```

## Rules
- `class` should be `className`
- CSS properties with a `-` in them must be transformed to a Camel Case
- An expression, basically anything which returns a value like a variable or a function must be wrapped with curly braces.
- Self-closing tags must me explicitly closed. 

## Empty Components
If you want a React component to show nothing, as sometimes is the case when data is still loading, return `null` from your component.
```javascript
if (isLoading() === true) {
  return null
}

return (
  <main>
    <h1>This is JSX</h1>
    <h2>JSX <i>looks</i> like HTML</h2>
  </main>
)
```

## Conditional Rendering
**If-else**
```javascript
function Dashboard () {
  const authed = isAuthed()
  
  if (authed === true) {
    return <h1>Welcome back!</h1>
  } else {
    return <h1>Login to see your dashboard</h1>
  }
}
```

**Ternary operator**
```javascript
function Dashboard () {

  return isAuthed() === true
    ? <h1>Welcome back!</h1>
    : <h1>Login to see your dashboard</h1>
}
```

**{ }**
```javascript
function Dashboard () {
  return (
    <React.Fragment>
      <Logo />
      {isAuthed() === true
        ? <h1>Welcome back!</h1>
        : <h1>Login to see your dashboard</h1>}
    </React.Fragment>
  )
}
```

**null**
```javascript
function Dashboard () {
  return (
    <React.Fragment>
      <Logo />
      {showWarning() === true
        ? <Warning />
        : null}
    </React.Fragment>
  )
}
```

**&&**
```javascript
function Dashboard () {
  return (
    <React.Fragment>
      <Logo />
      {showWarning() === true && <Warning />}
    </React.Fragment>
  )
}
```

## Rendering Lists
**Vue**
```javascript
<ul id="tweets">
  <li v-for="tweet in tweets">
    {{ tweet.text }}
  </li>
</ul>
```

**Angular**
```javascript
<ul id="tweets">
  <li *ngFor="let tweet of tweets">
    {{ tweet.text }}
  </li>
</ul>
```

**React.js**
```javascript
import tweets from "./tweets"

export default function Tweets () {
  return (
    <ul id="tweets">
      {tweets.map((tweet) => (
        <li>{tweet.text}</li>
      ))}
    </ul>
  )
}
```

Whenever you use `.map` to create a list in React, you need to make sure that you add a **unique** `key` prop to each list item.
```javascript
<ul id="tweets">
  {tweets.map((tweet) => (
    <li key={tweet.id}>{tweet.text}</li>
  ))}
</ul>
```