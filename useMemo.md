### useMemo Hook

#### What is useMemo?
useMemo is a React Hook that lets you cache the result of a calculation between re-renders.

#### Why use useMemo?
- To optimize performance by avoiding expensive calculations on every render
- To memoize values that are expensive to compute
- To ensure referential equality for complex values

#### How to use useMemo?
```javascript
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

- First argument: A function that returns the value you want to memoize
- Second argument: An array of dependencies

#### Example:
```jsx
import React, { useState, useMemo } from 'react';

function ExpensiveComponent({ a, b }) {
  const expensiveResult = useMemo(() => {
    // Imagine this is a very expensive calculation
    console.log('Computing expensive result...');
    return a * b * Math.random();
  }, [a, b]);

  return (
    <div>
      Result: {expensiveResult}
    </div>
  );
}

function App() {
  const [a, setA] = useState(0);
  const [b, setB] = useState(0);

  return (
    <div>
      <input
        type="number"
        value={a}
        onChange={e => setA(Number(e.target.value))}
      />
      <input
        type="number"
        value={b}
        onChange={e => setB(Number(e.target.value))}
      />
      <ExpensiveComponent a={a} b={b} />
    </div>
  );
}

export default App;

```

#### Key Points:
1. useMemo will only recompute the memoized value when one of the dependencies has changed
2. It's useful for expensive calculations that you don't want to run on every render
3. useMemo runs during rendering, so don't put side effects in the memoized function

#### Best Practices:
- Use useMemo for computationally expensive operations
- Ensure all values used in the memoized function are included in the dependency array
- Don't overuse useMemo - for most values, the cost of memoization might be higher than just recalculating the value
- Use useMemo when you need to maintain referential equality for complex objects or arrays that are passed as props to child components using React.memo
