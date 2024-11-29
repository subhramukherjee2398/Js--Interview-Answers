## What is React?

ans ; React is an open-source front-end JavaScript library that is used for building user interfaces, especially for single-page applications

## Major featuers of React?

Ans : The major features of React are:

- It uses VirtualDOM instead of RealDOM considering that RealDOM manipulations are expensive.
- Supports server-side rendering.

- Follows Unidirectional data flow or data binding.
- Uses reusable/composable UI components to develop the view.

## How Unidirectional Data flow happen in React?

Ans : Unidirectional data flow is a technique in which data flows in only one direction, either from parent to child or from child to parent.

In other words, data in a parent component never directly modifies data in a child component, but only propagates changes from parent to child.

This means that the parent and child components do not need to have a direct reference to each other, and they can be located in different files or directories.

This makes it easier to manage and test the components, as well as reuse them in different parts of the application.

```jsx

// Parent Component
function Parent() {
  const [count, setCount] = React.useState(0);

  // Callback function to update the count
  const handleIncrement = () => setCount(count + 1);

  return (
    <div>
      <h1>Parent Count: {count}</h1>
      <Child count={count} onIncrement={handleIncrement} />
    </div>
  );
}

// Child Component
function Child({ count, onIncrement }) {
  return (
    <div>
      <h2>Child Count: {count}</h2>
      <button onClick={onIncrement}>Increment Count</button>
    </div>
  );
}

```

## What is JSX?

Ans : JSX is a XML-like syntax extension to ECMAScript (the acronym stands for JavaScript XML). Basically it just provides syntactic sugar for the React.createElement() function, giving us expressiveness of JavaScript along with HTML like template syntax.

## What is Synthetic Events in react?

Ans : The react event handling system is known as Synthetic Events.

React’s Synthetic Events provide a layer of abstraction that makes it easier and more efficient to handle user interactions in a cross-browser compatible way.

## What is meaning of cross-browser compatible way?

Ans : A cross-browser compatible way refers to writing code, designing layouts, and implementing functionality that works consistently across different web browsers, including Chrome, Firefox, Safari, Edge, and sometimes older versions of Internet Explorer. The goal is to ensure that all users have a similar experience, regardless of the browser they use.

## When to use a Class Component over a Function Component?

Ans : If the component needs state or lifecycle methods then use class component otherwise use function component. However, from React 16.8 with the addition of Hooks, you could use state , lifecycle methods and other features that were only available in class component right in your function component

## What is fragments?

Ans : It's a common pattern in React which is used for a component to return multiple elements. Fragments let you group a list of children without adding extra nodes to the DOM.

## Why fragments are better than container divs?

Ans :

- Fragments are more performant than using a container div because they don’t add extra nodes to the DOM.

- Some CSS mechanisms like Flexbox and CSS Grid have a special parent-child relationships, and adding divs in the middle makes it hard to keep the desired layout.

## Advantages of React?

Ans :

- Increases the application's performance with Virtual DOM.
- JSX makes code easy to read and write.
- It renders both on client and server side (SSR).
- Easy to integrate with frameworks (Angular, Backbone) since it is only a view library.
- Easy to write unit and integration tests with tools such as Jest.

## What are the limitations of React?

- React is just a view library, not a full framework.
- There is a learning curve for beginners who are new to web development.
- Integrating React into a traditional MVC framework requires some additional configuration.
- The code complexity increases with inline templating and JSX.
- Too many smaller components leading to over engineering or boilerplate.


## React Lifecycle?

Ans : https://www.w3schools.com/react/react_lifecycle.asp

## What is component in React?

Ans : In React, a component is a reusable, self-contained piece of the user interface (UI). Components are the building blocks of any React application, each representing a part of the UI with its own logic and structure.

## What is Pure Component?with example?

Ans : In React, a **Pure Component** is a type of component that only re-renders when its props or state change. 
#### Characteristics 

1. **Shallow Comparison**: Pure Components perform a shallow comparison of their props and state to determine whether to re-render. If the shallow comparison indicates that the values have not changed, the component will not re-render.

2. **Extends `React.PureComponent`**: To create a Pure Component, you can extend `React.PureComponent` instead of `React.Component`. This automatically implements the `shouldComponentUpdate` lifecycle method, performing the shallow comparison for you.**For The function Compomonet we can use React.memo**

3. **Performance Optimization**: Using Pure Components can improve performance in scenarios where a component receives the same props and state frequently, helping to avoid unnecessary rendering.


```jsx
import React, { useState } from 'react';

// Regular Functional Component
const RegularComponent = ({ name }) => {
  console.log('RegularComponent Rendered');
  return <div>Regular Component: {name}</div>;
};

// Pure Functional Component
const PureComponentExample = React.memo(({ name }) => {
  console.log('PureComponentExample Rendered');
  return <div>Pure Component: {name}</div>;
});

const App = () => {
  const [name, setName] = useState('Alice');
  const [counter, setCounter] = useState(0);

  // Method to update state
  const updateName = () => {
    setName('Alice'); // Same value
  };

  const incrementCounter = () => {
    setCounter((prevCounter) => prevCounter + 1);
  };

  return (
    <div>
      <h1>Pure Component Example</h1>
      <button onClick={updateName}>Update Name (Same Value)</button>
      <button onClick={incrementCounter}>Increment Counter</button>
      <RegularComponent name={name} />
      <PureComponentExample name={name} />
      <p>Counter: {counter}</p>
    </div>
  );
};

export default App;

```

## what is Shallow Comparison?

Ans : In JavaScript, shallow comparison checks can be done using === for primitive data types, but for objects and arrays, it just checks if they reference the same location in memory. Here’s how shallow comparison works:

```jsx
const a = 1;
const b = 1;
console.log(a === b); // true, since both are the number 1
```

```jsx
const obj1 = { name: "Alice" };
const obj2 = { name: "Alice" };
const obj3 = obj1;

console.log(obj1 === obj2); // false, different objects in memory
console.log(obj1 === obj3); // true, same reference
```