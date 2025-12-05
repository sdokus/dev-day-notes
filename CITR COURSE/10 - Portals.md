# Portals

## What are Portals?
They're like modals or for rendering things outside your app that can still relate to your app

 React Portal allows rendering a component's children into a different part of the DOM tree outside of the component's own hierarchy, which is particularly useful for rendering elements like modals or side navigation elements that need to break out of the standard component structure.

`elRef` = "Element" Reference

`Modal.jsx` uses a ref. A ref is a reference to something that need to be exactly the same between renders. A hook would get regenerated / recreated so we need a ref because it'll create a div and then it hand back the same div every render. It's important that it's the same div because it'll be the one we use to render the portal.

We're using createPortal to render into this new modal div we're chosen for our modal. But this could be a contextual nav or any other DOM div we want.
We use the returned function on the effect to clean up when this Modal is unmounted from the DOM. Otherwise we'd leak memory.

## Children
Whatever is inside of the outer div/component = children
Typically `props.children` but can be destructured as `{children}`

## How does the useRef hook help in managing DOM elements in React?
The useRef hook creates a mutable reference object that persists across renders, allowing you to reference the same DOM element or store mutable values without causing re-renders. Its .current property can be modified directly without triggering a component re-render.

When setting up the query for getting a past order, we used:
```jsx
  const { isLoading: isLoadingPastOrder, data: pastOrderData } = useQuery({
    queryKey: ["past-order", focusedOrder],
    queryFn: () => getPastOrder(focusedOrder),
    enabled: !!focusedOrder,
    staleTime: 24 * 60 * 60 * 1000, // one day in milliseconds,
  });
```
The `enabled` property allows conditional execution of a query, preventing the query from running if the specified condition is false, such as only fetching data when a specific value (like focusedOrder) exists
