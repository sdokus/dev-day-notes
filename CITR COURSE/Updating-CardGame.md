# Updating The Game Card Game

## Following the Complete Intro to React (CITR) Course, I want to apply my learning to a project I started when I first learned React back in 2022!

## Add Test Driven Development
The first thing I did was read through all my files and I noticed that there were no tests, just one that was auto-generated when I first started the project.

I just added some simple tests to match the very basic expectations of the app:
1) The Instructions render in an alert
2) There is one draw deck with 98 cards to start
3) There are two incrementing decks and two decrementing decks
4) Clicking on the "Deal Cards" button leads to cards being added to the user's hand

From the class, this used the `@testing-library/react` and the `getByRole()` function

## Update React Version
I was originally using React version 17.0.2, so we need to update React to version 18.2.0
In `index.js` I was still using `ReactDOM.render` which could now be updated to `createRoot`

However, once updated, I found out that the library I was using for drag and drop (`react-beautiful-dnd`) is not compatible with React 18. I switched to use `dnd-kit` instead

## Update Components to `JSX` files
I had Cursor update my components to `.jsx` instead of just `.js` so I could practice applying the syntax for JSX. This was pretty simple, just updating some paths and `class` to `className`, etc etc.

## Revisit Custom Hooks
I was trying to add some custom hooks - `useCards` which seemed to be working, and `useDragNDrop` which (based on my comments) looked like I might have abandoned in favor of `react-beautiful-dnd`, but I'm not fully sure.

Either way, I wasn't actually importing or using my `useDragNDrop` hook anywhere, but I was able to actually use it and extract some drag and drop logic from the `Deck` component. 
