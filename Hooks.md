# React Hooks
 
1. ### What are Hooks in React ?
- Hooks are normal Javascript utility functions, written by facebook developers.
- Never create a state variable using useState outside the 
 component (functional component). 
    - It is used to create a local state inside a functional component. 
- Never create a state variable inside if conditions since it will create inconsistency. 
- Never create state variables inside for loop and functions as well. 
- Always call the hooks inside and top of the functional component.
- React-router-dom also provides a hook i.e. `useRouteError` which gives all the information about the route error. 
- `useParams`
2. ### What is useState and useEffect Hook ?
 - **useState hook**: Superpowerful state variables in react
    - It maintains the state of the component.
    - Pass the default value to the variable in the useState hook.
    - Whenever the state variable updates, React re-renders the component.
    - `const [state, setState] = useState([])`;
    - Whenever the state variable changes, setState function triggers and updates the component.
    - Always call the useState hook inside and top of the functional component.
    - Never create useState hook inside the if-else condition and for loops. It will create inconsistency in the program.
- **useEffect hook**:
    - The useEffect() is used to handle the side effects such as fetching data and updating the DOM. 
    -  It’s a powerful and flexible tool for managing asynchronous operations, such as data fetching, API calls and more. 
    - This hook runs on every render but there is also a way of using a dependency array using which we can control the effect of rendering. 
    - It is used to mimic the lifecycle methods of class-based components. 
    - The motivation behind the introduction of useEffect is to eliminate the side effects of using class-based components. 
    - For example, tasks like updating the DOM, fetching data from API endpoints, setting up subscriptions or timers, etc can lead to unwanted side effects. 
    - You call useEffect with a callback function that contains the side effect logic. 
    - It is a normal function, it contains 2 arguments - callback function and dependency array.
    - `useEffect( () => { }, []);`
     - By default, this function runs after every render of the component. 
    - if no dependency array => useEffect is called every render.
    - if dependency array is empty, useEffect is called only initial render (just once).
    - If dependency array contains some state, useEffect is called everytime whenever the state changes.

3. ### what is a Custom Hook ?
- A hook is nothing but a  utility function  . 
- Hooks are reusable functions. 
- When you have component logic that needs to be used by multiple components, we can extract that logic to a custom hook. 
- A custom hook in React is a JavaScript function that allows you to extract and reuse logic involving stateful behavior and side effects from function components. 
- Custom hooks enable you to encapsulate common logic in a way that can be shared across multiple components, promoting code reuse and better organization. 

4. ###  Why use custom hooks ? 
- **1.Code Reusability:** Custom hooks allow you to reuse  stateful logic across different components without duplicating code. 
- **2.Cleaner Components:** By extracting complex logic into 
 custom hooks, you can keep your components smaller and 
 more focused on rendering. 
- **3.Separation of Concerns:** Custom hooks help separate  the logic from the UI, making your code easier to manage and 
understand. 

5. ### Why should we name our hook as “useOnlineStatus” ? 
- It is a naming convention for custom hooks which is followed by most of the companies. 
- A lot of companies use a linter which throws an error if the custom hooks are not named like this. 
- It is a good practice to use the word  `use`  while naming  the custom hook. 
- If someone else sees the code, they will get to know that this is not a normal function but a React hook.


