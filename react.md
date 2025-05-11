
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
• Context API is built feature of react
• Provides a way to share data globally across components without prop drilling
• Its primarily designed for prop-drilling(passing data down to deeply nested
components) and suitable for a small to medium size application
Example:- Theme switching – dark to light
Redux
Redux allows for centralized state management with actions and reducers
Redux suitable for medium to large scall application
Middleware support: Redux allows to use middleware to handle async operations like API
calls and other side effects
Redux has a powerful developer tool for debugging and logging of actions
