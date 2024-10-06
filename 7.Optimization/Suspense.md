## Suspense

**Definition**: A React feature that lets components "wait" for something before rendering.

### Use cases:
- Data fetching.
- Code splitting.

### Benefits:
- Improves user experience by showing fallback content while loading.

### Example:
```javascript
<Suspense fallback={<Spinner />}>
  <ProfileDetails />
</Suspense>
```

---
