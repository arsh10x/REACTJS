# State Management in React

State management is a crucial aspect of React applications. It involves handling data that can change over time and ensuring that your UI reflects these changes. Let's break down the key concepts:

## 1. State and Props

### State

- State is mutable data that belongs to a component.
- It represents the internal data of a component that can change over time.
- State is managed within the component and can be updated using `setState()` in class components or state update functions in functional components with hooks.

Example (using hooks):
```javascript
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

### Props

- Props (short for properties) are read-only data passed from a parent component to a child component.
- They are immutable and help in making components reusable.
- Props flow down the component tree.

Example:
```javascript
function Parent() {
  return <Child name="John" />;
}

function Child(props) {
  return <p>Hello, {props.name}!</p>;
}
```

Key differences:
1. State is mutable, props are immutable.
2. State is managed within a component, props are passed from parent to child.
3. Updating state triggers a re-render, changing props from a parent also triggers a re-render.




