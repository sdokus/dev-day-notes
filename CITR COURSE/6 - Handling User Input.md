# Handling User Input

We're adding the Cart component to handle when users actually try to buy the pizza.

In the form, we add `onSubmit` to the form element in favor over an `onClick` on the button element to be more accessible if folks hit enter to submit the form.

When creating the Cart we make an unordered list of the items being added to the cart. This is a situation where using the index as they key is okay because there might be non-unique items (like if someone orders 3 of the same pizza)

Props are things that are passed from parent to child in a one way direction. A component can only modify its own state.

Props are immutable data passed from parent to child components, while state is mutable data that a component can modify internally

How can a child component affect its parent's data?
By passing a function from the parent to the child, which the child can call to modify the parent's state
