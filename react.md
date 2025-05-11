
# React

### How to handle states in react
There are several ways to handle states in react. Depending on the complexity of the
application and where the state is needed.
Local components state,
UseState
State for class components
Using this.state and this.setState

```
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
```
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

```
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
```
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
```
import { createStore } from "redux";
import { countReducer } from "./reducers/counter";
const store = createStore(countReducer);
export default store;
```

Store/actions/counter.js

```
export const increment = () => ({
type: "INCREMENT"
});
export const decrement = () => ({
type: "DECREMENT"
});
```
Store/reducers/counter.js
```
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
```
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
```
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
```
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
```
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



