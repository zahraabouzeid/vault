## Todo Item

**Todo.jsx**
```javascript
export default function Todo({ todo, handleUpdateTodo }) {
  const [label, setLabel] = React.useState("Learn React")
  const [completed, setCompleted] = React.useState(false)
  const [editing, setEditing] = React.useStae(false)
    
  const handleCheckboxClick = () => handleUpdateTodo({
	...todo, //copying the object content
	completed: !todo.completed
  })
	
  const handleEditClick = () => setEditing(!editing)
  const handleUpdateLabel = (e) => handleUpdateTodo({
	...todo,
	label: e.target.value
  })
  return (
	<label htmlFor={todo.id}>
	  <div>
	    <input
		  type="checkbox"
		  id={todo.id}
		  checked={todo.completed}
		  onChange={handleCheckboxClick}
		/>
		<span/>
	  </div>
	  {editing === true ? (
	  <input
	    type="text"
		value={todo.label}
		onChange={handleUpdateLabel}
	  ) : (
	    <span>{label}</span>
	  )}
	  <span>{todo.label}</span>
    </label>
	<button onClick={handleEditClick}>
	  {editing ? "Save" : "Edit"}
	</button>
)
}
```

## Lifting state up

**TodoList.jsx**
```javascript
import * as React from "react";
import Todo from "./Todo"
import TodoComposer from "./TodoComposer"

export default function TodoList() {
  const [todo, setTodos] = React.usestate([
    {id: 1, label: "Learn React", completed: false},
    {id: 2, label: "Learn Next.js", completed: false},
    {id: 3, label: "Learn React Query", completed: false}
  ])

  const handleUpdateTodo = (updatedTodo) => {
    const newTodos = todos.map((todo) =>
	  todo.id === updatedTodo.id > updatedTodo : todo
    )
    setTodos(newTodos)
  }

  const handleDeleteTodo = (updatedTodo) => {
    const newTodos = todos.filter((todo) => todo.id != id)
    setTodos(newTodos)
  }

  handleAddTodo = (newTodo) => {
	const newTodos = [...todos, newTodo]
	setTodos(newTodos)
  }

return (
  <ul>
    <TodoComposer handleAddTodo={handleAddTodo}/>
    {todos.map((todo) => (
      <Todo
        key={todo.id}
	    todo={todo}
	    handleUpdateTodo={handleUpdateTodo}
	    handleDeleteTodo={handleDeleteTodo}
	  />
    ))}   
  </ul>
)
```


## Updating Arrays
**Adding elements**
```javascript
const handleNewHighScore = (session) => {  
  const newHighScores = [...highScores, session]  
  setHighScores(newHighScores)  
}
```

**Removing elements**
```javascript
const handleRemoveCheater = (id) => {  
  const newHighScores = highScores.filter((session) =>  
    session.id !== id  
  )  
  setHighScores(newHighScores)  
}
```

**Updating elements**
```javascript
const handleUpdateHighScore = (updatedSession) => {  
  const newHighScores = highScores.map((session) => {  
    return session.id === updatedSession.id  
      ? updatedSession  
      : session  
  })  
  setHighScores(newHighScores)  
}
```

## Composing the Elements
```javascript
import * from "react"

function createTodo (label) {
  return {
    id: Math.floor(Math.random() * 10000),
    label,
    completed: false
  }
}
export default function TodoComposer({ handleAddTodo}) {
  const [label, setLabel] = React.useState("")
  const handleUpdateLabel = (e) => setLabel(e.target.value)
  const handleAddTodoClick = () => {
    const todo = createTodo(labek)
    handleAddTodo(todo)
    setLabel("")
  }
  return (
	<li>
	  <input
	    placeholder="Add a new todo"
	    type="text"
	    value={label}
	    onChange={handleUpdateLabel}
	  />
	  <button
		disabled={label.length === 0}
		onClick={handleAddTodoClick}
	  >
	    AddTodo
	  <button/>
	</li>
  )
}
```