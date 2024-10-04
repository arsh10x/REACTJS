## 2. Prop Drilling

Prop drilling occurs when you need to pass data through multiple levels of components that don't need the data themselves, just to get it to a deeply nested component.

Example of prop drilling:
```javascript
function GrandParent() {
  const [user, setUser] = useState({name: "John"});
  return <Parent user={user} />;
}

function Parent({user}) {
  return <Child user={user} />;
}

function Child({user}) {
  return <GrandChild user={user} />;
}

function GrandChild({user}) {
  return <p>Hello, {user.name}!</p>;
}
```

Problems with prop drilling:
1. Makes code harder to maintain and refactor.
2. Can lead to unnecessary re-renders.
3. Makes components less reusable as they become tightly coupled to the data they're passing along.