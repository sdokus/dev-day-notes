# Error Boundaries

Error Boundaries are a way to be defensive about potential API errors by creating a class component that can wrap your other components to handle errors better.

You wrap the error boundary around components because if it's just next to a component it won't catch the error and the component will just blow up withtout the error(s) being caught effectively.

Adding the Error Boundary at the root of the application is recommended so you handle all errors throughout the application.

Once wrapped, now anything that is a child of this component will have errors caught here. Think of this like a catch block from try/catch.

`componentDidCatch` is important to the Error Boundary as well:
```jsx
  componentDidCatch(error, info) {
    console.error("ErrorBoundary caught an error", error, info);
  }
  render() {
    if (this.state.hasError) {
      return (
        <div className="error-boundary">
          <h2>Uh oh!</h2>
          <p>
            There was an error with this listing. <Link to="/">Click here</Link>{" "}
            to back to the home page.
          </p>
        </div>
      );
    }

    return this.props.children;
  }
```

## What does an Error Boundary component do when an error occurs?

It catches rendering errors in its child components, prevents the entire application from crashing, and can display a fallback UI or error message

## Why are Error Boundaries still implemented as class components in React?

Functional components lack the necessary lifecycle methods to handle errors comprehensively, so class components remain the preferred method for creating Error Boundaries
