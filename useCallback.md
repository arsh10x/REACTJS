### useCallback Hook

#### What is useCallback?
useCallback is a React Hook that lets you cache a function definition between re-renders.

#### Why use useCallback?
- To optimize performance by preventing unnecessary re-renders of child components
- To maintain referential equality of functions across renders
- To avoid recreating functions on every render, especially when passed as props

#### How to use useCallback?
```javascript
const memoizedCallback = useCallback(
  () => {
    doSomething(a, b);
  },
  [a, b],
);
```

- First argument: The function you want to memoize
- Second argument: An array of dependencies

#### Example:
```jsx
import React, { useState, useCallback } from 'react';

const ExpensiveComponent = React.memo(({ onClick }) => {
  console.log('ExpensiveComponent rendered');
  return (
    <button onClick={onClick}>Click me</button>
  );
});

function App() {
  const [count, setCount] = useState(0);

  const handleClick = useCallback(() => {
    console.log('Button clicked');
  }, []); // Empty dependency array means this function never changes

  return (
    <div>
      Count: {count}
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <ExpensiveComponent onClick={handleClick} />
    </div>
  );
}

export default App;

```

#### Key Points:
1. useCallback returns a memoized version of the callback that only changes if one of the dependencies has changed
2. It's useful when passing callbacks to optimized child components that rely on reference equality to prevent unnecessary renders
3. useCallback is often used in conjunction with React.memo for child components

#### Best Practices:
- Use useCallback when passing functions as props to child components, especially if those components are memoized with React.memo
- Ensure all values from the component scope that the callback function uses are included in the dependency array
- Don't overuse useCallback for every function in your component - use it when it provides a tangible performance benefit
- Consider using useCallback when the function is a dependency for other hooks like useEffect