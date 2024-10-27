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

##  What is the purpose of async and await in JavaScript?

Ans : The purpose of async and await in JavaScript is to simplify the handling of asynchronous operation and making asynchronous code **look and behave like synchronous code**.

#### async

1.The async keyword is used to declare an asynchronous function.

2.An async function always returns a Promise

3.Tf a function returns a value, it automatically wraps it in a resolved Promise.

4.If an error is thrown inside an async function, it will automatically return a rejected Promise.


#### await

1.The await keyword can only be used inside an async function.
2.It pauses the execution of the async function until the Promise is resolved or rejected.
3.If the Promise is resolved, it returns the resolved value.
If the Promise is rejected, it throws an error that can be caught with a try...catch block.


##### Why Use async and await?
Readability: Makes the code look synchronous, improving readability and reducing complexity.

Avoids Callback Hell: Unlike callbacks, which can lead to deep nesting, and Promises, which can require chaining, async/await provides a flat and linear structure.

Error Handling: With async/await, you can use standard try...catch blocks for error handling, making it clearer and more consistent.

Maintainability: Code that uses async/await is often easier to maintain because of its clear flow.

## 2 .How do you create a Promise, and what are the possible states of a Promise?
## 3. How does the then() method work with Promises?
## 4.What is the difference between .then() and .catch() in a Promise?
## 5.What is the role of finally() in a Promise?
## 6. why must it be used inside an async function?

Ans : JavaScript is single-threaded, which means it executes code line by line. If you could use await outside an async function, it would block the main thread, making other operations wait, which goes against the nature of JavaScript’s asynchronous model.
Inside an async function, the event loop can continue processing other tasks while the await waits for a Promise to settle, keeping the code non-blocking.

## 7 .What is a callback hell, and how can it be avoided?

Ans: Callback hell, also known as "pyramid of doom," is a situation in JavaScript (and other programming languages) that occurs when multiple nested callbacks make the code difficult to read, maintain, and debug.

```
asyncFunction1(param1, function(result1) {
  asyncFunction2(result1, function(result2) {
    asyncFunction3(result2, function(result3) {
      asyncFunction4(result3, function(result4) {
        console.log('Final result:', result4);
      });
    });
  });
});

```

 **To avoid callback hell**, use named functions, Promises, async/await, modularize code, and consider using libraries that help manage asynchronous flows. These approaches lead to cleaner, more maintainable, and more readable code, significantly reducing the complexity associated with nested callbacks.

## 8. What is a Promise chain, and how do you handle multiple asynchronous operations using it?
## 9.What is the difference between Promise.all() and Promise.race()?
## 10.How does Promise.allSettled() differ from Promise.all()?
## 11 .What happens if a Promise is rejected and there is no .catch() handler?
## 12.What is the Event Loop, and how does it work in JavaScript?
## 13. What is the difference between the Call Stack and the Event Queue? (explain event loop)
## 14.How does JavaScript's single-threaded nature handle asynchronous operations without blocking?
## 15.How can you handle errors in async/await?
## 16.What is the difference between microtasks and macrotasks in JavaScript?
## 17.What is the purpose of setTimeout and setInterval in JavaScript? How are they related to asynchronous code?
## 18.Explain the concept of "task queue" and "microtask queue." How does the Event Loop prioritize them?
## 19.How can you use Promise.resolve() and Promise.reject()?
Ans : Promise.resolve(value) is used to create a promise that is resolved with the given value. If the value is a promise, it will return that promise; if the value is not a promise, it will return a new promise that is resolved with that value.

```
const resolvedPromise = Promise.resolve('Hello, world!');
resolvedPromise.then((value) => {
  console.log(value); // Output: Hello, world!
});

```

```
const anotherPromise = new Promise((resolve) => {
  setTimeout(() => resolve('Resolved from another promise!'), 1000);
});

const resolvedPromise = Promise.resolve(anotherPromise);
resolvedPromise.then((value) => {
  console.log(value); // Output (after 1 second): Resolved from another promise!
});

```

## 20. 