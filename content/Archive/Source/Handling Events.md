## Creating an Alerting Event
```javascript
export default function AlertButton({ message }) {
	const handleCLick = () => alert("Alert!")
	return (
		<button onClick={handleClick}>
			Alert
		</button>
	)
}
```

Whenever a `button` is clicked, React will invoke `handleClick`.

**Common Practices**
- Encapsulate the event handler into its own function
- Name the function `handle` + the event name.

**Passing the handler as reference and not as an invocation**
```javascript
<button onClick={handleClick}>
	Passing a Reference
</button>
<button onClick={handleClick()}>
	Passing an Invocation			 
</button>
```

- If we pass an invocation to an event, the JavaScript engine will immediately invoke the function and pass the return value to the event.
- If we pass a reference to the function to an event, the function will be invoked, when the event occurs.

**Scope**
By declaring our `handleClick` function inside of our component, we automatically have access to the `message` prop without the need to use arguments.

**Performance**
Declaring the function outside of the component is better for the performance, because if it's inside the component, then JavaScript will have to create a new function every time the component renders. But we should not worry about that as JavaScript is really good at creating and destroying functions.


