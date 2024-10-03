### useRef Hook

#### What is useRef?
useRef is a React Hook that lets you reference a value that's not needed for rendering.

#### Why use useRef?
- To persist values between renders without causing re-renders
- To access DOM elements directly
- To store mutable values that don't require component re-renders when they change

#### How to use useRef?
```javascript
const refContainer = useRef(initialValue);
```

- `initialValue`: The initial value you want the ref to have (optional)

#### Example:
```jsx
import React, { useRef, useEffect, useState } from 'react';

function TextInputWithFocusButton() {
  const inputEl = useRef(null);

  const onButtonClick = () => {
    // `current` points to the mounted text input element
    inputEl.current.focus();
  };

  return (
    <>
      <input ref={inputEl} type="text" />
      <button onClick={onButtonClick}>Focus the input</button>
    </>
  );
}

function Timer() {
  const [count, setCount] = useState(0);
  const intervalRef = useRef();

  useEffect(() => {
    intervalRef.current = setInterval(() => {
      setCount(c => c + 1);
    }, 1000);
    return () => clearInterval(intervalRef.current);
  }, []);

  return <div>Timer: {count}</div>;
}

export default function App() {
  return (
    <div>
      <TextInputWithFocusButton />
      <Timer />
    </div>
  );
}

```

#### Key Points:
1. useRef returns a mutable ref object whose `.current` property is initialized to the passed argument (initialValue)
2. The returned object will persist for the full lifetime of the component
3. Changing a ref doesn't cause a re-render
4. useRef can be used to store any mutable value, not just DOM refs

#### Best Practices:
- Use useRef to access DOM elements directly when necessary
- Use useRef to store mutable values that don't require the component to re-render when they change
- Avoid overusing refs - most of the time, you should use state for values that affect the component's rendering
- Remember that updating a ref doesn't trigger a re-render, so don't use it for values that should cause the UI to update