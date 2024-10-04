
# Redux Overview

### How:
Redux is a state management library for JavaScript applications. It stores the entire application state in a single centralized object called the "store". Components can access this state and dispatch actions to update it.

### Why:
Redux provides a predictable and manageable way to handle state in complex applications. It makes it easier to track changes, debug, and maintain consistency across the app.

### Where:
Redux is commonly used in large-scale React applications, but it can be used with any JavaScript framework or library. It's particularly useful in apps with complex data flows or those requiring frequent state updates.

## Key Points to Remember:
- **Single source of truth**: The entire state of the application is stored in the store.
- **State is read-only**: State can only be changed by dispatching actions.
- **Pure functions (reducers)**: Changes are made using pure functions called reducers.

---

## Creating a Reducer:

A reducer is a pure function that takes the current state and an action, and returns the new state. Here's a basic example:

```javascript
const initialState = { count: 0 };

function counterReducer(state = initialState, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    case 'DECREMENT':
      return { count: state.count - 1 };
    default:
      return state;
  }
}
```

### Using Redux Toolkit's `createSlice`:

Redux Toolkit simplifies creating reducers with `createSlice`:

```javascript
import { createSlice } from '@reduxjs/toolkit';

const counterSlice = createSlice({
  name: 'counter',
  initialState: { count: 0 },
  reducers: {
    increment: (state) => {
      state.count += 1;
    },
    decrement: (state) => {
      state.count -= 1;
    },
  },
});

export const { increment, decrement } = counterSlice.actions;
export default counterSlice.reducer;
```

---

## Hooks in Redux:

### `useSelector`:

`useSelector` is a hook provided by React-Redux to extract data from the Redux store state in your components. It subscribes to the store and re-renders the component when the selected state changes.

```javascript
import { useSelector } from 'react-redux';

function CounterDisplay() {
  const count = useSelector((state) => state.counter.count);
  return <div>Count: {count}</div>;
}
```

### `useDispatch`:

`useDispatch` returns a reference to the dispatch function from the Redux store, which allows you to dispatch actions to update the state.

```javascript
import { useDispatch } from 'react-redux';
import { increment, decrement } from './counterSlice';

function CounterButtons() {
  const dispatch = useDispatch();

  return (
    <div>
      <button onClick={() => dispatch(increment())}>Increment</button>
      <button onClick={() => dispatch(decrement())}>Decrement</button>
    </div>
  );
}
```

---

## Unidirectional Data Flow:

1. Components read the state with `useSelector`.
2. User interactions trigger `dispatch` using `useDispatch`.
3. Reducers process these actions and update the state.
4. The updated state flows back to the components, causing re-renders as needed.
