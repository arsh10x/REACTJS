### useEffect Hook

#### What is useEffect?
useEffect is a React Hook that let's you synchronize a component with an external system or perform side effects in functional components.

#### Why use useEffect?
- To perform side effects (data fetching, subscriptions, DOM manipulation)
- To replace lifecycle methods in class components
- To synchronize your component with external systems

#### How to use useEffect?
```javascript
useEffect(() => {
  // Effect code
  return () => {
    // Cleanup code (optional)
  };
}, [dependencies]);
```

- First argument: Function containing the effect code
- Return value (optional): Cleanup function
- Second argument: Array of dependencies

#### Dependency Array:
- The dependency array is the second argument passed to useEffect. It determines when the effect should run:

- Empty array []: Effect runs only once after initial render
- Array with values: Effect runs when any value in the array changes
- No array: Effect runs after every render
- Helps optimize performance and prevent unnecessary re-renders
- Should include all variables from component scope used in the effect

#### Examples:
1. Effect that runs on every render:
```javascript
useEffect(() => {
  console.log('This runs after every render');
});
```

2. Effect that runs only when a specific value changes:
```javascript
useEffect(() => {
  document.title = `You clicked ${count} times`;
}, [count]);
```

3. Effect that runs only once (on mount):
```javascript
useEffect(() => {
  const subscription = subscribeToData(dataId);
  return () => subscription.unsubscribe();
}, []); // Empty dependency array
```

#### Key Points:
1. useEffect runs after every render by default
2. The dependency array controls when the effect runs
3. Cleanup functions prevent memory leaks and run before the component unmounts
4. Multiple useEffect hooks can be used for separation of concerns

#### Best Practices:
- Use multiple useEffect hooks to separate unrelated logic
- Always include all variables used in the effect in the dependency array
- Use the ESLint rule 'exhaustive-deps' to help manage dependencies
- Avoid infinite loops by carefully managing state updates in effects.