# Context

Context is _not_ one way directional, it's more like a portal that you can dump things into, or App-level state, OR a way of keeping state even if the component is unmounted.

For this, we created a new file `contexts.jsx` where we imported `createContext` and then wrote one line:
```jsx
export const CartContext = createContext([[], function () {}]);
```
Be very sparing with use of Context.

Examples are:
- Logged in users
- Themes
- Carts

You can have multiple Contexts on the same App, the component being rendered will jump to the nearest one when it's trying to get state (?)

Context allows data to be shared across components without explicitly passing props through each level, while useState with prop passing requires manually passing state and setter functions down the component tree. Context provides a more centralized and less verbose way of managing shared state.
