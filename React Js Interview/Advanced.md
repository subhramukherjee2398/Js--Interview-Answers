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


## What is an Error Boundary?

- Error Boundary helps us to handle such errors & display a fallback UI instead of breaking the UI or showing white screen.


- There’s a npm package called react-error-boundary which is a wrapper on top of the traditional Error Boundary component.

```jsx
import React from 'react';
import { ErrorBoundary } from "react-error-boundary";

const App = () => {
return <ErrorBoundary fallback={<div>Something went wrong</div>}>
/* rest of your component */
</ErrorBoundary>
}
```

## What is React Portal?

Ans : 
- Portals are a way to render children into a DOM node that exists outside the DOM hierarchy of the parent component.
- Portals are useful for rendering elements that are not children of the main component, such as a modal dialog or a tooltip.
- Portals are implemented using ReactDOM.createPortal() and can be accessed using the ReactDOM.findDOMNode() method.






