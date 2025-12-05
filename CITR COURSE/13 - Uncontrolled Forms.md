# Uncontrolled Form

Controlled form = inputs are validated before submission

An uncontrolled form is a form where the browser handles form data management, and you only listen for submit events, rather than explicitly controlling input and output using React hooks.

In TanStack, API requests that change things = mutations = modifying data on the server side and therefore should be called sparingly to avoid unintended side effects.

Queries, on the other hand can be called multiple times without changing the server state.

For this lesson we built out a contact page with a form that people can input non-controlled things. We did this by using a mutation with TanStackQuery.

Use a controlled form when you need to dynamically react to input changes, such as populating a dependent dropdown list based on the selection in another dropdown, or performing real-time validation.
