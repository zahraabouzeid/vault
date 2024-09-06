_React is a lovechild of HTML and JavaScript_

## Reusability
Let's say we had some HTML:
```html
<aside>
  <h2>Authors</h2>
  <ul>
    <li>Tyler McGinnis</li>
    <li>Ben Adam</li>
    <li>Lynn Fisher</li>
  </ul>
</aside>
```

But what if we wanted to reuse it somewhere else?
Then we just have to use react, so it might look like this:

```javascript
export default function Authors () {
  return <aside>
    <h2>Authors</h2>
    <ul>
      <li>Tyler McGinnis</li>
      <li>Ben Adam</li>
      <li>Lynn Fisher</li>
    </ul>
  </aside>
}
```

Now to re-use it we just have to import it:
```javascript
import Authors from './Authors'

...
	<Authors />
...
```

## Single Responsibilty Principe
- Components and functions should do just one thing.
- If you have a component that's being reused somewhere else, make it its own file. If not, just create it inside of whatever file you need it.

## React and Pure Functions
React embraces [Pure Functions](Pure%20Functions) and, as a rule, you need to make sure your components are always pure.

```javascript
import Authors from "./Authors"

export default function About () {
  localStorage.setItem('viewed_about', true)
  return <main>
    <h1>About Us</h1>
    <p>We write JavaScript and words about JavaScript.</p>
    <Authors />
  </main>
}
```
Using `localStorage.setItem('viewed_about', true)` in the component makes it impure.