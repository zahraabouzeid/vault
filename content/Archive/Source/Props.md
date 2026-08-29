Props are to components what arguments are to functions.
## Passing Props to Components
Any Prop that isn't a string must be wrapped with curly braces:
```javascript
	<Profile
		username="tylermcginnis"
		authed={true}
		logout={handleLogout}
		header={<h1>Hello!</h1>}
	/>
```

**Boolean Shortcut**
If you pass a prop without a value, that value will be set to `true`. 

```javascript
	<Profile authed={true} />
	<Profile authed />
```

## Accessing props
**Objects**
```javascript
function Hello (props) {
  return (
    <h1>
      Hello, {props.first} {props.last}
    </h1>
  )
}
```

**Destructuring**
```javascript
function Hello ({ first, last }) {
  return (
    <h1>
      Hello, {first} {last}
    </h1>
  )
}
```

## Accessing Childrens
Let's say we want to access what is inside these components:
```HTML
<Header>You can have text between tags.</Header>
<Layout>
  <h1>You can also have</h1>
  <p>elements between tags</p>
</Layout>
```

For that we access them via `props.children`:
```javascript
function Header (props) {
  return <h1 className="header">{props.children}</h1>
}

function Layout (props) {
  return (
    <div className="layout">
      <Sidebar />
	      {props.children}
      <Footer />
    </div>
  )
}
```