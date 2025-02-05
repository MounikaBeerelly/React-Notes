### Table of Contents

| No. | Questions |
| --- | --------- |
|1  | [What is JSX ?](#what-is-jsx) |
|2  | [What is Component Composition ?](#what-is-component-composition) |
|3  | [Reconciliation in React ?](#reconciliation-in-react)|


1. ### What is JSX ?
- JSX (JavaScript XML) is not HTML inside Javascript. Combination of HTML and JavaScript. 
- JSX is a syntax extension for JavaScript that lets you write HTML-like markup inside a JavaScript file. 
- JSX is HTML/XML like syntax (looks like HTML).
- We can build React applications without JSX. But JSX makes developers life easy.
- JSX transpiled into standard JavaScript objects before it reaches the JS engine.
- Write attributes in JSX as camelcase.
- Prevents the cross-site scripting.

2. ### What is Component Composition ?
    Use a component inside another component, then it is known as component composition.

3. ### Reconciliation in React ?
- In React, reconciliation is the process of efficiently updating the DOM when the state or props of a component change. It's a crucial part of React's performance optimization strategy.
- **How Reconciliation works**:
    - **Virtual DOM**: React maintains a lightweight copy of the actual DOM called the Virtual DOM. When a component's state or props change, React creates a new Virtual DOM tree representing the desired UI state.
    - **Diffing Algorithm**: React then compares the new Virtual DOM with the previous one to identify the differences. This process is called "diffing."
    - **Minimal Updates**: Based on the diffing results, React determines the minimal set of changes needed to update the real DOM to match the new Virtual DOM. This minimizes the number of DOM operations, which are typically expensive in terms of performance.
    - **Batching**: React batches multiple updates together to further optimize performance. Instead of updating the DOM immediately for each change, it groups them and performs them in a single operation.
- **Benefits of Reconciliation:**
    - **Improved Performance**: By updating only the necessary parts of the DOM, React avoids unnecessary re-renders and minimizes DOM manipulations, leading to faster UI updates.
    - **Consistent UI**: Reconciliation ensures that the UI stays in sync with the underlying data, preventing rendering errors and inconsistencies.
    - **Developer Productivity**: React's declarative approach, combined with reconciliation, allows developers to focus on describing what the UI should look like, rather than worrying about the low-level details of DOM manipulation.
- **Key Considerations:**
    - **Keys**: When working with lists of elements, assigning unique keys helps React identify which elements have been added, removed, or reordered, making the diffing process more efficient.
    - **Pure Components**: Using React.PureComponent or the memo function can help prevent unnecessary re-renders by shallowly comparing props and state.
    - **shouldComponentUpdate**: For advanced use cases, you can use the shouldComponentUpdate lifecycle method to manually control whether a component should re-render.
