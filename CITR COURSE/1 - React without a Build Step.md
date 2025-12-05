# React without a Build Step

### TIP:
You can use `npx serve` as a simple way to see a file locally
Also you can generate a quick HTML file in VSCode with Emmet by just typing `!` and then pressing tab

## Lesson Summary
We got a very simple page set up with an `index.html` file. This is the important part of that set up:
```html
  <body>
    <div id="root">not rendered</div>
    <script src="https://unpkg.com/react@18.3.1/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@18.3.1/umd/react-dom.development.js"></script>
    <script src="./src/App.js"></script>
  </body>
```

We then set up `App.js` which first set up the App (a reusable "stamp" of something rendered on the page).

```js
const App = () => {
	return React.createElement( // creates the element (duh)
	  "div", // wrap it all in a div
	  {}, // empty attributes for now
	  React.createElement("h1", {}, "Pixel Perfect Pizzas") // Within the div element, create the title for the page
	);
  };
```
 Beneath that was what hooks this up with the HTML we are serving up locally:
 ```js
  const container = document.getElementById("root"); // grab the "root" of the HTML
  const root = ReactDOM.createRoot(container); // create a ReactDOM root element
  root.render(React.createElement(App)); // use the .render method and pass in your App element
 ```

This is the simplest React application you could possibly have. Next we added another React component (`Pizza`) and played with passing it `props`:

```js
const Pizza = (props) => {
  return React.createElement("div", {}, [
    React.createElement("h1", {}, props.name),
    React.createElement("p", {}, props.description),
  ]);
};

const App = () => {
  return React.createElement("div", {}, [
    React.createElement("h1", {}, "Pixel Perfect Pizzas"),
    React.createElement(Pizza, {
      name: "The Pepperoni Pizza",
      description: "Mozzarella Cheese, Pepperoni",
    }),
    React.createElement(Pizza, {
      name: "The Hawaiian Pizza",
      description: "Sliced Ham, Pineapple, Mozzarella Cheese",
    }),
    React.createElement(Pizza, {
      name: "The Big Meat Pizza",
      description: "Bacon, Pepperoni, Italian Sausage, Chorizo Sausage",
    }),
  ]);
};
```

 ### Quick Facts
- The package that provides access to DOM and server renderers for React is `React-DOM`
- UMD === Universal Module Definition
- The method for creating a root for rendering a React application is `ReactDOM.createRoot()`
- `createElement()` is to create and stamp out a reusable component instance, similar to creating a stamp that can be used multiple times. AKA creates a JavaScript object representing a UI element
- There are two types of components, function components and class components. These examples are function components
- `props` are a way to pass data and configuration to a React component
	- Props are variables that a parent (App) passes to its children (the instances of Pizza.)
