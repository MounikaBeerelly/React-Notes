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
|9 | [When and why do we need lazy loading ?](#when-and-why-do-we-need-lazy-loading)|
|10 | [When and why do we need Suspense ?](#when-and-why-do-we-need-suspense)|
|11 | [Higher Order Components ?](#higher-order-components)|

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

9. ### When and why do we need lazy loading ? 
- In simpler terms, lazy loading is a design pattern. 
- It allows you to load parts of your application on demand to reduce the initial load time. 
- For example, you can initially load the components and modules related to user login and registration. Then you can load the rest of the components based on user navigation. 
- Ultimately it improves both the use experience and application performance. 
- **Advantages of Lazy loading** 
    - Reduces the initial load time by reducing the bundle size. 
    - Reduces browser workload. 
    - Improves application performance in low-band width situations. 
    - Improves user experience at initial loading. 
    - Optimizes resource usage. 
 - **Disadvantages of lazy loading** 
    - Not suitable for small scale applications. 
    - Placeholder can slow down quick scrolling. 
    - Requires additional communication with the server to fetch resources. 
    - Can affect SEO and ranking. 
- Example:
    ```
    // without Lazy loading
    import About from './About';

    // with Lazy()
    const About = React.lazy(() => import ('/About'));
    ```
-  When we use lazy() on a component which fetches the API 
 response, React can give us an error i.e.  A component  suspended while responding to synchronous input  . 
- To avoid or handle this error, React offers a component i.e. Suspense. 

10. ###  When and why do we need Suspense ?  
- Suspense is a built-in React component which lets you temporarily render a fallback UI while its children are still loading. 
- If a component tries to retrieve the API response, while it does that, we can show a fallback UI to the user until we get the API response. 
- This fallback UI could be a shimmer UI as well. 
- We can just wrap the lazy loaded component inside the 
 <Suspense> component. 
     ```
     import React, {Suspense} from 'react';

         // without Lazy loading
    import About from './About';

        // with Lazy()
    const About = React.lazy(() => import ('/About'));

    <Suspense fallback= {<Loading />}>
        <About />
    </Suspense>
    ```
- This <Suspense> component has a property i.e.  fallback  which takes the component which must be rendered until we get the API response in this case. 
- Suspense is best used when you want to display a fallback while waiting for something to load. 
- The two main use cases for this are when you are waiting for data to be fetched from an API after the initial page load and when you are lazy loading other React components.

11. ###  Higher Order Components ? 
- Higher order component is a function that takes a component and returns a component. 
- It takes a component as an input, enhances that component, adds some features into it and returns the component. 
- Higher order components are pure functions because they do not change the existing behavior of the input component.  

12. ### What are Controlled and Uncontrolled Components ?
- **Uncontrolled Components** :
    - If a component is managing its own state and controlling the behavior on its own then the component will be known as Uncontrolled component. 
    - The parent component will have no power or control over 
    this component and hence it will be known as an uncontrolled component. 
    ```
    import React, { useState } from 'react';

    const ItemCard = () => {
        const [showHeading, setShowHeading] = useState(false);
        const handleClick = () => {
            setShowHeading(!showHeading);
        }

        return (
            <div>
                <button 
                    onClick={handleClick}>
                        Click
                </button>
                 {showHeading ? 
                    <h1>Hello</h1> 
                    : null
                 }
            </div>
        )
    }

    const ItemCardList = () => {
        return (
            <div>
                <ItemCard />
            </div>
        )
    }

    export default ItemcardList;
    ```
    - In the above example, the `<ItemCard />` component is a child component of the `<ItemCardList />` component. 
    - The `<ItemCard />` component has a state variable i.e. showHeading  which has a default value  false  . This  value gets changed when the button is clicked by the user. 
    - If the showHeading is true then the  Hello  message  will be shown, if it is false then the message will be hidden. 
    - Now this component manages its own state and behavior and it does not depend on its parent component. Hence it is referred to as an  uncontrolled component. 
- **Controlled Component**
    - If the state and behavior of a component is being managed by its parent component, then it is referred to as the controlled component. 
    ```
    import React, { useState } from 'react';

    const ItemCard = () => {

        return (
            <div>
                <button 
                    onClick={handleClick}>
                        Click
                </button>
                {props.showHeading ? 
                    <h1>Hello</h1> 
                    : null
                }
            </div>
        )
    }

    const ItemCardList = () => {
        return (
            <div>
                <ItemCard showHeading={true}/>
            </div>
        )
    }

    export default ItemcardList;
    ```
    - In the above example, the `<ItemCard />` component does not have any state variable to manage. 
    - Instead, the value of showHeading is being sent from the parent component `<ItemCardList />` and is being received by the `<ItemCard />` component via props. 
    - Since the `<ItemCardList />` component is now controlling the `<ItemCard />` component, the `<ItemCard />` is now referred to as the  Controlled Component.

13. ###  Lifting the state up ?
- In the above example, the <ItemCard /> component does not 
control its own state, instead it is controlled by its parent component `<ItemCardList />`. 
- But with the currently implemented code, we can not change the state by clicking the button because the parent component has no way to know about the user's interaction with the button. 
- To do that, we need to let the parent component know when the button is clicked so that it can change the value of the state variable i.e.  showHeading  . 
- This can be achieved by  lifting the state up  . 
- In the below example, we pass a function as a prop i.e.  onShow  to the child component i.e. `<ItemCard />` from the parent component i.e. `<ItemCardList />` which sets the value of the state variable showHeading. 
- In the child component, we use the  onShow  prop and  pass it as a function to the onClick event in the button element. 
- This will let the parent component know that the user has clicked the button. Then the value of the  showHeading  state  variable will be changed.
     ```
    import React, { useState } from 'react';

    const ItemCard = ({ onShow, showHeading }) => {

        return (
            <div>
                <button 
                    onClick={onShow}>
                        Click
                </button>
                {showHeading ? 
                    <h1>Hello</h1> 
                    : null
                }
            </div>
        )
    }

    const ItemCardList = () => {
        const [showHeading, setShowHeading] = useState(false);
        return (
            <div>
                <ItemCard 
                  showHeading={showHeading}
                  onShow= {
                    () => setShowHeading(!showHeading)
                  }
                />
            </div>
        )
    }

    export default ItemcardList;
    ```

14. ### What is Prop Drilling ?
- React has a one-way data stream. That means the data flows 
into one direction i.e. from parent component to child component. 
- Passing props is a great way to explicitly pipe data through your UI tree to the components that use it. 
- But passing props can become inconvenient when there is a huge tree of components which has a parent component having children cponents and these children components are also parents to their children components. 
- In this case, lifting the state up can lead to a situation called Prop Drilling.

15. ### What is React Context ?
- React context is a method to pass props from parent to child components, by storing the props in a store (similar in redux) and using these props from the store by child components without actually passing them manually at each level of the component tree. 
- Using Redux to interact with states from parent to child 
components is not only quite difficult to understand but also gives you more complex code. 
- Whenever you want a store to keep your states or variables in and use them elsewhere in your program, use  Context  . 
- Generally when we have two or more levels (height) in our 
component tree, it is viable to use a store instead of passing props and then lifting the state as this will create confusion and unnecessary lengthy code. 
- **Create and Provide Context** :
    ```
    import { createContext } from 'react';

    export const Cartcontext = createContext({
        items: [];,
    });
    ```
    - In the above code, a context is created using the  createContext which is imported from  react.
    - We have given a default value this i.e. an object which has a list named  items. 
    - We can pass any value to the context while creating it such as a string, number, list, object, etc. 
    - This context is now assigned to a variable named  CartContext which is being exported to use in other components. 
    ```
    import { createContext } from 'react';

    const App = () => {
        return (
            <CartContext.Provider>
                <Header />
                <Body />
            </CartContext.Provider>
        )
    }

    export default App;
    ```
    - In the above code, the CartContext is imported in the `<App />` component and is being used as a wrapper of the `<Header />` and `<Body />` component. 
    - This will make the context available to access for the application. 
    - createContext returns a context object. 
    - The context object itself does not hold any information. 
    - It represents which context other components read or provide. 
    - The context object has a few properties: 
        - ***SomeContext.Provider*** : lets you provide the context  value to components. 
        - ***SomeContext.Consumer*** : is an alternative and rarely  used way to read the context value. 
    - The above code will still throw an error because we also need to pass a default value to the Provider.
    ```
    const App = () => {
        return (
            <CartContext.Provider value= {{ items: [] }}>
                    <Header />
                    <Body />
            </CartContext.Provider>
        )
    }
    ```
- **Consuming the context** :

    ```
    import {useContext} from 'react';
    import { Cartcontext } from './store.js';

    const Header = () => {
        const cartCtx = useContext(CartContext);
        return (
            <h1>Hello</h1>
        )
    }
    ```
    - To consume the context, we make use of the  useContext  hook. 
    - useContext returns the  context value  for the context  you passed. 
    - To determine the context value, React searches the component tree and finds the closest context provider above for that particular context. 


