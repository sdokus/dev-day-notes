# Custom Hooks

Quick Aside: React has a `<Strict Mode>` that you can wrap your App or component in to get additional feedback and double-renders everything for troubleshooting purposes.

Custom Hooks are reusable, composable hooks.

Essentially they are functions that call other hooks (functions). What makes them different than typical functions is that they follow the rules of hooks and therefore must be called in teh same order and not placed inside conditionals or loops.

Custom hooks enable reusable, composable logic that can be shared across different components, reducing code duplication and improving modularity.

Q: What happens if there's a custom hook with a `useEffect` that's waiting on an async function grabbing something from the database and it's taking a long long time?
- His answer talks about how in the custom hook we "schedule an effect to be run", but we initially set the state of `pizzaOfTheDay` to `null`
- "Renders finish first before effects happen"

Naming Conventions:
- Components always start with an uppercase letter
- A convention is to start any custom hook with `use` (this will help linters, but other than that doesn't really matter)
