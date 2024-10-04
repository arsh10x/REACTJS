# React Reconciliation: Working Example

Reconciliation is the algorithm React uses to efficiently update the DOM by comparing the new virtual DOM with the previous one. React identifies what parts of the UI need to be updated and applies changes only where necessary, improving performance.

In this example, we'll demonstrate how React compares two virtual DOM trees and how it updates the actual DOM when a change occurs.

---

## Example: Reconciliation in Action

Below is an example of how React handles the reconciliation process when the root element in the virtual DOM changes.

### Code Example:

```jsx
import React, { useState } from "react";
import ReactDOM from "react-dom";

function App() {
  const [toggle, setToggle] = useState(true);

  return (
    <div>
      <button onClick={() => setToggle(!toggle)}>Toggle Element</button>
      {toggle ? <div><Counter /></div> : <span><Counter /></span>}
    </div>
  );
}

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

ReactDOM.render(<App />, document.getElementById("root"));

# How Reconciliation Works in This Example

In this section, we'll explain the step-by-step process of how React's reconciliation works with the example provided.

---

## 1. Initial Render:
- When the app first loads, the virtual DOM tree consists of a `<div>` wrapping the `<Counter />` component.
- The real DOM is rendered based on this structure.

---

## 2. State Change:
- Clicking the **Toggle Element** button changes the `toggle` state from `true` to `false`, which triggers a re-render of the component.

---

## 3. Tree Diffing:
- React compares the old virtual DOM tree:
  ```jsx
  <div>
    <Counter />
  </div>

<span>
  <Counter />
</span>
