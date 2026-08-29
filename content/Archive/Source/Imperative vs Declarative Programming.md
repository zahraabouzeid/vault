Imperative programming is **how** you do something, and declarative programming is more like **what** you do. React is **declarative**. What makes React Declarative is that it describes what the UI is based on state. It is an abstraction over imperative code.

## Imperative
C, C++, Java
- Relies on context making it difficult to reuse
- Gives procedural instructions on how to do something
- ls explicit about the changes it wants to make
## Declarative
HTML and SQL
- Is offen an abstraction over imperative code
- Is typically context independent
- Is written primarily for humans, not computers

## Both
- JavaScript
- C#
- Python

## Examples
### Example 1
Write a function called `double` which takes in an array of numbers and returns a new array after doubling every item in the original array.

**Imperative**
```javascript
function double(arr) {
  let result = [];
  arr.forEach(element => result.push(element * 2));
  return doubledArray;
}

let originalArray = [1, 2, 3, 4, 5];
let doubledArray = double(originalArray);

console.log("Original Array:", originalArray);
console.log("Doubled Array:", doubledArray);
```

**Declarative**
```javascript
function double(arr) {
  return arr.map((item) => item * 2);
}
```
### Example 2
Write a function called `add` which takes in an array and returns the result of adding up every item in the array.

**Imperative**
```javascript
function add(arr) {
	let result = 0;
	arr.forEach(element => result += element);
	return result;
}

let sum = add([1, 3, 5, 2]);
console.log(sum);
```

**Declarative**
```javascript
function add(arr) {
  return arr.reduce((prev, current) => prev + current, 0);
}
```



