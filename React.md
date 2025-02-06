### Table of Contents

| No. | Questions |
| --- | --------- |
|1  | [What is JSX ?](#what-is-jsx) |
|2  | [What is Component Composition ?](#what-is-component-composition) |
|3  | [Reconciliation in React ?](#reconciliation-in-react)|
|4  | [What is React Fiber ?](#what-is-react-fiber)|
|5 | [Why and when do we need keys in React ?](#why-and-when-do-we-need-keys-in-react)|
|6 | [Can we use indexes as keys in React ?](#can-we-use-indexes-as-keys-in-react)|
|7 | [How does componentDidMount get executed ?](#how-does-componentdidmount-get-executed) |
|8 | [What happens when there are multiple children components in the parent class component ?](#what-happens-when-there-are-multiple-children-components-in-the-parent-class-component)|

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

4. ### What is React Fiber ?
    React Fiber is a powerful tool for building responsive and renderable user interfaces in React applications. It introduces a new reconciliation algorithm that enables incremental rendering, allowing React to split rendering work into chunks and spread it out over multiple frames.

5. ### Why and when do we need keys in React ? 
 - Keys are unique identifier, which are used to identify the which item is inserted, deleted and updated in an array. 
 - Keys should be given to the elements inside the array to give the elements a stable identity. 

6. ### Can we use indexes as keys in React ? 
- It is not recommended to use indexes as keys in React if the order of the items may change. 
- This can negatively impact the performance and may cause issues with component state. 
- If you choose not to assign any explicit key to list items, then React will default to using indexes as keys. 

7. ###  How does componentDidMount get executed ? 
- First the constructor method of parent class gets executed. 
- Then the render method of the parent class gets executed. 
- The render method of the parent class encounters the child class component. So it goes to that component. 
- Then the constructor method of child class gets executed. 
- After that the render() method of the child class gets executed. 
- Then the componentDidMount() of the child class gets executed. 
- Then it goes to the parent class component and executes the 
- componentDidMount of the parent class component. 
- `Constructor (Parent) -> render (Parent) -> Constructor (Child) -> render (Child) -> componentDidMount (Child) -> componentDidMount(Parent)`

8. ###  What happens when there are multiple children components in the parent class component ? 
- Below is the order of execution. 
    - Constructor (Parent) 
    - Render (Parent) 
    - Constructor (Child 1) 
    - Render (Child 1) 
    - Constructor (Child 2) 
    - Render (Child 2) 
    - componentDidMount (Child 1) 
    - componentDidMount (Child 2) 
    -  componentDidMount (Parent) 
- There are 2 phases in the React lifecycle 
    - Render phase 
    - Commit phase 
- The constructor method and render method come under the 
 render phase  while componentDidMount comes under the  commit phase. 
- In the commit phase, React updates the DOM. 
- Since updating the DOM is an expensive task, React batches all the constructor methods and render methods of children components and once there is no more child component, then it 
performs the commit phase. 
- componentDidMount is used to make an API call inside it.


