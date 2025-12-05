# TanStack Query

This is showing up how to query the database. We're setting up a 'Past Orders' page

Tanstack Query is a library that simplifies caching API requests across multiple libraries like React, Angular, and Vue. It automates caching logic, handling cache expiry, and hydration without developers needing to write complex caching mechanisms manually.

What are the key benefits of using Tanstack Query?

Tanstack Query simplifies caching API requests, reduces the need for useEffect, handles cache management automatically, allows precaching of data, and provides a consistent approach to managing data fetching and caching across different types of requests.

We set up an `api` directory with a `getPastOrders.js` file that just simply fetches the past order route and response/data

Implicit returns is a thing with arrow functions

TanStack is able to cache things and provides a cool development toolbox on the frontend.

The `queryKey` is used to identify and store a unique query in the cache, allowing TanStack Query to determine whether to return cached data, fetch fresh data, or check if the cached data is stale.
