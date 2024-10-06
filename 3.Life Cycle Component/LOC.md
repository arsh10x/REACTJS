# React Component Lifecycle Methods

React components go through a lifecycle of events. Understanding these lifecycle methods is crucial for managing component behavior and optimizing performance. The lifecycle is divided into three main phases: Mounting, Updating, and Unmounting.

## 1. Mounting Phase

The Mounting phase occurs when a component is being added to the DOM.

### Methods in order of execution:

1. **constructor(props)**
   - Called when the component is initialized
   - Used to set up initial state and bind methods
   - Avoid side effects or subscriptions

   ```javascript
   constructor(props) {
     super(props);
     this.state = { count: 0 };
   }
   ```

2. **static getDerivedStateFromProps(props, state)**
   - Called right before rendering
   - Used to update state based on props
   - Returns an object to update state or null

   ```javascript
   static getDerivedStateFromProps(props, state) {
     if (props.count !== state.count) {
       return { count: props.count };
     }
     return null;
   }
   ```

3. **render()**
   - The only required method
   - Returns JSX to be rendered
   - Should be pure (no side effects)

   ```javascript
   render() {
     return <div>{this.state.count}</div>;
   }
   ```

4. **componentDidMount()**
   - Called after the component is mounted to the DOM
   - Good place for subscriptions or data fetching

   ```javascript
   componentDidMount() {
     document.title = `Count: ${this.state.count}`;
   }
   ```

## 2. Updating Phase

The Updating phase occurs when a component's state or props change.

### Methods in order of execution:

1. **static getDerivedStateFromProps(props, state)**
   - Same as in Mounting phase

2. **shouldComponentUpdate(nextProps, nextState)**
   - Determines if the component should re-render
   - Used for performance optimization

   ```javascript
   shouldComponentUpdate(nextProps, nextState) {
     return this.state.count !== nextState.count;
   }
   ```

3. **render()**
   - Same as in Mounting phase

4. **getSnapshotBeforeUpdate(prevProps, prevState)**
   - Called right before changes are committed to the DOM
   - Return value is passed to componentDidUpdate

   ```javascript
   getSnapshotBeforeUpdate(prevProps, prevState) {
     return { scrollPosition: window.scrollY };
   }
   ```

5. **componentDidUpdate(prevProps, prevState, snapshot)**
   - Called after the update is committed to the DOM
   - Good for DOM operations or network requests

   ```javascript
   componentDidUpdate(prevProps, prevState, snapshot) {
     if (this.state.count !== prevState.count) {
       document.title = `Count: ${this.state.count}`;
     }
     if (snapshot.scrollPosition) {
       window.scrollTo(0, snapshot.scrollPosition);
     }
   }
   ```

## 3. Unmounting Phase

The Unmounting phase occurs when a component is being removed from the DOM.

### Method:

1. **componentWillUnmount()**
   - Called immediately before the component is unmounted
   - Used for cleanup (cancelling network requests, removing subscriptions)

   ```javascript
   componentWillUnmount() {
     document.title = 'React App'; // Reset title
     clearInterval(this.intervalId); // Clear any intervals
   }
   ```

## Key Points for Interview:

1. Explain that understanding lifecycle methods helps in managing side effects, optimizing performance, and handling component state correctly.

2. Highlight that the `render()` method is the only required method and should be pure.

3. Mention that `componentDidMount()` is ideal for initial data fetching or setting up subscriptions.

4. Explain that `shouldComponentUpdate()` can be used for performance optimization by preventing unnecessary re-renders.

5. Point out that `componentWillUnmount()` is crucial for cleanup to prevent memory leaks.

6. Be prepared to discuss how these methods relate to the newer React features like Hooks (e.g., useEffect can replace several lifecycle methods in functional components).

7. Remember that some methods are considered legacy (e.g., componentWillMount, componentWillUpdate) and should be avoided in new code.

