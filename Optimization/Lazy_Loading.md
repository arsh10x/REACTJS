
# Performance Optimization Techniques

## Lazy Loading

**Definition**: Lazy loading is a technique for loading components or modules only when they are needed.

### Implementation:
Use `React.lazy()` and `Suspense` to dynamically import components.

### Benefits:
- Reduces initial load time.
- Decreases bundle size.

### Example:
```javascript
const LazyComponent = React.lazy(() => import('./LazyComponent'));

function MyComponent() {
  return (
    <React.Suspense fallback={<div>Loading...</div>}>
      <LazyComponent />
    </React.Suspense>
  );
}
```


## Key Takeaways for Interviews

- Performance optimization is crucial for large-scale React applications.
- Lazy loading and code splitting reduce initial load times.
- Asset optimization improves overall application performance.
- `Suspense` enhances user experience during loading states.
- Bundlers play a crucial role in optimizing the final build.
- These techniques often work together to create a smooth, fast user experience.
