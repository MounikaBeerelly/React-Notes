# Testing

- **Note** - If we are using Jest version 28 or later with React Testing Library, jest-environment-jsdom now must be installed separately.
- `npm install -D jest-environment-jsdom` 
- We can also change the name of function  test() to it(). They both work the same way. it() is like an alias of test().
- Add the /coverage folder to .gitignore. This folder contains the data about how many files it has covered while testing. 
- Currently, we have to run the npm run test command again and again after creating test cases. To solve that issue, we can add a new command in the package.json file inside our scripts. 
    ```
    “watch-test”: “jest –watch” 
    ```
- And instead of using npm run test command, we can use npm run watch-test. 
- Whenever we are using  fetch() inside the test case, we should always wrap our render() inside act() function.

### Types of Testing ?
- Unit Testing 
- Integration Testing 
- End-to-End Testing (e2e testing) 
1. ### Unit Testing :
- Unit Testing is a fundamental aspect of software testing 
where individual components or functions of an application 
are tested in isolation. 
- This method ensures that each unit of the application performs as expected. 
- By focusing on small, manageable parts of the application, 
unit testing helps identify and fix bugs early in the 
development process, significantly improving code quality 
and reliability. 
- Unit tests are typically automated and written by 
 developers. 
2. ### Integration Testing :
- Integration testing is a software testing process where 
software components, modules, or units are tested to 
evaluate system compliance concerning functional requirements. 
- This testing phase is crucial to ensure seamless interactions among various units/components, their functionalities and how well they can operate as a single entity. 
3. ### End-to-End Testing :
- In e2e testing, the application is tested from the moment 
the user starts using the application to the moment user 
leaves the application. 
- In this testing, we test the complete flow of the application from beginning to the end. 

4. ###  React Testing Library (RTL) :
- React Testing Library builds on top of DOM Testing  Library by adding APIs for working with React components. 
- React Testing Library Jest uses behind the scenes. 
- Jest is a delightful JavaScript Testing Framework with a focus on simplicity. 
- It works with projects using: Babel, TypeScript, Node, React, Angular, Vue and more!

5. ### Setup testing in the application:
- Install React Testing Library 
    ```
    npm install -D @testing-library/react
    ```
- Install Jest 
    ```
    npm install -D jest
    ```
- We are using jest with Babel, hence we need to install some 
dependencies as well. 
    ```
    npm install –D babel-jest @babel/core @babel/preset-env
    ```
-  Once we install the dependencies, we have to configure babel as well. 
- Create `babel.config.js`  file and below code in it: 
    ```
    module.exports = {
        presets: [[
            "@babel/preset-env", {
                targets: {
                    node : "current"
                }
            }
        ]];
    }
    ```
- We are using parcel and parcel uses babel. So Parcel has its own configuration of babel already. 
- When we created babel.config.js, we were creating our own configuration of babel which conflicts with the existing configuration of babel. 
- The new configuration of babel will overwrite the existing configuration done by Parcel. To avoid this, we should refer to the official documentation of  `Parcel - Usage with other tools`. 
- As per the documentation, we have to create a file `.parcelrc` and below 
configuration: 
    ```
    {
    "extends": "@parcel/config-default",
    "transformers": {
        "*.{js,mjs,jsx,cjs,ts,tsx}": [
        "@parcel/transformer-js",
        "@parcel/transformer-react-refresh-wrap"
        ]
    }
    }
    ```
- The above configuration will disable default babel transpilation configured by Parcel. Now we can use our own config file for Babel. 
- Command to run test cases -  `npm run test` 
- Configure Jest 
- Initialize Jest - `npx jest –init` 
-  Install @babel/preset-react
    ```
    npm install -D @babel/preset-react
    ``` 
- Include `@babel/preset-react` inside babel config file.
    ```
    module.exports  = {
        presets: [
            ["@babel/preset-env", { targets: {node: "current" }}],
            [ "@babel/preset-react", {runtime: "automatic"}]
        ],
    }
    ```
- Install @testing-library/jest-dom 
    ```
    npm install -D @testing-library/jest-dom
    ```

6. ### Grouping of test cases 
- We can group all the test cases in a file using the  describe() function. 
- This function takes 2 arguments: 
    - Description 
    - An arrow function 
- Inside the arrow function, we can put all the test cases. 
- We can also create groups inside a group. To do that, we can put a describe function inside a describe function. 

7. ### Helper functions 
- **beforeAll()**- This function will be called before running all the test cases. 
- **afterAll()**- This function will be called after running all the test cases. 
- **beforeEach()**- This function will be called before running every single test case. 
- **afterEach()**- This function will be called after running every 
 single test case. 