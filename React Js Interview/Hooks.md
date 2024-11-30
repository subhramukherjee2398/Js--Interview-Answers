## How useEffect satisfy Lifecycle methods?

Ans :

#### 1. **componentDidMount** (Runs once after initial render)

```js
useEffect(() => {
  // Code here runs once after the initial render
  console.log("Component mounted");

  // Example: Fetch data or start a subscription here
  fetchData();
}, []); // Empty dependency array means this runs only once
```

#### 2. **componentDidUpdate** (Runs after every render if dependencies change)

```js
useEffect(() => {
  console.log("Component updated");

  // Example: Run some code when `count` or `user` changes
}, [count, user]); // This effect runs whenever `count` or `user` changes
```

If you want the effect to run after every update, include `useEffect` without dependencies (though this is uncommon and can cause performance issues if used unnecessarily).

```js
useEffect(() => {
  console.log("Runs after every render");
});
```

#### 3. **componentWillUnmount** (Cleanup before component is removed)

```js
useEffect(() => {
  console.log("Setting up...");

  return () => {
    console.log("Cleaning up...");
    // Example: Clear a subscription or remove an event listener
    unsubscribe();
  };
}, []); // Empty dependency array ensures this cleanup only runs on unmount
```

#### Combining Lifecycle Methods

```js
useEffect(() => {
  console.log("Mount or update");

  return () => {
    console.log("Cleanup on unmount or before next effect");
  };
}, [dependency]); // Runs on mount, dependency change, and cleanup on unmount
```

### What are React Hooks, and why were they introduced?

React Hooks are functions that allow you to use state and other React features in functional components. They were introduced in React 16.8 to enable state management and side effects without converting components to class-based components. This promotes cleaner, more readable code and allows for reusable logic across components.

### Can you explain the difference between class components and functional components with Hooks?

Class components manage state and lifecycle methods through `this` and require more boilerplate code. Functional components with Hooks allow you to manage state and side effects using `useState` and `useEffect`, respectively, resulting in less code and improved readability. They also promote better composition of behavior through custom hooks.

### What are the rules of Hooks?

The two main rules are:

1. **Only call Hooks at the top level:** Don’t call Hooks inside loops, conditions, or nested functions to ensure the order of Hooks remains consistent across renders.

2. **Only call Hooks from React functions:** You can call Hooks from functional components or custom Hooks, but not from regular JavaScript functions.

### What is the purpose of the `useState` hook?

The `useState` hook is used to declare state variables in functional components. It returns an array with the current state value and a function to update that state.

### How does the `useEffect` hook work? Can you explain its dependency array?

The `useEffect` hook performs side effects in functional components, such as data fetching or subscribing to events. It takes a function as its first argument and an optional dependency array as its second argument. The effect runs after the component renders. The dependency array controls when the effect runs—if it’s empty, the effect runs once on mount; if it contains values, the effect runs whenever those values change.

### What is the purpose of the `useContext` hook?

The `useContext` hook allows functional components to subscribe to context changes, providing a way to access context values without manually passing props down the component tree. It simplifies state management for global data like themes or user information.

### How do you optimize performance in a component using Hooks?

To optimize performance, you can: - Use `React.memo` to prevent unnecessary re-renders. - Utilize `useCallback` to memoize functions that are passed as props. - Use `useMemo` to memoize expensive calculations. - Properly manage dependencies in `useEffect` to avoid running effects too often.

### Can you explain the difference between `useMemo` and `useCallback`?

 `useMemo` memoizes the result of a computation, returning a cached value unless its dependencies change:

`useCallback` memoizes a function definition, returning the same function instance unless its dependencies change:
       
The difference between `useMemo` and `useCallback` lies in their purpose:

1. **`useMemo`**: Used to memoize the **result** of a computation to avoid unnecessary recalculations.
2. **`useCallback`**: Used to memoize a **function** definition to avoid unnecessary re-creations.

---

### **`useMemo` Example**:
Memoize a computed value.

```javascript
import React, { useState, useMemo } from 'react';

const ExpensiveCalculation = ({ num }) => {
  const result = useMemo(() => {
    console.log("Expensive calculation running...");
    return num * 2;
  }, [num]); // Recalculates only when `num` changes.

  return <div>Result: {result}</div>;
};

export default function App() {
  const [count, setCount] = useState(0);
  const [num, setNum] = useState(5);

  return (
    <div>
      <button onClick={() => setCount(count + 1)}>Re-render</button>
      <button onClick={() => setNum(num + 1)}>Increase Num</button>
      <ExpensiveCalculation num={num} />
    </div>
  );
}
```

**Output**: The "Expensive calculation running..." log appears **only when `num` changes**, even if the component re-renders due to `count`.

---

### **`useCallback` Example**:
Memoize a function.

```javascript
import React, { useState, useCallback } from 'react';

const Button = React.memo(({ handleClick }) => {
  console.log("Button rendered");
  return <button onClick={handleClick}>Click Me</button>;
});

export default function App() {
  const [count, setCount] = useState(0);
  const [value, setValue] = useState(0);

  // Memoize the callback to prevent unnecessary re-creations.
  const incrementCount = useCallback(() => {
    setCount((prev) => prev + 1);
  }, []);

  return (
    <div>
      <button onClick={() => setValue(value + 1)}>Re-render</button>
      <Button handleClick={incrementCount} />
      <p>Count: {count}</p>
    </div>
  );
}
```

**Output**: The "Button rendered" log appears only once, even if `value` changes, because `incrementCount` is memoized and doesn't re-trigger re-renders.

---

### Summary:
- Use `useMemo` when you need to **memoize a computed value**.
- Use `useCallback` when you need to **memoize a function** to avoid passing a new reference to child components.

### What are custom hooks, and how do you create one?

Custom hooks are JavaScript functions that leverage existing hooks to encapsulate and reuse logic. They must start with the word "use". For example:

```jsx
function useFetch(url) {
  const [data, setData] = useState(null);
  useEffect(() => {
    fetch(url)
      .then((response) => response.json())
      .then(setData);
  }, [url]);
  return data;
}
```

### How does `useReducer` work, and when would you use it instead of `useState`?

`useReducer` is a hook that manages complex state logic with a reducer function, similar to Redux. It’s particularly useful when you have multiple state values that rely on each other or when the next state depends on the previous state. It can help keep state updates organized and predictable.

```jsx
import React, { useReducer } from 'react';

// Define the reducer function
const reducer = (state, action) => {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    case 'reset':
      return { count: 0 };
    default:
      throw new Error(`Unhandled action type: ${action.type}`);
  }
};

export default function Counter() {
  // Initialize state and dispatch
  const [state, dispatch] = useReducer(reducer, { count: 0 });

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'increment' })}>Increment</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>Decrement</button>
      <button onClick={() => dispatch({ type: 'reset' })}>Reset</button>
    </div>
  );
}

```

### How can you share logic between components using custom hooks?

Custom hooks encapsulate logic that can be reused across components. You can extract shared stateful logic into a custom hook and call it in any component. This promotes DRY principles and makes code more maintainable.

### What is the purpose of `useLayoutEffect`, and how does it differ from `useEffect`?

 `useLayoutEffect` is similar to `useEffect`, but it runs synchronously after all DOM mutations. This means it can be used for measuring layout and making changes before the browser paints. It’s generally used for operations that need to happen immediately after rendering but before the browser updates the screen.

### Can you explain how React’s built-in hooks work under the hood?

  React hooks leverage a series of linked lists to track the state and effects of each component during render. When a component renders, React maintains a list of Hooks in the order they are called, ensuring that their states and effects correspond to the correct component instance across re-renders.

### How would you implement a debounced input field using Hooks?

You can implement a debounced input field by using `useState` for the input value and `useEffect` to set a timeout:

```jsx
import React, { useState, useEffect } from "react";

function DebouncedInput() {
  const [inputValue, setInputValue] = useState("");
  const [debouncedValue, setDebouncedValue] = useState(inputValue);

  useEffect(() => {
    const handler = setTimeout(() => {
      setDebouncedValue(inputValue);
    }, 300);

    // Cleanup the timeout on component unmount or when inputValue changes
    return () => {
      clearTimeout(handler);
    };
  }, [inputValue]);

  return (
    <div>
      <input
        type="text"
        value={inputValue}
        onChange={(e) => setInputValue(e.target.value)}
        placeholder="Type here..."
      />
      <p>Debounced Value: {debouncedValue}</p>
    </div>
  );
}

export default DebouncedInput;

```

### Imagine you have a complex state in your component. How would you manage it using Hooks?

For complex state, I would use `useReducer` to manage the state in a predictable way. This approach allows handling various actions in a single function and keeps the state logic organized:

```javascript
    const initialState = { count: 0, name: "" };
    function reducer(state, action) {
      switch (action.type) {
        case "increment":
          return { ...state, count: state.count + 1 };
        case "setName":
          return { ...state, name: action.payload };
        default:
          return state;
      }
    }
    const [state, dispatch] = useReducer(reducer, initialState);
```

### How would you implement form handling with validation using Hooks?**

 I would manage the form state using `useState`, create a function to handle input changes, and validate the form on submission. Example:

```javascript
    const [formData, setFormData] = useState({ name: "", email: "" });
    const [errors, setErrors] = useState({});

    const handleChange = (e) => {
      setFormData({ ...formData, [e.target.name]: e.target.value });
    };

    const validate = () => {
      const newErrors = {};
      if (!formData.email.includes("@")) newErrors.email = "Invalid email";
      return newErrors;
    };

    const handleSubmit = (e) => {
      e.preventDefault();
      const validationErrors = validate();
      if (Object.keys(validationErrors).length > 0) {
        setErrors(validationErrors);
      } else {
        // Submit form
      }
    };
```

### How would you implement error boundaries with Hooks?

While error boundaries cannot be implemented directly with Hooks, you can create a class component that catches errors and use it to wrap functional components. Alternatively, you can handle errors in functional components using `useEffect` or custom hooks to log errors and provide fallback UI.

