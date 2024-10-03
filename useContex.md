### useContext Hook

#### What is useContext?
useContext is a React Hook that allows you to consume context in a functional component.

#### Why use useContext?
- To access shared data without passing props through every level
- To avoid prop drilling in deeply nested component trees
- To provide a way to manage global state in your application

#### How to use useContext?
```javascript
const value = useContext(MyContext);
```

- `MyContext`: The context object created with React.createContext()
- `value`: The current context value, determined by the nearest MyContext.Provider

#### Example:
```jsx
import React, { createContext, useContext, useState } from 'react';

const ThemeContext = createContext();

function ThemeProvider({ children }) {
  const [theme, setTheme] = useState('light');

  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      {children}
    </ThemeContext.Provider>
  );
}

function ThemedButton() {
  const { theme, setTheme } = useContext(ThemeContext);

  return (
    <button
      onClick={() => setTheme(theme === 'light' ? 'dark' : 'light')}
      style={{
        background: theme === 'light' ? '#fff' : '#000',
        color: theme === 'light' ? '#000' : '#fff',
      }}
    >
      Toggle Theme
    </button>
  );
}

function App() {
  return (
    <ThemeProvider>
      <ThemedButton />
    </ThemeProvider>
  );
}

export default App;

```

#### Key Points:
1. useContext must be used with a Context object created by React.createContext()
2. The component calling useContext will re-render whenever the context value changes
3. useContext always looks for the nearest Provider above it in the tree

#### Best Practices:
- Use context for global state that many components need to access
- Keep context values as specific as possible to avoid unnecessary re-renders
- Consider using multiple contexts for different parts of your application state
- Use context in combination with useReducer for more complex state management