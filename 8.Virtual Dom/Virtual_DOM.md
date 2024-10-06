## Virtual DOM
The Virtual DOM (VDOM) is a programming concept where an ideal, or "virtual," representation of a UI is kept in memory and synced with the "real" DOM by a library such as ReactDOM.

### Key Points:
- It's a lightweight copy of the actual DOM.
- React creates a tree of custom objects representing a part of the DOM.
- Manipulating the virtual DOM is much faster than manipulating the real DOM.

### Process:
1. React creates a virtual DOM when your app initializes.
2. When state changes occur, a new virtual DOM tree is created.
3. This new tree is compared with the previous one (diffing).
4. Only the differences are updated in the real DOM.