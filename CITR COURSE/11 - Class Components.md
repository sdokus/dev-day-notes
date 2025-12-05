# Class Components

Generally not used any more, function components are more popular nowadays but these are still out there in older React codebases.

Every React component has a render section. In this example, it's the user-facing error page.

There's a constructor, which you have to pass it `super(props)`

Class Components get a bit more complicated with the use of `this`

Class components cannot use hooks, have their own state management with this.`setState`, use lifecycle methods like `componentDidMount`, and require binding methods or using arrow functions to maintain correct context. Function components use hooks like `useState` and `useEffect`, have simpler syntax, and do not require method binding.

Key lifecycle methods include `componentDidMount` (runs once when the component is first rendered), `componentWillUnmount` (runs when the component is removed from the DOM), `componentDidUpdate` (runs every time the component's state changes), and the `constructor` (initializes the component and sets initial state).

Since class components cannot directly use hooks, you can create a function component that runs the hook and then passes the hook's result as a prop to the class component. This allows you to indirectly use hook functionality within a class component.

A static method is called directly on the uninstantiated class, rather than on an instance of the class. In React class components, static methods like `getDerivedStateFromError` are used to handle special scenarios, such as managing state when an error occurs.

An error boundary is a class component that catches JavaScript errors anywhere in its child component tree, logs those errors, and displays a fallback UI instead of the component tree that crashed. It prevents the entire application from breaking when an error occurs in a specific component.
