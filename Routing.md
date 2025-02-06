# Routing

1. ### Explain React Routing ?
-  Whenever we want to create routes, we have to create routing configuration. 
- `CreateBrowserRouter`  from  react-router-dom  is used  to create the routing configuration. 
- The configuration means an information that tells what will 
 happen on a specific route. 
- **Example :**

    ```
    const AppRouter = CreateBrowserRouter([
        {
            path: "/",
            element: <App />,
        },
        {
            path: "/about",
            element: <About />,
        },
    ]);
    ```
- But just creating the configuration is not enough. We will have to provide this configuration to render it on to the page. 
- To do that, we use  `RouterProvider`  which will provide  the routing configuration to the app. 
- **Example :**

    ```
    const root = ReactDOM.createRoute(
        document.getElementById("root")
        );
    root.render(<RouterProvider router={AppRouter} />)
    ```
- We also need a component which will be shown whenever a user tries to access an anonymous path. 
     ```
    const AppRouter = CreateBrowserRouter([
        {
            path: "/",
            element: <App />,
            errorElement: <Error />,
        },
        {
            path: "/about",
            element: <About />,
        },
    ]);
    ```
- React-router-dom also provides a hook i.e. `useRouteError` which gives all the information about the route error. 
- We can show this information to the user on UI. 

2. ### How to create Children Routes ?
    ```
    const AppRouter = CreateReactRouter([
        {
            path: "/",
            element: <App />,
            children: [
                {
                    path: "/",
                    element: [
                        {
                            path: "/",
                            element: <Body />,
                        },
                        {
                            path: "/about",
                            element: <About />,
                        },
                    ],
                },
            ],
        },
    ]);
    ```
- Now we have to show the respective component based on its path in the `<AppLayout />` component. 
- To help us to do that, react-router-dom provides an  outlet. 
- This outlet gets filled with children when the user tries to access a path and shows that component on the UI based on that path. 
    ```
    const App = () => {
        return(
            <div className="app">
                <Header />
                <Outlet />
            </div>
        );
    };
    ```
3. ### Types of Routing ?
-  Two types of routing 
    1.  Client side routing 
    2.  Server side routing 
- In client side routing, the app does not make any network calls while navigating from one page to another. Everything happens on the client side. 
- In the server side routing, when a user navigates to a path, the browser will reload, make a network call, get the page from the server, and then show it on the UI. 
- This is the benefit of single page applications. We have all the components on the client side. They just get interchanged based on the route. 

4. ### Dynamic routing ?
    ```
    const Approuter = CreateBrowserRouter([
        {
            path: "/restaurant/:resId",
            element: <Restaurants />,
        },
    ]);
    ```
- We can extract this  resId  using a hook i.e.,  useParams  from react-router-dom. 
- Example:  `const { resId } = useParams();`