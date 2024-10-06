## Code Splitting

**Definition**: Dividing your code into smaller chunks to be loaded on demand.

### Implementation:
Use `dynamic import()` syntax or `React.lazy` for component-level splitting.

### Benefits:
- Reduces initial bundle size.
- Improves application load time.

### Example:
```javascript
import('./module').then(module => {
  // Use the module
});
```

---