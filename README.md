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
 HTML Element (render) `