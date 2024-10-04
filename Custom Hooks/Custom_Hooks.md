# Custom Hooks in React

## What are Custom Hooks?

Custom hooks are a mechanism to reuse stateful logic across multiple components in React applications. They allow you to extract component logic into reusable functions.

## When to Use Custom Hooks

Use custom hooks when you:

1. Find yourself repeating the same stateful logic in multiple components
2. Need to share complex logic between components
3. Want to make your components cleaner and more focused on rendering
4. Need to compose multiple hooks into a single, more powerful hook

## Key Points for Interviews

1. Custom hooks always start with "use" (e.g., useCounter, useFetch)
2. They can use other hooks like useState, useEffect, etc.
3. They don't render anything; they just return values and functions
4. They follow the same rules as regular hooks (only call at the top level, only call from React functions)

## Code Example: useCounter Hook

```javascript
import { useState, useCallback } from 'react';

function useCounter(initialValue = 0) {
  const [count, setCount] = useState(initialValue);

  const increment = useCallback(() => {
    setCount(prevCount => prevCount + 1);
  }, []);

  const decrement = useCallback(() => {
    setCount(prevCount => prevCount - 1);
  }, []);

  const reset = useCallback(() => {
    setCount(initialValue);
  }, [initialValue]);

  return { count, increment, decrement, reset };
}

// Usage in a component
function CounterComponent() {
  const { count, increment, decrement, reset } = useCounter(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
      <button onClick={reset}>Reset</button>
    </div>
  );
}
```

## Explanation

1. We define `useCounter`, a custom hook that manages a counter's state and operations.
2. It uses `useState` to manage the count state.
3. `increment`, `decrement`, and `reset` functions are created using `useCallback` to optimize performance.
4. The hook returns an object with the current count and functions to manipulate it.
5. In `CounterComponent`, we use our custom hook, demonstrating how it simplifies the component's code.

## Benefits

1. Reusability: The same hook can be used in multiple components.
2. Separation of Concerns: Logic is separated from the component's rendering.
3. Testability: Custom hooks can be tested independently of components.
4. Composition: Complex logic can be built by combining multiple hooks.
