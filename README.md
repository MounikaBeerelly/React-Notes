# React-Notes

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

### 4.  Role of type attribute in `script` tag. What options can I use there ? 
 - The type attribute specifies the type of the script. 
 - The type attribute identifies the content between the 
    `script` tags. 
 - It has a default value which is  text/javascript. 
    - text/javascript - It is the basic standard of writing 
 JavaScript code inside the `script` tag. 
- text/ecmascript - This value indicates that the script is following ECMAScript standards. 
- module - This value tells the browser that the script is a module that can import or export other files inside. 
- text/babel - This value indicates that the script is a babel type and requires babel to transpile it. 
- text/typescript - As the name suggests, the script is 
 written in typescript.

### 5. Config driven UI ?
- Config driven UI is a technique that allows you to create user interfaces based on a configuration file such as JSON, or a typescript file that defines the layout and content of UI components. 
- This can be useful for creating dynamic and customizable UIs without hard coding them.

### 6. 