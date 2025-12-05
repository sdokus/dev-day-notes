# TanStack Router

Routers are needed once you want to have more than one page on your site.

TanStack Router is more client-side whereas React Router is more balanced between client and server routing.

SPA = single page application --> We're making that but with multiple pages.

We set up a routes directory and then a `__roots.jsx` file where it seems like we're basically pulling things out of `App.jsx`. We're also moving `Order.jsx` there because it's also basically a route.

The double underscore (dunder) (like `routes/__root.jsx`) defines the root route and shared components/code for all routes in the application

The Outlet component represents the area where different page components will be swapped out and rendered when navigating between routes

We're making it lazy. It will now code split this for us and lazy-load our route for us. This really helps in large apps. In this tiny app it probably actually slows us down because adding 1KB to an app doesn't slow it down, but an extra round trip does.

Lazy loading allows components to be loaded only when they are needed, reducing initial page load time and improving performance

`<Link>` handles routing client-side, manages browser history correctly, and prevents full page reloads (versus `<a>` which is an HTML anchor link)
