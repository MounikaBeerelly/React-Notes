# React-Notes

**Notes**
---------
-  In class-based components, whenever a component loads, a constructor is called and then the render() method is called.
- It is suggested to use Context in small and mid-size applications. In the large-scale applications, we can make use of  Redux.

### 1. How to make our application compatible with older browsers/specific browsers ?
 - To make our application compatible with older/specific browsers, we can make use of  browserslist. 
 - In the package.json file, we can create a list and give it name as browserslist  and specify all the browsers/specific  versions in the list. 
 - Browserslist is a package stored in node modules and parcel uses that to make the app compatible. 
 - Refer to  `https://browserslist.dev`

    ```
    "browserslist": {
    "production": [
        ">0.2%",
        "not dead",
        "not op_mini all"
    ],
    "development": [
        "last 1 chrome version",
        "last 1 firefox version",
        "last 1 safari version"
    ]
    }
    ```
 - The production list will be used when creating a production build by running the build script, and the development list will be used when running the start script
 - **0.2%:** All browsers that have at least 0,2% of global market share
 - **not dead:** Exclude browsers without official support in the last 24 months
 - **not ie <= 11:** Exclude IE 11 and older versions
 - **not op_mini all:** Exclude Opera Mini

### 2. What is Babel ?
- Babel is a Opensource JavaScript compiler/transpiler.
- Converts JSX code into react code (browser understandable language).
- Babel converts JSX into React.creteElement.
- ` JSX -> React.createElement -> ReactElement - JS Object -> 
 HTML Element (render)`

 ### 3. Creating Functional Components 
 - While creating a functional component, the first letter of the name of the component must be in uppercase. Otherwise React will throw an error. 
 - A React component is a normal JavaScript function which returns a JSX/React element. 
 - Example: 
    ```
    const Funcomponent = () => {
        return <h1>Functional Component </h1> ;
    }
    ```

### 4.  Role of type attribute in `<script>` tag. What options can I use there ? 
 - The type attribute specifies the type of the script. 
 - The type attribute identifies the content between the 
    `<script>` tags. 
 - It has a default value which is  text/javascript. 
    - text/javascript - It is the basic standard of writing 
 JavaScript code inside the `<script>` tag. 
- text/ecmascript - This value indicates that the script is following ECMAScript standards. 
- module - This value tells the browser that the script is a module that can import or export other files inside. 
- text/babel - This value indicates that the script is a babel type and requires babel to transpile it. 
- text/typescript - As the name suggests, the script is 
 written in typescript.

### 5. Config driven UI ?
- Config driven UI is a technique that allows you to create user interfaces based on a configuration file such as JSON, or a typescript file that defines the layout and content of UI components. 
- This can be useful for creating dynamic and customizable UIs without hard coding them.

### 6. Fetching data from an API ?
- There are two approaches. 
- First Approach 
    - `Page Loads -> Make API call -> Render UI` 
    - In this approach, as soon as the page loads, we will 
 make an API call. 
    - As soon as we get the API response, we will populate 
 the data and render the UI. 
- Second Approach 
    - Page Loads -> Render UI -> Make API call -> Render 
    - In this approach, as soon as the page loads, we will 
 render the skeleton of the UI.
    - Then we will make an API call. 
    - Once we get the API response, then we will populate 
 the data and render the UI. 
    - In React, we are always going to follow the second 
 approach.
- The fetch() global function 
    - The global fetch() method starts the process of fetching a resource from the network, returning a promise that is fulfilled once the response is available. 
    - The promise resolves to a response object representing response to your request. 
    - A fetch() promise only rejects when the API fails.
    
    ```
    const fetchData = async () => {
        const response = await fetch(API);
        const data = await response.json();
        console.log(data);
    };
    ```
### 7. What is Shimmer UI ?
  When the page loads and the data is being fetched, until the data is displayed on the UI, instead of showing a spinner, we can show the skeleton of the UI. 

### 8. What is optional chaining ? 
  It is a feature that simplifies the process of accessing properties and methods of nested objects or arrays when intermediate properties may be null or undefined. 

### 9. What is Modularity ?
  Breakingdown the code into small modules is nothing but Modularity.

### 10. Bundling ?
- When we are building a large-scaled application, it is important to break it down into different components (Bundles). 
- Having a single bundle will make our app slower since a single bundle will contain all the code of the application which takes a lot of time to load. 
- The solution for this is to split our app into smaller chunks (bundles). 
- This process is known as below terms: 
    - Chunking 
    - Code Splitting 
    - Dynamic Bundling 
    - Lazy Loading 
    - On demand loading 
- For example, 
    - If we are developing an e-commerce application. This ecommerce app will have a cart which will contain different functionalities. So we can create a separate bundle for the Cart component. 
    - This bundle will not be loaded initially. It will be loaded only when the user visits the cart page. 
    - That means, with this approach the app will have 2 bundles. 
        - One would be a normal bundle which contains all the code of the app except for the cart component. This bundle will be loaded when the user visits our app. 
        - The other bundle will contain the code of the cart component which will be loaded only when the user visits the shopping cart. 
 - That is why this process is also known as  on demand  loading.