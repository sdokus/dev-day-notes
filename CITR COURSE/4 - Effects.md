# Effects

Often combined with State, Effects are most often API requests.

Derivative State

Typically, a React Component is structured like:
```jsx
// imports

// variables that need to be defined outside the function component

export default function Component(){
	// State variables

	// useEffect
}

```
The `useEffect` hook is used for handling side effects in React components, such as API requests, setting up timers, or performing actions that occur outside the normal render cycle. It allows you to execute code at specific points in a component's lifecycle, like when the component first loads or when certain dependencies change.

`useEffect` is for when you want to grab something from your API but just on the first page load. For example:
```jsx
  useEffect(() => {
    fetchPizzaTypes();
  }, []); // Second variable is saying "just run this once, don't track against other variables

  async function fetchPizzaTypes() {
    const pizzasRes = await fetch("/api/pizzas");
    const pizzasJson = await pizzasRes.json();
    setPizzaTypes(pizzasJson);
    setLoading(false);
  }
```

For `useEffect` the second variable is for checking "has this variable changed from something different than this? If so, let's re-render"

XHR === Ajax requests

Async functions always return a Promise, but `useEffect` expects its callback to either return `undefined` or a cleanup function. To use an async function within `useEffect`, you should define a separate async function inside the effect and then call it.

Derivative state refers to state values that can be calculated directly from other state or props, and therefore do not need to be managed as a separate state using hooks. These values can be computed using normal variables or functions based on existing state.

TIP: You can create an artificial delay by creating a new Promise that resolves after a specified time using methods like `new Promise((resolve) => setTimeout(resolve, milliseconds))`.

What is the difference between an expression and a statement in JavaScript?

An expression is a piece of code that produces a value and can be part of a line, while a statement is a complete line of code that performs an action. Ternary operators are expressions because they return a value.

