# ✰ Array in Javascript

## What is Array?

Ans : Array is a data structure that is used to store multiple values in a single variable.

## How to create Array ?

Ans :

1.Literal or [] bracker :

```js
let arr = [1, 2, 3, 4];
```

2.new Array() Constructor :

```js // Creating an empty array
let arr1 = new Array();
console.log(arr1); // Output: []

// Creating an array with a specific length
let arr2 = new Array(4);
console.log(arr2); // Output: [ <4 empty items> ]

// Creating an array with elements
let arr3 = new Array(1, 2, 3, 4);
console.log(arr3); // Output: [1, 2, 3, 4]

```

3.Array.of()

```
let arr = Array.of(1, 2, 3, 4);
console.log(arr); // Output: [1, 2, 3, 4]

```

4.Array.from()

```
// Converting a string to an array
let arr = Array.from("hello");
console.log(arr); // Output: ['h', 'e', 'l', 'l', 'o']

// Converting a Set to an array
let set = new Set([1, 2, 3]);
let arrFromSet = Array.from(set);
console.log(arrFromSet); // Output: [1, 2, 3]

```

5.Array Spread Syntax (...)

```
let arr = [1, 2, 3];
let arr2 = [...arr, 4, 5, 6];
console.log(arr2); // Output: [1, 2, 3, 4, 5, 6]
```

6.Array.fill()

```
let arr = new Array(5).fill(0);
console.log(arr); // Output: [0, 0, 0, 0, 0]

```

7.Array.concat()

```
let arr1 = [1, 2];
let arr2 = [3, 4];
let combinedArr = arr1.concat(arr2);
console.log(combinedArr); // Output: [1, 2, 3, 4]

```

## What are Array Methods?

Ans : **Source** : https://www.w3schools.com/js/js_arrays.asp

## typeof(array)?

Ans : Array is an object.

## Difference between "const points = [40]" vs "const points = new Array(40) "?

Ans :

```
// Create an array with one element:
const points = [40];

// Create an array with 40 undefined elements:
const points = new Array(40);
```

## How to Recognize an Array?

Ans :

```
const fruits = ["Banana", "Orange", "Apple"];

1.Array.isArray(fruits);

2.(fruits instanceof Array);
```

## How to check if an Array is Empty?

Ans : 

```
let arr = [];
console.log(arr.length); // Output: 0

let arr = [1, 2, 3];
console.log(arr.length); // Output: 3

let arr = ["a", "b", "c"];
console.log(arr.length); // Output: 3

```

## Array?.toString() vs Array.join()?

Ans : join()=> addition you can specify the separator:

## What will output?

```
const fruits = ["Banana", "Orange", "Apple", "Mango"];
delete fruits[0];

```
Answer : undefined

## what is flat()?

ans : flat() method creates a new array with all sub-array elements concatenated into it at a depth equal to the depth of the sub-array.

```
const myArr = [[1,2],[3,4],[5,6]];
const newArr = myArr.flat();

//for last depth
const myArr = [[1,2],[3,4],[5,6]];
const newArr = myArr.flat(infinity);
```

## What is the difference between flat() and flatMap()?

Ans : flat() method creates a new array with all sub-array elements concatenated into it at a depth equal to the depth of the sub-array.

The flatMap() method first maps all elements of an array and then creates a new array by flattening the array.

## Explain splice() method?

Ans : The splice() method can be used to add new items to an array:
```
const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.splice(2, 0, "Lemon", "Kiwi");
```

```
The first parameter (2) defines the position where new elements should be added (spliced in).

The second parameter (0) defines how many elements should be removed.

The rest of the parameters ("Lemon" , "Kiwi") define the new elements to be added.
```

**Also Remove**

```
const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.splice(0, 1);

```

## Array toSpliced()?

Ans : ES2023 added the Array toSpliced() method as a safe way to splice an array without altering the original array.

The difference between the new toSpliced() method and the old splice() method is that the new method creates a new array, keeping the original array unchanged, while the old method altered the original array.

```
const months = ["Jan", "Feb", "Mar", "Apr"];
const spliced = months.toSpliced(0, 1);
```

## Exlain Slice() method?

Ans : The slice() method can be used to extract a portion of an array:

```
const fruits = ["Banana", "Orange", "Apple", "Mango"];
const sliced = fruits.slice(1, 3);


The first parameter (1) defines the starting index of the slice.

The second parameter (3) defines the ending index of the slice.
```

## slice() vs splice()  ?

Ans : 

1.slice() method extracts a portion of an array does not modify the original array.

2.splice() method modifies the original array.

3.slice() takes two parameters, start and end, while splice() takes three parameters, start, deleteCount, and items.

## indexOf() vs includes()?

Ans : Array.includes() allows to check for NaN values. Unlike Array.indexOf().

## What is Array toSorted() and toReversed()?

Ans : ES2023 added the toSorted() method as a safe way to sort an array without altering the original array.

The difference between toSorted() and sort() is that the first method creates a new array, keeping the original array unchanged, while the last method alters the original array.

```
const months = ["Jan", "Feb", "Mar", "Apr"];
const sorted = months.toSorted();
```
**toReversed** same as toSorted(), doesnot modify.


```
const months = ["Jan", "Feb", "Mar", "Apr"];
const reversed = months.toReversed();

```

## Array with() ?

The .with() method used in your example is part of the immutable array methods introduced in ECMAScript 2023 (ES14). It creates a new array by replacing the element at a given index with a new value, without modifying the original array.

```
const months = ["Januar", "Februar", "Mar", "April"];
const myMonths = months.with(2, "March");

console.log(myMonths); // ["Januar", "Februar", "March", "April"]
console.log(months);   // ["Januar", "Februar", "Mar", "April"]

```

## Array.from() vs Array() ?

Ans : Array.from() will convert the given value into array, Array() will create the array with given values

## How to convert Converting an Array to a String?

Ans : The JavaScript method toString() converts an array to a string of (comma separated) array values.

```
let arr = [1, 2, 3, 4];
console.log(arr.toString()); // Output: 1,2,3,4

```

## How to convert Converting a String to an Array?

Ans : The JavaScript method split() converts a string to an array of characters.

```
let str = "hello";
let arr = str.split("");
console.log(arr); // Output: ['h', 'e', 'l', 'l', 'o']

```

## How to convert Converting an Array to a Number?

Ans : The JavaScript method parseInt() converts an array to a number.

```
let arr = [1, 2, 3, 4];
let num = parseInt(arr);
console.log(num); // Output: 1234

```

## How to convert Converting a Number to an Array?

Ans :

### Convert a Number to an Array of Digits

You can convert a number into an array where each element is a digit of the number.

#### Method 1: Using .toString() and Array.from()

```
let num = 12345;
let arr = Array.from(String(num), Number);
console.log(arr); // Output: [1, 2, 3, 4, 5]

Explanation:
String(num) converts the number into a string.
Array.from() creates an array from the string.
The Number function converts each string element back to a number.
```

#### Method 2: Using .toString() and .split()

```
let num = 6789;
let arr = num.toString().split('').map(Number);
console.log(arr); // Output: [6, 7, 8, 9]

Explanation:
.toString() converts the number to a string.
.split('') splits the string into individual characters.
.map(Number) converts each character back into a number.
```

### Convert a Number to an Array with One Element

If you want to convert a number to an array where the number is the only element:

#### Using Array Literal Notation

```
let num = 123;
let arr = [num];
console.log(arr); // Output: [123]
```

#### Using Array.of()

```
let num = 456;
let arr = Array.of(num);
console.log(arr); // Output: [456]
```

### Convert a Range of Numbers to an Array

If you want to create an array of numbers within a certain range (e.g., from 1 to 10):

#### Using Array.from()

```
let start = 1;
let end = 10;
let arr = Array.from({ length: end - start + 1 }, (_, i) => start + i);
console.log(arr); // Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

Explanation:
Array.from() creates an array with the specified length.
The callback (start + i) generates the numbers in the range.
```

## How to convert Converting an Array to a Boolean?

Ans : The JavaScript method every() converts an array to a boolean.

```
let arr = [1, 2, 3, 4];
let bool = arr.every(Number.isInteger);
console.log(bool); // Output: true

Explanation:
Number.isInteger() checks if a number is an integer.
.every() checks if every element in the array satisfies the condition.
```
