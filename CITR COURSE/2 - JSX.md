# JSX

JSX is a thin layer built over Javascript - it basically is a more human readable way to write javascript, which is translated into HTML.

You have to use `className` instead of `class` when writing HTML because `class` is a reserved keyword in JavaScript for defining classes, so React uses className to avoid syntax conflicts and align with the JavaScript DOM API's naming convention.

With JSX you can start exporting and importing components between files - this can be used for modularization.

Curly braces `{}` allow you to embed any JavaScript expression within JSX, such as calling methods on props (like `props.name.toLocaleUpperCase()`) or inserting dynamic values.

JSX is transformed into `React.createElement()` calls during the build process, effectively creating a thin layer on top of JavaScript that allows writing HTML-like syntax in JavaScript.

Lowercase tags (i.e. `<h1>`) are DOM tags that we're telling JSX we want to render literally, versus capitalizing the tag tells JSX it's a "synthetic" or custom React component (i.e `<Pizza />`).

## Run the API Server
This step is to get access to the API data set up in the repo. First we adjusted the `vite.confic.js` file to add a server/proxy for both `/api` and `/public` on port 3000. This means when the API is requested for these endpoints, we now have the output targeted for `"http://localhost:3000"`, which will avoid CORs issues and run the frontend and backend on the same port.

AKA this is allowing up to import a bunch of images (from `/public` I'm assuming) and pizzas with descriptions and more info (from `/api`, I have to think)

We navigate to the cloned repo and run
```
cd citr-v9-project/api
npm install
npm run dev
```
And this outputs a `Server listening on port 3000` message, meaning that when something is pinged to port 3000 it will now be able to receive that data (I think?)
