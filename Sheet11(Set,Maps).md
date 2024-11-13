# ✰ Set , Map , WeakMap , WeakSet

## What are Maps and Sets in JavaScript, and how do they differ from arrays and objects?

- A `Map` is a collection of key-value pairs where any data type can be used as a key.
- A `Set` is a collection of unique values, useful when duplicate values are not needed.

## What are WeakMaps and WeakSets, and how do they differ from Maps and Sets?

- `WeakMap` and `WeakSet` store references weakly, allowing garbage collection of items if there are no other references to them.
- They do not prevent objects from being garbage-collected.

## How do you add, retrieve, update, and delete items in a Map?

Ans : Here's how you can perform basic operations with a `Map` in JavaScript:

############# 1. **Adding Items**

To add an item to a `Map`, you use the `.set()` method, which takes two arguments: the key and the value.

```javascript
const map = new Map();
map.set("key1", "value1");
map.set("key2", "value2");
```

########## 2. **Retrieving Items**

To retrieve an item from a `Map`, use the `.get()` method with the key as an argument. It returns the value associated with that key, or `undefined` if the key doesn’t exist.

```javascript
console.log(map.get("key1")); // Output: 'value1'
console.log(map.get("key3")); // Output: undefined (if 'key3' doesn't exist)
```

########## 3. **Updating Items**

To update an item in a `Map`, simply use `.set()` with an existing key. It will overwrite the previous value.

```javascript
map.set("key1", "newValue");
console.log(map.get("key1")); // Output: 'newValue'
```

########## 4. **Deleting Items**

To delete an item, use the `.delete()` method with the key. It returns `true` if the key was deleted and `false` if the key didn’t exist.

```javascript
map.delete("key1"); // Removes 'key1' from the map
console.log(map.get("key1")); // Output: undefined
```

########## 5. **Additional Methods**

- **Checking if a Key Exists**: Use `.has()` to check if a specific key exists in the `Map`.
  ```javascript
  console.log(map.has("key2")); // Output: true or false
  ```
- **Clearing All Items**: Use `.clear()` to remove all items from the `Map`.
  ```javascript
  map.clear();
  console.log(map.size); // Output: 0
  ```

`Map` provides efficient and flexible methods to handle data with unique keys, which can be useful in various JavaScript applications.

## How do you add, check, and delete values in a Set?

Ans : In JavaScript, `Set` provides efficient ways to work with unique values. Here's how you can add, check, and delete values in a `Set`:

######## 1. **Adding Values**

To add a value to a `Set`, use the `.add()` method. `Set` automatically ensures that each value is unique, so if a value already exists, it won’t add it again.

```javascript
const set = new Set();
set.add(1);
set.add(2);
set.add(2); // Won't be added again
console.log(set); // Output: Set { 1, 2 }

const set = new Set([1, 2, 3]);
const values = set.values();

for (let value of values) {
  console.log(value); // Output: 1, 2, 3
}
```

######## 2. **Checking for a Value**

To check if a value exists in a `Set`, use the `.has()` method. It returns `true` if the value is present, and `false` otherwise.

```javascript
console.log(set.has(1)); // Output: true
console.log(set.has(3)); // Output: false
```

######## 3. **Deleting Values**

To remove a value from a `Set`, use the `.delete()` method. It returns `true` if the value was deleted and `false` if the value didn’t exist.

```javascript
set.delete(1); // Removes the value 1 from the set
console.log(set.has(1)); // Output: false
```

######## 4. **Additional Methods**

- **Clearing All Values**: Use `.clear()` to remove all values from the `Set`.
  ```javascript
  set.clear();
  console.log(set.size); // Output: 0
  ```
- **Getting the Size of the Set**: Use `.size` to get the number of unique values in the `Set`.
  ```javascript
  console.log(set.size); // Output: the number of unique values
  ```

`Set` is ideal for managing collections of unique values, like removing duplicates from an array or tracking items without needing key-value pairs.

## How is a Set different from an Array in JavaScript?\*\*

Ans :

| Feature                 | `Set`                                                                        | `Array`                                                                       |
| ----------------------- | ---------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| **Uniqueness**          | Only unique values are allowed.                                              | Allows duplicate values.                                                      |
| **Order of Elements**   | Maintains insertion order but doesn’t support indexing.                      | Maintains insertion order and supports indexing.                              |
| **Accessing Elements**  | Use `.has()` to check if an element exists; no indexing.                     | Access via index (e.g., `array[0]`).                                          |
| **Adding Elements**     | `.add(value)`                                                                | `.push(value)`                                                                |
| **Removing Elements**   | `.delete(value)`                                                             | `.splice(index, 1)`                                                           |
| **Checking Existence**  | `.has(value)`                                                                | `.includes(value)`                                                            |
| **Removing Duplicates** | Automatically removes duplicates.                                            | Requires filtering to remove duplicates.                                      |
| **Performance**         | Faster lookups and deletions due to optimized structure.                     | Slower lookups and deletions, especially in large arrays.                     |
| **Use Case**            | Ideal for unique collections, removing duplicates, or fast existence checks. | Ideal for ordered collections, indexed access, or when duplicates are needed. |

## How is a Map different from an Object in JavaScript?

Ans :

| Feature                | `Map`                                                                                                  | `Object`                                                                                               |
| ---------------------- | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| **Key Types**          | Keys can be of any type: primitives, objects, or functions.                                            | Keys must be strings or symbols.                                                                       |
| **Order of Keys**      | Maintains insertion order for keys.                                                                    | Does not guarantee key order (though modern engines often keep insertion order for strings).           |
| **Default Properties** | Only includes properties you explicitly add.                                                           | Inherits prototype properties, which can lead to unexpected keys (unless using `Object.create(null)`). |
| **Key-Value Pairing**  | Stores values with their keys directly; optimized for fast retrieval.                                  | Uses string keys mapped to values; may need `hasOwnProperty` to avoid prototype properties.            |
| **Methods for Adding** | `.set(key, value)`                                                                                     | `object[key] = value` or `Object.assign()`.                                                            |
| **Checking Existence** | `.has(key)`                                                                                            | `key in object` or `object.hasOwnProperty(key)`.                                                       |
| **Deleting Entries**   | `.delete(key)`                                                                                         | `delete object[key]`.                                                                                  |
| **Size Property**      | `.size` provides the count of key-value pairs.                                                         | No direct size property; need `Object.keys(obj).length`.                                               |
| **Iterability**        | Can directly iterate over entries with `.entries()`, `.keys()`, or `.values()`.                        | Requires `for...in` or conversion (e.g., `Object.keys()`).                                             |
| **Performance**        | Generally more efficient for frequent addition and deletion of key-value pairs.                        | Generally slower for frequent additions and deletions, especially with large data.                     |
| **Use Cases**          | Ideal for managing dynamic key-value pairs, especially when key types vary or insertion order matters. | Good for simple, static key-value data, configurations, or when only string keys are needed.           |

## How can you convert a Set back to an Array?

   ```js
   Array.from(set); // or [...set];
   ```

## How would you find the union, intersection, and difference between two Sets?

Ans : You can perform union, intersection, and difference operations on two `Set` objects in JavaScript using methods like the spread operator, `filter`, and `Set` constructors. Here’s how to do each operation with examples:

###### 1. **Union of Two Sets**
The union of two sets includes all unique elements from both sets.

**Example:**

```javascript
const setA = new Set([1, 2, 3]);
const setB = new Set([3, 4, 5]);

const union = new Set([...setA, ...setB]);
console.log(union); // Output: Set { 1, 2, 3, 4, 5 }
```

###### 2. **Intersection of Two Sets**
The intersection of two sets includes only the elements that are present in both sets.

**Example:**

```javascript
const setA = new Set([1, 2, 3]);
const setB = new Set([3, 4, 5]);

const intersection = new Set([...setA].filter(x => setB.has(x)));
console.log(intersection); // Output: Set { 3 }
```

###### 3. **Difference of Two Sets**
The difference of two sets (in this case, `setA - setB`) includes elements that are in the first set but not in the second.

**Example:**

```javascript
const setA = new Set([1, 2, 3]);
const setB = new Set([3, 4, 5]);

const difference = new Set([...setA].filter(x => !setB.has(x)));
console.log(difference); // Output: Set { 1, 2 }
```


## What is a WeakMap, and why might you use it instead of a regular Map?

Ans : A `WeakMap` is a variation of `Map` in JavaScript that has some key differences designed to improve memory management, especially for handling objects as keys.

##### Key Features of `WeakMap`

1. **Only Object Keys**: In a `WeakMap`, keys must be objects (not primitives like strings or numbers). This is because `WeakMap` is optimized for object key storage, allowing certain memory management optimizations that wouldn’t apply to primitive values.

2. **Automatic Garbage Collection**: When an object used as a key in a `WeakMap` no longer has any other references, it is automatically eligible for garbage collection, even if it’s still a key in the `WeakMap`. This isn’t the case with a regular `Map`, where all keys are strongly referenced and will prevent garbage collection as long as they’re in the `Map`.

3. **No Iteration Methods**: `WeakMap` does not support methods to iterate over keys, values, or entries (`.keys()`, `.values()`, `.entries()`, or `.forEach()` methods are absent). This is to ensure that keys can be garbage-collected, as iteration would imply a need to hold references to all entries, preventing efficient memory cleanup.

4. **Limited API**: The API is simpler than `Map`, with only four methods:
   - `.set(key, value)`: Adds a key-value pair to the `WeakMap`.
   - `.get(key)`: Retrieves the value associated with the key.
   - `.delete(key)`: Removes the key-value pair associated with the key.
   - `.has(key)`: Checks if a specific key exists in the `WeakMap`.

##### Why Use `WeakMap` Instead of `Map`?

`WeakMap` is particularly useful when you want to associate data with an object but don’t want that association to prevent the object’s garbage collection if it’s no longer referenced elsewhere in the code. Here are common use cases:

- **Storing Metadata or Caching Results for DOM Elements**: If you need to store temporary data related to DOM elements (such as event handlers or cached values), a `WeakMap` ensures that when the DOM element is removed from the page, the memory used for associated data can be freed automatically.

    ```javascript
    const elementData = new WeakMap();
    const button = document.querySelector('button');

    // Associate some data with the button
    elementData.set(button, { clicked: 0 });

    // If `button` is removed from the DOM and no other references exist,
    // both `button` and its associated data in `elementData` are garbage collected.
    ```

- **Private Data for Objects**: You can use a `WeakMap` to store private data for objects, allowing the data to be garbage collected along with the object.

    ```javascript
    const privateData = new WeakMap();

    function MyClass(name) {
      privateData.set(this, { name });
    }

    MyClass.prototype.getName = function() {
      return privateData.get(this).name;
    };

    const instance = new MyClass('Alice');
    console.log(instance.getName()); // Output: 'Alice'
    ```

In summary, **use `WeakMap`** when you need to associate data with objects and want that data to be garbage collected when the object itself is no longer needed. This is especially useful for memory-efficient caching, managing temporary data tied to object lifetimes, and handling metadata for objects without risking memory leaks.


## What is a WeakSet, and how does it differ from a regular Set?

Ans : A `WeakSet` is a special type of `Set` in JavaScript with unique properties focused on memory management. Here’s what makes `WeakSet` distinct and when you might use it:

#### Key Features of `WeakSet`

1. **Only Object Values**: `WeakSet` can only contain objects as values (no primitive values like numbers, strings, or booleans). This is because `WeakSet` is optimized for object storage to leverage automatic garbage collection.

2. **Automatic Garbage Collection**: Like `WeakMap`, if there are no other references to an object stored in a `WeakSet`, it becomes eligible for garbage collection. This behavior helps manage memory by allowing unused objects to be automatically removed, which is not possible with a regular `Set`.

3. **No Iteration Methods**: `WeakSet` does not support methods like `.forEach()` or properties like `.size` because it doesn’t allow you to iterate over or directly inspect its contents. This restriction supports automatic garbage collection by avoiding persistent references to the stored objects.

4. **Limited API**: The `WeakSet` API is simpler than `Set`:
   - `.add(value)`: Adds an object to the `WeakSet`.
   - `.delete(value)`: Removes an object from the `WeakSet`.
   - `.has(value)`: Checks if a specific object is in the `WeakSet`.

#### How `WeakSet` Differs from `Set`

| Feature                 | `WeakSet`                                               | `Set`                                      |
|-------------------------|---------------------------------------------------------|--------------------------------------------|
| **Allowed Values**      | Only objects                                            | Any type (objects and primitives)          |
| **Garbage Collection**  | Automatically removes objects if there are no other references | No automatic removal; keeps strong references to all values |
| **Iteration**           | Not iterable, no `.forEach()` or `.size` property       | Iterable, supports `.forEach()`, `.size`, etc. |
| **Primary Use Case**    | Storing temporary object references without creating memory leaks | General collection of unique values, both primitive and object |

#### When to Use `WeakSet`

`WeakSet` is particularly useful when you need a collection of unique objects and want these objects to be garbage-collected if there are no other references to them. Here are common use cases:

- **Tracking DOM Elements Temporarily**: For example, to keep track of which elements have already been processed or event listeners have been attached to, without worrying about memory leaks when elements are removed from the DOM.

    ```javascript
    const processedElements = new WeakSet();
    const element = document.querySelector('#my-element');

    if (!processedElements.has(element)) {
        // Process the element and mark it as processed
        processedElements.add(element);
        // Perform processing
    }
    // When `element` is removed from DOM and dereferenced, it’s garbage collected.
    ```

- **Private Metadata for Objects**: `WeakSet` can be used to "tag" objects with metadata in a way that remains private and temporary.

#### Example Comparison of `Set` and `WeakSet`

```javascript
// Example of a regular Set
const set = new Set();
set.add(1);           // Works, allows primitive values
set.add({ foo: 1 });  // Works, allows object values
console.log(set.size); // Output: 2

// Example of a WeakSet
const weakSet = new WeakSet();
weakSet.add({ foo: 1 }); // Works, only allows objects
// weakSet.add(1);       // Error: Invalid value (only objects allowed)
```

In summary, **use `WeakSet`** when you need to track objects in a way that allows for efficient memory usage and automatic cleanup. It’s especially useful for handling temporary object collections without the risk of memory leaks.



