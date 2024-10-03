### useState Hook

#### What is useState?
useState is a React Hook that allows you to add state to functional components.

#### Why use useState?
- To add state management to functional components
- To track values that change over time
- To trigger re-renders when data changes

#### How to use useState?
```javascript
const [state, setState] = useState(initialValue);
```

- `state`: The current state value
- `setState`: Function to update the state
- `initialValue`: The initial state value

#### Example:
```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
    <p> You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
export default Counter;
```

#### Key Points:
1. useState can be used multiple times in a component
2. When updating state based on previous state, use the functional update form:
   ```javascript
   setCount(prevCount => prevCount + 1)
   ```
3. useState doesn't merge objects like class component's setState
4. The state update function (setState) replaces the previous state entirely

#### Best Practices:
- Use multiple useState calls for unrelated state variables
- Use the functional update form when new state depends on previous state
- Keep state as local as possible to components that need it.