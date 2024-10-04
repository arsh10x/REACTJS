# React Routing Concepts for Interview Preparation

## 1. React Router

React Router is a standard library for routing in React applications. It enables the creation of single-page applications with navigation without page refreshes.

### Key Features:
- Provides components like `BrowserRouter`, `Route`, and `Link`
- Uses component-based architecture for defining routes
- Supports nested routing
- Offers hooks like `useParams` and `useNavigate`

### Example:

```jsx
import { BrowserRouter, Routes, Route, Link } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Home</Link>
        <Link to="/about">About</Link>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}
```

## 2. Protected Routes and RBAC

Protected routes are crucial for implementing Role-Based Access Control (RBAC) in React applications.

### Implementation Steps:
1. Create a higher-order component or custom hook for auth checks
2. Wrap routes requiring specific permissions
3. Redirect unauthorized users or show error messages
4. Store user roles/permissions in app state (e.g., Redux, Context API)

### Example of a Protected Route Component:

```jsx
import { Navigate } from 'react-router-dom';

function ProtectedRoute({ children, requiredRole }) {
  const { user } = useAuth(); // Assume this hook provides user info

  if (!user) {
    return <Navigate to="/login" />;
  }

  if (user.role !== requiredRole) {
    return <Navigate to="/unauthorized" />;
  }

  return children;
}

// Usage
<Route 
  path="/admin" 
  element={
    <ProtectedRoute requiredRole="admin">
      <AdminDashboard />
    </ProtectedRoute>
  } 
/>
```

## 3. Query Parameters

Query parameters allow passing data to routes via the URL.

### Key Points:
- Appear after '?' in URL, formatted as key-value pairs
- Multiple params separated by '&'
- Accessed using `useSearchParams` hook in React Router
- Optional and don't affect route matching

### Example of Using Query Params:

```jsx
import { useSearchParams } from 'react-router-dom';

function ProductList() {
  const [searchParams, setSearchParams] = useSearchParams();
  const category = searchParams.get('category');
  const sortBy = searchParams.get('sortBy');

  // Use category and sortBy to filter and sort products

  return (
    <div>
      {/* Product list UI */}
      <button onClick={() => setSearchParams({ category: 'electronics', sortBy: 'price' })}>
        Filter Electronics & Sort by Price
      </button>
    </div>
  );
}

// This component could be accessed via a URL like:
// /products?category=electronics&sortBy=price
```

## Summary

- React Router provides the foundation for SPA navigation
- Protected routes implement RBAC for application security
- Query params enable flexible data passing through URLs
