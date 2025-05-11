
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
