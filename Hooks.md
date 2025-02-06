# React Hooks
 
1. ### What are Hooks in React ?
- Hooks are normal Javascript utility functions, written by facebook developers.
- Never create a state variable using useState outside the 
 component (functional component). 
    - It is used to create a local state inside a functional component. 
- Never create a state variable inside if conditions since it will create inconsistency. 
- Never create state variables inside for loop and functions as well. 
- Always call the hooks inside and top of the functional component.

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
