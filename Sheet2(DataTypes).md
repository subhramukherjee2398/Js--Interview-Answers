# Data Types

<!--
## What is Data Type?

Ans : Data type is a classification of data that defines the kind of data and how it is stored in memory.

## What is the difference between primitive and reference data types?

Ans :

Primitive data types are the most basic data types in JavaScript. They are the building blocks of data and are used to represent simple values such as numbers, strings, and booleans.

Reference data types, on the other hand, are more complex data types that are used to store and manipulate larger amounts of data. They are typically implemented using pointers or references to memory locations.

## How Many Data types in JavaScript?

Ans : 1.Primitive data 2 .Non-Primitive data / Reference data Type

**Primitive data ( 7 types )** :

1.Number
2.String
3.Boolean
4.Undefined
5.Null
6.Symbol
7.BigInt

->They are called call by value.

->As they store in Stack memory.

->when we take the data, it is copied, so the changes are done on copied data.

**Non-Primitive data ( 3 types )** :

1.Object
2.Array
3.Function

-> They are called call by reference.

-> As they store in Heap memory.so they doesnot store the value instaed store the reference of the value.

-> Means whatever changes we are doing, we are doing in original value

Here are some potential interview questions on data types in JavaScript, ranging from basic to advanced: -->

## What are the different data types in JavaScript?

Ans : JavaScript has 7 primitive data types:

- **String**
- **Number**
- **BigInt**
- **Boolean**
- **Undefined**
- **Symbol**
- **Null**

- Additionally, **Object** is a non-primitive data type that includes arrays, functions, and other objects.

## What is the difference between `null` and `undefined`?

- `null`: Represents the **intentional absence of any value** and is an assignment value.
- `undefined`: Represents a variable that has been declared but has not been assigned a value.

## What is the `typeof` operator in JavaScript, and how does it work?

The `typeof` operator returns the data type of a given value in string form,

```js
typeof 42; // "number"
typeof "hello"; // "string"
typeof true; // "boolean"
typeof undefined; // "undefined"
typeof null; // "object" (special case, a known bug)
```

## What are the primitive data types in JavaScript?

Primitive types include **String**, **Number**, **BigInt**, **Boolean**, **Undefined**, **Symbol**, and **Null**.


## What is the difference between primitive and reference data types in JavaScript?

- **Primitive types** store single values directly in the variable and are immutable.Store  data into stack memory.They are called call by value.
- **Reference types** (like objects and arrays) store references to the memory location, and are mutable.Store data into heap memory.They are called call by reference.

## What is `NaN` in JavaScript, and how do you check if a value is `NaN`?

   `NaN` stands for "Not-a-Number." It represents a value that isn’t a legal number. 
   
   - Use `isNaN(value)` or `Number.isNaN(value)` for a stricter check.

## What is the difference between `==` and `===` operators in JavaScript?

   - `==`: Loose equality that performs **type coercion**.
   - `===`: Strict equality that checks both value and type **without coercion**.

## How does JavaScript handle type coercion?

   Here are the type coercion examples in JavaScript formatted within single backticks:

### 1. **String Coercion**
- **Using the `+` operator**:
  - When adding a string to a number:
  ```javascript
  console.log('5' + 2);   // '52'
  console.log(2 + '5');   // '25'
  ```

- **Using `String()`**:
  - The `String` function converts a value to a string:
  ```javascript
  console.log(String(123)); // '123'
  console.log(String(true)); // 'true'
  ```

### 2. **Number Coercion**
- **Using the `-`, `*`, or `/` operators**:
  - When using arithmetic operators:
  ```javascript
  console.log('5' - 2);   // 3
  console.log('5' * 2);   // 10
  console.log('10' / '2'); // 5
  ```

- **Using `Number()`**:
  - The `Number` function converts a value to a number:
  ```javascript
  console.log(Number('123')); // 123
  console.log(Number(''));     // 0
  console.log(Number('abc'));  // NaN
  ```

### 3. **Boolean Coercion**
- **Falsies**: Values that are considered false in a boolean context:
  ```javascript
  console.log(Boolean(0));          // false
  console.log(Boolean(""));         // false
  console.log(Boolean(null));       // false
  console.log(Boolean(undefined));  // false
  console.log(Boolean(NaN));        // false
  console.log(Boolean(false));      // false
  ```

- **Trues**: All other values are considered true:
  ```javascript
  console.log(Boolean(1));          // true
  console.log(Boolean("Hello"));    // true
  console.log(Boolean([]));         // true
  console.log(Boolean({}));         // true
  ```

### 4. **Comparison Operators**
- **Using `==` (loose equality)**:
  ```javascript
  console.log(5 == '5');             // true
  console.log(null == undefined);     // true
  console.log(0 == false);            // true
  console.log('' == false);           // true
  ```

- **Using `===` (strict equality)**:
  ```javascript
  console.log(5 === '5');            // false
  console.log(null === undefined);    // false
  console.log(0 === false);           // false
  console.log('' === false);          // false
  ```

### 5. **Function Invocation**
- **Calling a function without arguments**:
  ```javascript
  function add(a, b) {
      return a + b;
  }
  console.log(add(5)); // NaN
  ```

### 6. **Implicit Type Coercion in Conditionals**
- **Using conditionals**:
  ```javascript
  if ("hello") {
      console.log("This is true!"); // Executes
  }
  if (0) {
      console.log("This won't execute!"); // Does not execute
  }
  ```

These examples illustrate the various scenarios of type coercion in JavaScript.

## How does JavaScript treat functions as data types?

   Ans :  Functions are first-class objects, meaning they can be assigned to variables, passed as arguments, and returned from other functions.

## How do you handle immutability in JavaScript with respect to primitive data types?
  
Ans : Primitive data types are immutable. Once created, their values cannot be altered.

## What are Symbols in JavaScript, and why would you use them?

Ans :  Symbols are unique and immutable values used as property keys, often for adding properties without affecting existing code.






21. **What are typed arrays in JavaScript, and when would you use them?**
    Typed arrays are array-like objects for handling binary data in memory-efficient ways, useful in WebGL and other binary-heavy applications.

22. **How does JavaScript's garbage collection work in relation to reference data types?**
    JavaScript uses a mark-and-sweep algorithm. Objects not referenced are marked for garbage collection.

23. **What are WeakMap and WeakSet in JavaScript?**

    - **WeakMap** and **WeakSet** allow garbage collection of items with no other references. They are useful for caching or managing objects without preventing garbage collection.

24. **What is `BigInt`, and how is it different from `Number` in JavaScript?**
    **BigInt** supports integers larger than `Number.MAX_SAFE_INTEGER`, useful for precision in calculations with large numbers.

25. **What are Proxies in JavaScript, and how do they relate to data types?**
    Proxies allow intercepting and customizing operations on objects (e.g., property access). They can be used for validation, logging, etc.

26. **How do you handle serialization and deserialization of objects in JavaScript?**
    Use `JSON.stringify()` for serialization and `JSON.parse()` for deserialization. For more complex objects, libraries like `serialize-javascript` are used.

27. **How does JavaScript's `instanceof` operator work, and when should you use it?**
    `instanceof` checks if an object is derived from a certain constructor, useful for type-checking objects created with custom classes.

28. **What is the `toString()` method, and how can you use it to convert data types?**
    `toString()` converts data to a string. For objects, use `Object.prototype.toString.call(value)` to get a more descriptive result.

29. **What is JSON, and how does it relate to JavaScript objects?**
    JSON (JavaScript Object Notation) is a format for representing data structures and objects, used in data exchange.

30. **How do JavaScript closures interact with different data types?**
    Closures can capture and retain access to primitive and reference values in their scope even after the function has completed.

### Code-Based Questions

31. **Write a function to check if a value is an array or not.**

    ```javascript
    function isArray(value) {
      return Array.isArray(value);
    }
    ```

32. **How would you merge two objects in JavaScript without mutating the original objects?**

    ```javascript
    const obj1 = { a: 1 };
    const obj2 = { b: 2 };
    const merged = { ...obj1, ...obj2 };
    ```

33. **How can you convert an array-like object (like `arguments`) into an actual array?**

    ```javascript
    const arrayFromArguments = Array.from(arguments);
    ```

34. **Write a function that deep clones an object.**

    ```javascript
    function deepClone(obj) {
      return JSON.parse(JSON.stringify(obj));
    }
    ```

35. **How would you implement a custom `typeof` function to accurately determine the type of any variable?**
    ```javascript
    function getType(value) {
      return Object.prototype.toString.call(value).slice(8, -1).toLowerCase();
    }
    ```


36. **Why do you think JavaScript treats `[] == ![]` as `true`?**
    JavaScript converts `[]` to `0` and `![]` to `false`, resulting in `0 == 0`, which is `true`.


38. **How would you handle the precision issues with floating-point numbers in JavaScript?**
    Use rounding techniques or libraries like `math.js` to handle floating-point precision.

40. **When would you use a `Symbol` as a property key over a string in an object?**
    Use `Symbol`
