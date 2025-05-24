
# React

### How to handle states in react
There are several ways to handle states in react. Depending on the complexity of the
application and where the state is needed.
Local components state,
UseState
State for class components
Using this.state and this.setState

```jsx
import React, { Component } from 'react';
class Counter extends Component {
constructor(props) {
super(props);
this.state = { count: 0 };
}
increment = () => {
this.setState({ count: this.state.count + 1 });
};
decrement = () => {
this.setState({ count: this.state.count - 1 });
};
render() {
return (
<div>
<p>Count: {this.state.count}</p>
<button onClick={this.increment}>Increment</button>
<button onClick={this.decrement}>Decrement</button>
</div>
);
}
}
```

Global State
Context API
For more complex app, share multiple components, we can use context api. It allow to
pass through the component tree without manually passing props to each level.
Example:-
config
```jsx
import React, { useState, ReactNode } from "react";
const CountContext = React.createContext(undefined);
export const CountProvider = ({ children }) => {
const [count, setCount] = useState(0);
return (
<CountContext.Provider value={{ count, setCount }}>
{children}
</CountContext.Provider>
);
};
export const useCount = () => {
const context = React.useContext(CountContext);
if (!context) {
throw new Error("useCount must be used within a CountProvider");
}
return context;
```
Wrap component with providers

```jsx
import Sample from "./components/sample";
import "./App.css";
import { CountProvider } from "./context/countContext";
function App() {
return (
<CountProvider>
Hello
<Sample />
</CountProvider>
);
}
export default App;
```
Consume
```jsx
import { useCount } from "../context/countContext";
const Sample = () => {
const { count, setCount } = useCount();
return (
<div>
Count: {count}
<button onClick={() => setCount(count + 1)}>Increment</button>
<button onClick={() => setCount(count - 1)}>Decrement</button>
</div>
);
};
export default Sample;
```

#### Global state management
Redux
Redux allows for centralized state management with actions and reducers
Store/index.js
```jsx
import { createStore } from "redux";
import { countReducer } from "./reducers/counter";
const store = createStore(countReducer);
export default store;
```

Store/actions/counter.js

```jsx
export const increment = () => ({
type: "INCREMENT"
});
export const decrement = () => ({
type: "DECREMENT"
});
```
Store/reducers/counter.js
```jsx
export const countReducer = (state = 0, action) => {
switch (action.type) {
case "INCREMENT":
return state + 1;
case "DECREMENT":
return state - 1;
default:
return state;
}
};
```
App.jsx
```jsx
import { Provider } from "react-redux";
import store from "./store";
<Provider store={store}>
Hello
<Sample />
```
#### Redux toolkit
Redux toolkit simplifies redux’s complexities, including store setup, and middleware, while
promoting best practices.
store\slice\counterSlice.js
```jsx
import { createSlice } from "@reduxjs/toolkit";
const initialState = {
count: 0
};
const counterSlice = createSlice({
name: "counter",
initialState,
reducers: {
increment: (state) => {
state.count += 1;
},
decrement: (state) => {
state.count -= 1;
}
}
});
export const { increment, decrement } = counterSlice.actions;
export default counterSlice.reducer;
```
Store\index.js
```jsx
import { configureStore } from "@reduxjs/toolkit";
import counterSlice from "./slice/counterSlice";
const store = configureStore({
reducer: {
counter: counterSlice
}
});
```
### Difference between context api and redux, use cases?
Context API
* Context API is built feature of react
* Provides a way to share data globally across components without prop drilling
* Its primarily designed for prop-drilling(passing data down to deeply nested
components) and suitable for a small to medium size application

Example:- Theme switching – dark to light
Redux
Redux allows for centralized state management with actions and reducers
Redux suitable for medium to large scall application
Middleware support: Redux allows to use middleware to handle async operations like API
calls and other side effects
Redux has a powerful developer tool for debugging and logging of actions

### Error handling in react

* Error boundaries (For react component errors)
Error boundaries are react components that catch javascript errors anywhere in
their child component tree.
* Try/ Catch for synchronous code with components
We have synchronous code that may throw an error inside react component (eg:
calculations, function etc)
* Error handling in asynchronous operations (eg- API calls)
For asynchrnous operations like API calls or data fetching, errors are usally handled
using try...catch with async functions.
Async/ await allows easy handling of asynchronous code
* Global error handling (for unhandled errors)
Window.onerror for JS errors and window.onunhandledrejection for promise
rejections

### What is peer dependency?

A package is designed to work with another package, but doesn’t to install it directly
Collaboration without duplication
Avoid version conflicts
If you get a chance to setup a react application, what will be your approach
If you get a change to upgrade to react app to vite, how will approach

### What is broswerslist

Browserlist is a configuration file and tool used in the frontend development ecosystem to
specify browsers our project supports. Here we can define which browsers and version
want to target.
Autoprefixer for CSS
Babel(javscript) - babel will transple modern javascript (like ES6+) in to older versions
Package.json
```js
"browserslist": [
"last 2 versions",
"not dead",
"> 0.2%",
"not op_mini all"
]
```
### How you will do the code review
Use live review

### what is Virtual dom vs Reconciliation
The Virtual DOM is a lightweight, in-memory representation of the actual DOM used by
libraries like React to optimize UI updates. Reconciliation is the process where React
compares the current Virtual DOM with the previous one, identifies changes, and
efficiently updates the real DOM.

### Session storage vs Token based authentication
The main difference between the session and token authentication is that the
authentication details are stored on the server side in session authentication and on the
user side in token authentication. Token authentication is more secure than session
authentication because a token cannot be tampered with.


### How will you use Roles permissions in React
Define Roles and Permissions: A common approach is to create an object or
an array that maps roles to their corresponding permissions.
Classic inheritance vs Prototype inheritance

### React Life Cycle methods
![image](https://github.com/user-attachments/assets/f7e29072-ed00-493e-9ba5-4982b78f8eda)

#### componentDidMount:
This is called after a component has been inserted into the DOM. It's a great place to perform
initial setup tasks, like fetching data from an API or setting up event listeners.

#### componentDidUpdate
This is called after a component has re-rendered due to changes in its state or props. It's a great
place to handle side effects or perform additional actions based on those changes.

#### componentWillUnmount
This is called just before a component is removed from the DOM. It's a crucial place to perform
cleanup tasks, such as clearing timers, unsubscribing from events, or releasing resources to
prevent [memory leaks](https://en.wikipedia.org/wiki/Memory_leak#:~:text=In computer
science%2C a memory,longer needed is not released.).

#### shouldComponentUpdate
We use this lifecycle method to control whether a component should re-render when its state or
props change. It is particularly useful for optimizing performance by preventing unnecessary
renders.
We use this lifecycle method to control whether a component should re-render when its state or
props change. It is particularly useful for optimizing performance by preventing unnecessary
renders.

### Q. What is JSX? 
JSX (JavaScript XML) is a syntax extension for JavaScript used primarily with React. It allows you to write HTML-like code directly within JavaScript, making it easier to describe the structure of a UI.
Here’s a simple example:
```jsx
const element = <h1>Hello, world!</h1>;
```

### Q. What is the difference between an Element and a Component?
 **Element:**
      - A React **Element** is a plain JavaScript object that describes what you want to see on the UI. It represents a DOM node or a component at a specific point in time. 
      - Elements are immutable: once created, you cannot change their properties. Instead, you create new elements to reflect updates.
      - Elements can be nested within other elements through their `props`.
      - Creating an element is a fast, lightweight operation—it does **not** create any actual DOM nodes or render anything to the screen directly.
**Example (without JSX):**
        
```js
        const element = React.createElement("button", { id: "login-btn" }, "Login");
 ```

        **Equivalent JSX syntax:**
  ```jsx
        <button id="login-btn">Login</button>
  ```

        **The object returned by `React.createElement`:**
   ```js
        {
          type: 'button',
          props: {
            id: 'login-btn',
            children: 'Login'
          }
        }
   ```
Elements are then passed to the React DOM renderer (e.g., `ReactDOM.render()`), which translates them to actual DOM nodes.

---

 **Component:**
      - A **Component** is a function or class that returns an element (or a tree of elements) to describe part of the UI. Components can accept inputs (called **props**) and manage their own state (in case of class or function components with hooks).
      - Components allow you to split the UI into independent, reusable pieces, each isolated and composable.
      - You can define a component using a function or a class:

   **Example (Function Component with JSX):**
        ```jsx
        const Button = ({ handleLogin }) => (
          <button id="login-btn" onClick={handleLogin}>
            Login
          </button>
        );
        ```

   When JSX is compiled, it's transformed into a tree of `React.createElement` calls:

```jsx
      const Button = ({ handleLogin }) =>
          React.createElement(
            "button",
            { id: "login-btn", onClick: handleLogin },
            "Login"
          );
   ```

   **In summary:**
      - **Elements** are the smallest building blocks in React—objects that describe what you want to see.
      - **Components** are functions or classes that return elements and encapsulate logic, structure, and behavior for parts of your UI.

### Q. When to use a Class Component over a Function Component?

After the addition of Hooks(i.e. React 16.8 onwards) it is always recommended to use Function components over Class components in React. Because you could use state, lifecycle methods and other features that were only available in class component present in function component too.

But even there are two reasons to use Class components over Function components.

1. If you need a React functionality whose Function component equivalent is not present yet, like Error Boundaries.
2. In older versions, If the component needs _state or lifecycle methods_ then you need to use class component.


### Q. What are Pure Components?
Pure components are the components which render the same output for the same state and props. In function components, you can achieve these pure components through memoized React.memo() API wrapping around the component. This API prevents unnecessary re-renders by comparing the previous props and new props using shallow comparison. So it will be helpful for performance optimizations.

But at the same time, it won't compare the previous state with the current state because function component itself prevents the unnecessary rendering by default when you set the same state again.

The syntactic representation of memoized components looks like below,
```js
const MemoizedComponent = memo(SomeComponent, arePropsEqual?);
```
Below is the example of how child component(i.e., EmployeeProfile) prevents re-renders for the same props passed by parent component(i.e.,EmployeeRegForm).

### 13. What are synthetic events in React?

SyntheticEvent is a cross-browser wrapper around the browser's native event. Its API is same as the browser's native event, including stopPropagation() and preventDefault(), except the events work identically across all browsers. The native events can be accessed directly from synthetic events using nativeEvent attribute.

Let's take an example of BookStore title search component with the ability to get all native event properties
```jsx
function BookStore() {
  function handleTitleChange(e) {
    console.log("The new title is:", e.target.value);
    // 'e' represents synthetic event
    const nativeEvent = e.nativeEvent;
    console.log(nativeEvent);
    e.stopPropagation();
    e.preventDefault();
  }

  return <input name="title" onChange={handleTitleChange} />;
}
```
### 18	What is the difference between Shadow DOM and Virtual DOM?
The Shadow DOM is a browser technology designed primarily for scoping variables and CSS in web components. The Virtual DOM is a concept implemented by libraries in JavaScript on top of browser APIs.

### 19. What is React Fiber?
Fiber is the new reconciliation engine or reimplementation of core algorithm in React v16. The goal of React Fiber is to increase its suitability for areas like animation, layout, gestures, ability to pause, abort, or reuse work and assign priority to different types of updates; and new concurrency primitives.

### 21. What are controlled components?
A component that controls the input elements within the forms on subsequent user input is called Controlled Component, i.e, every state mutation will have an associated handler function. That means, the displayed data is always in sync with the state of the component.

The controlled components will be implemented using the below steps,

1. Initialize the state using useState hooks in function components or inside constructor for class components.
2. Set the value of the form element to the respective state variable.
3. Create an event handler to handle the user input changes through useState updater function or setState from class component.
4. Attach the above event handler to form elements change or click events
   
For example, the name input field updates the user name using handleChange event handler as below,

```jsx
import React, { useState } from "react";

function UserProfile() {
  const [username, setUsername] = useState("");

  const handleChange = (e) => {
    setUsername(e.target.value);
  };

  return (
    <form>
      <label>
        Name:
        <input type="text" value={username} onChange={handleChange} />
      </label>
    </form>
  );
}
```
### 22. What are uncontrolled components?
The Uncontrolled Components are the ones that store their own state internally, and you query the DOM using a ref to find its current value when you need it. This is a bit more like traditional HTML.

The uncontrolled components will be implemented using the below steps,

Create a ref using useRef react hook in function component or React.createRef() in class based component.
Attach this ref to the form element.
The form element value can be accessed directly through ref in event handlers or componentDidMount for class components
In the below UserProfile component, the username input is accessed using ref.
```jsx
import React, { useRef } from "react";

function UserProfile() {
  const usernameRef = useRef(null);

  const handleSubmit = (event) => {
    event.preventDefault();
    console.log("The submitted username is: " + usernameRef.current.value);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Username:
        <input type="text" ref={usernameRef} />
      </label>
      <button type="submit">Submit</button>
    </form>
  );
}
```
### 22. What is Lifting State Up in React?
When several components need to share the same changing data then it is recommended to lift the shared state up to their closest common ancestor. That means if two child components share the same data from its parent, then move the state to parent instead of maintaining local state in both of the child components.

### 25. What are Higher-Order Components?
A higher-order component (HOC) is a function that takes a component and returns a new component. Basically, it's a pattern that is derived from React's compositional nature.

We call them pure components because they can accept any dynamically provided child component but they won't modify or copy any behavior from their input components.
```jsx
const EnhancedComponent = higherOrderComponent(WrappedComponent);
```
### 28 What is reconciliation?
Reconciliation in React is the process by which React updates the browser’s DOM to match your component tree’s current state in the most efficient way possible. Internally, React keeps a Virtual DOM representation of what the UI “should” look like; when your component’s props or state change, React:


