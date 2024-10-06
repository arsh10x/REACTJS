## 3. Context

Context provides a way to pass data through the component tree without having to pass props down manually at every level. It's designed to share data that can be considered "global" for a tree of React components.

Steps to use Context:

1. Create a context
```javascript
const UserContext = React.createContext();
```

2. Provide the context
```javascript
function App() {
  const [user, setUser] = useState({name: "John"});
  return (
    <UserContext.Provider value={user}>
      <Main />
    </UserContext.Provider>
  );
}
```

3. Consume the context
```javascript
function GrandChild() {
  const user = React.useContext(UserContext);
  return <p>Hello, {user.name}!</p>;
}
```

Benefits of Context:
1. Solves the prop drilling problem.
2. Makes it easier to share global data.
3. Can make components more reusable as they're not tightly coupled to the data passing mechanism.

Considerations when using Context:
1. Don't overuse it. Not all data needs to be in Context.
2. Can make component reuse more difficult if not structured properly.
3. Changes to Context value will cause all components that use that Context to re-render.
