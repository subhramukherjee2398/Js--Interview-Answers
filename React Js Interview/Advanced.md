## What is HOC?

Ans : 
- HOC stands for Higher-Order Component in React
- HOC is a function that takes a component as an argument and returns a new component with added features or modifications.
- It is a design pattern used to enhance the functionality of a component by wrapping it in another component.

```jsx
import React, { useState } from 'react';

// HOC function
const withCounter = (WrappedComponent) => {
  return function WithCounter(props) {
    const [count, setCount] = useState(0);

    const increment = () => {
      setCount((prevCount) => prevCount + 1);
    };

    // Pass down the count and increment function as props
    return (
      <WrappedComponent 
        count={count} 
        increment={increment} 
        {...props} 
      />
    );
  };
};

// Example functional component
const DisplayCounter = ({ count, increment }) => {
  return (
    <div>
      <h1>Count: {count}</h1>
      <button onClick={increment}>Increment</button>
    </div>
  );
};

// Wrap the component with the HOC
const EnhancedDisplayCounter = withCounter(DisplayCounter);

// Usage in application
const App = () => {
  return (
    <div>
      <EnhancedDisplayCounter />
    </div>
  );
};

export default App;


```

## what are the inbuilt React HOC?

Ans : 1. Redux's connect HOC
2. React Router's withRouter HOC


