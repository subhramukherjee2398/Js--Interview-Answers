## 1.What is synchronous and asynchronous code?

Ans :

In synchronous code, tasks are performed one at a time. Each task waits for the previous one to complete before starting.

If a task takes a long time to finish, it will block the subsequent code from running until it's done.

**Asynchronous Code**

In asynchronous code, tasks can start without waiting for the previous one to finish, allowing other operations to continue in the meantime.

It's especially useful for tasks that take time, like network requests or reading files, as it does not block the rest of the code from executing.

## 2 . What is Single threaded languge and Multi threaded language?

Ans :
**Single Threaded**

single-threaded language, there is only one thread of execution, meaning it can handle one task at a time.

JavaScript is typically a single-threaded language (in most environments like browsers). It uses an **event loop** to handle asynchronous operations without blocking the main thread.

**Multi Threaded**

In a multi-threaded language, multiple threads can run simultaneously, allowing it to handle multiple tasks at the same time.

## 3. What are callbacks, and how do they work in JavaScript?

Ans : callbacks are functions that are passed as arguments to other functions and are executed after some kind of event or operation has completed.

```
function fetchData(callback) {
  // Simulate a delay with setTimeout
  setTimeout(() => {
    const data = { name: 'John', age: 30 };
    callback(data); // Invoke the callback with the data
  }, 2000);
}

// Define the callback function
function handleData(data) {
  console.log('Data received:', data);
}

// Call fetchData with handleData as the callback
fetchData(handleData);

```

## 4 .What are Promises, and why were they introduced in JavaScript?

Ans : Promises in JavaScript are objects that represent the state completion (or failure) of an asynchronous operation and its resulting value.

It was introduced in Es6 to handle aysnchornous operation in more manageable, easire and cleaner way than using callbacks.

#### How Promises Work?

Pending: The initial state; the operation has not completed yet.
Fulfilled: The operation was completed successfully.
Rejected: The operation failed

A Promise is created with a constructor that takes a single function.
The executor function takes two parameters: resolve and reject

resolve(value): Marks the Promise as fulfilled and provides a value.
reject(error): Marks the Promise as rejected and provides an error.

Syntax :

```

const myPromise = new Promise((resolve, reject) => {
  const success = true;

  if (success) {
    resolve('Operation was successful!');
  } else {
    reject('Something went wrong.');
  }
});


myPromise
  .then((result) => {
    console.log(result); // Will run if the promise is resolved
  })
  .catch((error) => {
    console.error(error); // Will run if the promise is rejected
  });

```

#### .then()

The then() method is used to handle the fulfillment of the Promise.

```
myPromise.then(onFulfilled, onRejected);
```

#### .catch()

The catch() method is used to handle the rejection of the Promise.

```
myPromise.catch((error) => console.error(error));
```

It’s syntactic sugar for **_.then(null, onRejected)_**

#### .finally()

Executes a callback function once the Promise is settled (fulfilled or rejected).
Useful for cleanup tasks

```
myPromise.finally(() => {
  console.log('Operation complete!');
});

```

#### Why Promises Were Introduced?

1.Avoiding Callback Hell->romises provide a way to chain asynchronous operations without nesting callbacks

2.Error Handling-> Catch()

3.Control Flow -> asynchronous operations by enabling chaining .then()
oncurrency management with methods like Promise.all(), Promise.race(), etc.


#### Chaining Promises
```
// Example of promise chaining
fetchUserData()
  .then((user) => fetchUserPosts(user.id))
  .then((posts) => displayPosts(posts))
  .catch((error) => console.error('Error:', error));
```


### Promise.all()

Takes an array of Promises and resolves when all of them are fulfilled or rejects if any of them fail.
Useful for running asynchronous operations in parallel.

```
const promise1 = fetch('/api/data1');
const promise2 = fetch('/api/data2');

Promise.all([promise1, promise2])
  .then((results) => {
    console.log('All data fetched:', results);
  })
  .catch((error) => {
    console.error('Error fetching data:', error);
  });

```

### Promise.race()

Resolves or rejects as soon as the first Promise in the array settles (completes or fails).
Useful for timeout scenarios.

```
Promise.race([promise1, promise2])
  .then((result) => {
    console.log('First completed:', result);
  });
```

### Promise.allSettled()

Resolves when all Promises have settled, regardless of their status (fulfilled or rejected).
Useful when you want to know the result of all Promises, even if some fail.

```
Promise.allSettled([promise1, promise2])
  .then((results) => {
    console.log('All settled:', results);
  });

```
### Promise.any()

Resolves as soon as any of the Promises in the array fulfill, or rejects if all fail.
Useful for "first-success" scenarios.

```
Promise.any([promise1, promise2])
  .then((result) => {
    console.log('First fulfilled:', result);
  })
  .catch((error) => {
    console.error('All promises rejected:', error);
  });

```