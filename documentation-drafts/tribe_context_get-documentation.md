# `tribe_context()->get();` Cheat Sheet

## What is the `->get()` method within `tribe_context()`?
While `->is()` returns a boolean for if the location has been set, *`->get()` returns the value for that location key*

## What can you pass to `->get()`?
Any *location* available based on the plugins you have active. The `Tribe__Context` class maintains a list of registered context locations, each associated with a specific data field or functionality.

