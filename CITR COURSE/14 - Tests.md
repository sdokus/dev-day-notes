# Tests

## When should you add tests
- To keep the main goals of your code in mind
- When you catch a bug to make sure it's fixed and it won't be reintroduced
- Tests should fail fast, fail loudly, and be testing something important
- Prioritize testing user experience

## Vitests / Testing Library React
- You can use `afterEach(cleanUp);` to clear out the testing library after every single test

## Mocking
- The purpose of mocking API requests by enabling fake responses instead of making real network calls, which helps prevent potential issues and allows testing API interactions without actual server dependencies

## Testing Custom Hooks
- One option is to make a fake component that calls the custom hook you want and then just throw it out
- Another option is to use `renderHook` from React
	- Here the helper renderHook abstracts away that oddity we had to do to get that hook tested. But rest assured it's doing essentially the same thing: creating a component under the hood that's running the hook lifecycle methods appropriately for you.
- `waitFor` is a handy trick where you need to wait for React to settle. You give it a body that throws errors until it's true. expect when it doesn't work throws an error so that's how this works.

## Snapshot Testing
- Low confidence, low cost
- Snapshot testing has low confidence, breaks easily with UI changes, can cause cascading test failures across nested components, and requires frequent snapshot updates, making it less reliable for complex or frequently changing components.
- Snapshot testing is most suitable for simple, display-focused components with minimal logic, such as headers, footers, navigation bars, or components that have a relatively stable rendering structure.

## Coverage
- There's something built in to Vite testing that shows you exactly how much of your code is covered by tests and how many times lines of code are hit by your tests.

## React Upcoming Features
- When should developers use useMemo and useCallback?
	- Developers should only use useMemo and useCallback when they have a real performance problem, as these techniques can make code harder to reason about and potentially cause unexpected rendering behavior.
