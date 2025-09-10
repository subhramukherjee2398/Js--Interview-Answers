# Data Types

## What are the different data types in JavaScript?

**Ans:**

JavaScript has 7 primitive data types:

-   **String**
-   **Number**
-   **BigInt**
-   **Boolean**
-   **Undefined**
-   **Symbol**
-   **Null**

Additionally, **Object** is a non-primitive data type that includes arrays, functions, and other objects.

## What is the difference between `null` and `undefined`?

**Ans:**

-   `null`: Represents the **intentional absence of any value** and is an assignment value.
-   `undefined`: Represents a variable that has been declared but has not been assigned a value.

## What is the `typeof` operator in JavaScript, and how does it work?

**Ans:**

The `typeof` operator returns the data type of a given value in string form.

```javascript
typeof 42; // "number"
typeof "hello"; // "string"
typeof true; // "boolean"
typeof undefined; // "undefined"
typeof null; // "object" (special case, a known bug)
```

## What are the primitive data types in JavaScript?

**Ans:**

Primitive types include **String**, **Number**, **BigInt**, **Boolean**, **Undefined**, **Symbol**, and **Null**.

## What is the difference between primitive and reference data types in JavaScript?

**Ans:**

-   **Primitive types** store single values directly in the variable and are immutable. They store data in stack memory and are called by value.
-   **Reference types** (like objects and arrays) store references to the memory location and are mutable. They store data in heap memory and are called by reference.

## What is `NaN` in JavaScript, and how do you check if a value is `NaN`?

**Ans:**

`NaN` stands for "Not-a-Number." It represents a value that isn’t a legal number.

-   Use `isNaN(value)` or `Number.isNaN(value)` for a stricter check.

## What is the difference between `==` and `===` operators in JavaScript?

**Ans:**

-   `==`: Loose equality that performs **type coercion**.
-   `===`: Strict equality that checks both value and type **without coercion**.

## What does type coercion mean in JavaScript?

**Ans:**

In JavaScript, type coercion means converting a value from one data type to another automatically or implicitly when an operation is performed.

## How does JavaScript handle type coercion?

**Ans:**

Here are some type coercion examples in JavaScript:

### 1. String Coercion

-   **Using the `+` operator**:
    -   When adding a string to a number:

        ```javascript
        console.log('5' + 2);   // '52'
        console.log(2 + '5');   // '25'
        ```

-   **Using `String()`**:
    -   The `String` function converts a value to a string:

        ```javascript
        console.log(String(123)); // '123'
        console.log(String(true)); // 'true'
        ```

### 2. Number Coercion

-   **Using the `-`, `*`, or `/` operators**:
    -   When using arithmetic operators:

        ```javascript
        console.log('5' - 2);   // 3
        console.log('5' * 2);   // 10
        console.log('10' / '2'); // 5
        ```

-   **Using `Number()`**:
    -   The `Number` function converts a value to a number:

        ```javascript
        console.log(Number('123')); // 123
        console.log(Number(''));     // 0
        console.log(Number('abc'));  // NaN
        ```

### 3. Boolean Coercion

-   **Falsy Values**: Values that are considered false in a boolean context:

    ```javascript
    console.log(Boolean(0));          // false
    console.log(Boolean(""));         // false
    console.log(Boolean(null));       // false
    console.log(Boolean(undefined));  // false
    console.log(Boolean(NaN));        // false
    console.log(Boolean(false));      // false
    ```

-   **Truthy Values**: All other values are considered true:

    ```javascript
    console.log(Boolean(1));          // true
    console.log(Boolean("Hello"));    // true
    console.log(Boolean([]));         // true
    console.log(Boolean({}));         // true
    ```

### 4. Comparison Operators

-   **Using `==` (loose equality)**:

    ```javascript
    console.log(5 == '5');             // true
    console.log(null == undefined);     // true
    console.log(0 == false);            // true
    console.log('' == false);           // true
    ```

-   **Using `===` (strict equality)**:

    ```javascript
    console.log(5 === '5');            // false
    console.log(null === undefined);    // false
    console.log(0 === false);           // false
    console.log('' === false);          // false
    ```

### 5. Implicit Type Coercion in Conditionals

-   **Using conditionals**:

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

**Ans:**

Functions are first-class objects, meaning they can be assigned to variables, passed as arguments, and returned from other functions.

## How do you handle immutability in JavaScript with respect to primitive data types?

**Ans:**

Primitive data types are immutable. Once created, their values cannot be altered.

## What are Symbols in JavaScript, and why would you use them?

**Ans:**

Symbols are unique and immutable values used as property keys, often for adding properties without affecting existing code.

## What are typed arrays in JavaScript, and when would you use them?

**Ans:**

Typed arrays are array-like objects for handling binary data in memory-efficient ways, useful in WebGL and other binary-heavy applications.

## How does JavaScript's garbage collection work in relation to reference data types?

**Ans:**

JavaScript uses a mark-and-sweep algorithm. Objects not referenced are marked for garbage collection.

## What are WeakMap and WeakSet in JavaScript?

**Ans:**

-   **WeakMap** and **WeakSet** allow garbage collection of items with no other references. They are useful for caching or managing objects without preventing garbage collection.

# JavaScript Garbage Collection & Mark-and-Sweep Algorithm

## 🔹 JavaScript Garbage Collection
JavaScript has **automatic garbage collection**, meaning developers don’t need to manually free memory.

- **Primitive types** (number, string, boolean, null, undefined, symbol, bigint)  
  → Stored on the **stack** and cleared automatically when out of scope.

- **Reference types** (objects, arrays, functions, etc.)  
  → Stored on the **heap** and managed by the **garbage collector** using the **mark-and-sweep algorithm**.

---

## 🔹 Mark-and-Sweep Algorithm

### Steps:
1. **Roots Identification**
   - Roots are objects directly accessible (e.g., global objects like `window` or `global`, variables in scope, call stack).

2. **Mark Phase**
   - The GC starts from the roots.
   - Every object reachable via references is *marked* as alive.

3. **Sweep Phase**
   - Objects **not marked as reachable** are considered garbage.
   - These objects are “swept” and memory is freed.

---

## 🔹 Example

```javascript
function test() {
  let a = { name: "subhra" }; 
  let b = { hobby: "coding" };

  a.ref = b; // a → b
  b.ref = a; // b → a (circular reference)
}

test();

// After test() finishes, both a and b go out of scope.
// Even though a ↔ b reference each other, they are not reachable from roots, so both will be collected.
// This shows why mark-and-sweep is powerful: it handles circular references safely.
```

## What is `BigInt`, and how is it different from `Number` in JavaScript?

**Ans:**

**BigInt** supports integers larger than `Number.MAX_SAFE_INTEGER`, useful for precision in calculations with large numbers.

## What are Proxies in JavaScript, and how do they relate to data types?

**Ans:**

Proxies allow intercepting and customizing operations on objects (e.g., property access). They can be used for validation, logging, etc.

## How do you handle serialization and deserialization of objects in JavaScript?

**Ans:**

Use `JSON.stringify()` for serialization and `JSON.parse()` for deserialization. For more complex objects, libraries like `serialize-javascript` are used.

## How does JavaScript's `instanceof` operator work, and when should you use it?

**Ans:**

`instanceof` checks if an object is derived from a certain constructor, useful for type-checking objects created with custom classes.

## What is the `toString()` method, and how can you use it to convert data types?

**Ans:**

`toString()` converts data to a string. For objects, use `Object.prototype.toString.call(value)` to get a more descriptive result.

## What is JSON, and how does it relate to JavaScript objects?

**Ans:**

JSON (JavaScript Object Notation) is a format for representing data structures and objects, used in data exchange.

## How do JavaScript closures interact with different data types?

**Ans:**

Closures can capture and retain access to primitive and reference values in their scope even after the function has completed.

## Code-Based Questions

### Write a function to check if a value is an array or not.

**Ans:**
```javascript
function isArray(value) {
  return Array.isArray(value);
}
```

### How would you merge two objects in JavaScript without mutating the original objects?

**Ans:**
```javascript
const obj1 = { a: 1 };
const obj2 = { b: 2 };
const merged = { ...obj1, ...obj2 };
```

### How can you convert an array-like object (like `arguments`) into an actual array?

**Ans:**
```javascript
const arrayFromArguments = Array.from(arguments);
```

### Write a function that deep clones an object.

**Ans:**
```javascript
function deepClone(obj) {
  return JSON.parse(JSON.stringify(obj));
}
```

### How would you implement a custom `typeof` function to accurately determine the type of any variable?

**Ans:**
```javascript
function getType(value) {
  return Object.prototype.toString.call(value).slice(8, -1).toLowerCase();
}
```

## Why do you think JavaScript treats `[] == ![]` as `true`?

**Ans:**

JavaScript converts `[]` to `0` and `![]` to `false`, resulting in `0 == 0`, which is `true`.

## How would you handle the precision issues with floating-point numbers in JavaScript?

**Ans:**

Use rounding techniques or libraries like `math.js` to handle floating-point precision.

## When would you use a `Symbol` as a property key over a string in an object?

**Ans:**

Use `Symbol` to create unique property keys that will not conflict with other properties, especially when adding properties to objects you don't own.