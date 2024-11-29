
## What is React Router, and why is it used in React applications?**
   - React Router is a standard library for routing in React applications.
   - It enables navigation between different components, allowing for a single-page application (SPA) experience without reloading the page.
   -  It manages the browser's history and allows developers to define routes and link components to those routes.

## What are the primary components of React Router, and how do they differ?

  - **BrowserRouter**: Uses the HTML5 history API to keep UI in sync with the URL.

   - **HashRouter**: Uses the hash portion of the URL (window.location.hash) to keep UI in sync. It’s useful for static file hosting.

   - **Route**: Defines a route and renders the specified component when the path matches the current URL.

   - **Link**: Provides a declarative way to navigate to different routes, replacing the need for `<a>` tags.

   - **Switch** (or <Routes> in v6): renders the first child <Route> that matches the current location. This ensures that only one route is rendered at a time, preventing multiple components from being displayed simultaneously.

## How does Route work in React Router, and what role does the path prop play?
   - Defines a route and renders the specified component when the path matches the current URL.

   - path : Where we pass the URL

   - component : Where we pass the component

## Explain the difference between exact, strict, and sensitive props in a route?

   - **exact**: Ensures that the path must match exactly; if not specified, routes will match partially.

   - **strict**: When set to true, the route will match only if the trailing slash is present in the URL.

   
   A trailing slash at the end of a URL (e.g., https://example.com/ vs. https://example.com) 
   
   - **sensitive**: If true, the matching is case-sensitive; otherwise, it is case-insensitive.

## How does the <Link> component differ from an a tag in HTML?
   - <Link> is a React Router component that prevents full page reloads by managing the browser’s history internally. It updates the URL and the UI efficiently, 
   - while an ``<a>`` tag causes a full page reload and doesn't utilize React’s routing capabilities.

## What is the purpose of the useHistory, useLocation, useParams,useNavigate hooks?

  - **useHistory** : Provides access to the history instance, allowing for programmatic navigation (e.g., redirecting after form submission).

   - **useLocation**: Returns the current location object, which includes the pathname, search, and state, useful for determining the current URL.

   - **useParams**: Retrieves URL parameters defined in the route path, useful for accessing dynamic segments of the URL (e.g., /users/:id).

   - **useNavigate**: Navigate to a new location in the same way you navigate to a new location in a browser. It returns an object with a cancel method.


## How can you pass data or state to a route when using programmatic navigation?

Ans :  
**Using the state Parameter**
```jsx
import { useNavigate } from 'react-router-dom';

const MyComponent = () => {
  const navigate = useNavigate();

  const goToDetails = () => {
    navigate('/details', { state: { userId: 123, userName: 'Alice' } });
  };

  return <button onClick={goToDetails}>Go to Details</button>;
};

```
```jsx
import { useLocation } from 'react-router-dom';

const Details = () => {
  const location = useLocation();
  const { userId, userName } = location.state || {}; // Use default empty object to avoid errors

  return (
    <div>
      <h2>User ID: {userId}</h2>
      <p>User Name: {userName}</p>
    </div>
  );
};

```
**Using URL Query Parameters**

```jsx
import { useNavigate } from 'react-router-dom';

const MyComponent = () => {
  const navigate = useNavigate();

  const goToDetails = () => {
    navigate('/details?userId=123&userName=Alice');
  };

  return <button onClick={goToDetails}>Go to Details</button>;
};

```

```jsx
import { useLocation } from 'react-router-dom';

const Details = () => {
  const location = useLocation();
  const queryParams = new URLSearchParams(location.search);
  const userId = queryParams.get('userId');
  const userName = queryParams.get('userName');

  return (
    <div>
      <h2>User ID: {userId}</h2>
      <p>User Name: {userName}</p>
    </div>
  );
};

```

## How do nested routes work in React Router, and what are some scenarios where they are useful?

Ans : Nested routes allow components to render their own <Route> components inside a parent route. This is useful for applications with hierarchical structures (like a dashboard with multiple sections) where the layout can remain consistent while changing the content based on the nested route.


## What is the difference between URL parameters and query strings in React Router?

Ans : URL parameters are part of the route path (e.g., /users/1), while **query strings** are appended to the URL after a ? (e.g., /users?sort=name). Query strings can be accessed using the useLocation hook, where you can parse location.search.


## How does the outlet work in React Router v6?

Ans : The outlet component is used to **render child routes in a parent route**. It serves as a placeholder for where the nested route components will be displayed within the parent component.


## How do you handle a 404 error page in React Router?
   
Ans : You can define a route with a wildcard path (*) to catch all unmatched routes:
      
      <Route path="*" component={NotFound} />
      

## How would you implement route guards (protected routes) with React Router?

Ans : You can create a wrapper component that checks authentication before rendering a route:
