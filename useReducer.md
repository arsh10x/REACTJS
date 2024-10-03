### useReducer Hook

#### What is useReducer?
useReducer is a React Hook that lets you add a reducer to your component.

#### Why use useReducer?
- To manage more complex state logic in components
- When the next state depends on the previous state
- To optimize performance for components that trigger deep updates

#### How to use useReducer?
```javascript
const [state, dispatch] = useReducer(reducer, initialState, init);
```

- `reducer`: Function that specifies how the state gets updated
- `initialState`: The initial state value
- `init` (optional): Function to calculate the initial state lazily

#### Example:
```jsx
import React, { useReducer } from 'react';

const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);
  return (
    <>
      Count: {state.count}
      <button onClick={() => dispatch({ type: 'increment' })}>+</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
    </>
  );
}

export default Counter;

```

#### Key Points:
1. useReducer is preferable to useState when you have complex state logic
2. It follows the reducer pattern popularized by Redux
3. The reducer function should be pure and return the new state
4. useReducer can be more efficient than useState for deep updates

#### Best Practices:
- Use useReducer for managing state objects with multiple sub-values
- Keep your reducer functions pure - they should calculate the new state based on the action and current state, without side effects
- Use the action type to determine how the state should change
- Consider using useReducer with useContext for managing global state