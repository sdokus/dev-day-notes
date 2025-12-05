# React Hooks

Key Concept: You want to keep your rendered components are simple as possible, keeping track of state outside of components.

Ensure that the component always produces the same markup given the same inputs, regardless of when it is rendered.

Difference between using an arrow function and a named function in a React component is a named function will show up in stack traces during debugging, making it easier to identify the source of errors

Two way data binding is not free in React.

`import { useState } from 'react';` --> when the component is re-rendered, it will use this hook to "remember" what the dynamic data is.

A hook is a special function in React that allows functional components to use state and other React features. useState is the most common hook, which returns an array with the current state value and a function to update that state.

`useState` is called with a default value and returns an array with two elements: the current state value and a setter function to update that state. For example, `const [pizzaType, setPizzaType] = useState('pepperoni')` creates a state variable with an initial value of 'pepperoni'.

`const [pizzaType, setPizzaType] = useState("pepperoni")`
AKA
`const [thing, setTheThing] = useState("default")`

** Always set a default value **

To make this value dynamic, add the `onChange` function to the select:
```jsx
	<select
		onChange={(e) => setPizzaType(e.target.value)}
		name="pizza-type"
		value={pizzaType}
	>
```
What is the purpose of the onChange event handler in React form elements?

The `onChange` event handler allows updating the component's state when a user interacts with a form element, triggering a re-render and ensuring the component's state reflects the user's input.

Never use hooks in conditionals or loops! They depend on being called in the same order every time so they should always be at the top level.

`useRef` is a React Hook that provides a way to create a mutable reference object that persists across component renders without causing a re-render when its value is updated.

`useRef` returns a plain JavaScript object with a single property: `current`.
The value assigned to `current` persists across component renders.
Updating the `current` property of a ref does not trigger a re-render of the component, unlike updating state with `useState`
