
# Coding Challenge : Javascript

## 1.How to define a class with properties and methods in JavaScript?


```js 
class Car {
  constructor(name,model){
     this.name = name
     this.model = model
  }

  start(){
    console.log("My car is ",this.name)
  }

}

 let Jeep = new Car("JEEP","JUV");

 Jeep.start()
```

## 2.How to implement class inheritance in JavaScript?

```js

class Parent {
    constructor(name){
        this.name = name
    }

    start(){
        console.log(this.name)
    }
 }

 class Child extends Parent{
    start(){
        super.start()
    }
 }

 let Enc = new Child("KJKJ");
 Enc.start()
```

## 3.How to find duplicate elements in a given array?

```js
let arr = [1,2,3,4,5,6,7,8,9,10,1,2,3,4,5,6,7,8,9,10]
```
```js
let duplicate = arr.filter(function(item, index, array){
    return array.indexOf(item) !== index;
});
console.log(duplicate)
```
## 4.How to find duplicate elements in a given array?

```js

let arr = [
  { id: 1, name: 'Alice' },
  { id: 2, name: 'Bob' },
  { id: 3, name: 'Charlie' },
  { id: 1, name: 'David' },
  { id: 2, name: 'Eve' }
];

```

```js
let duplicate = arr.filter(function(item, index, array){
    return array.findIndex(x => x.id === item.id && x.name === item.name) !== index;
});
console.log(duplicate)
```

## 5.Count Occurrences of a Character in a String

```js
let str = "hello world";
```

```js
function countOccurrencesWithReduce(str) {
  return str.split('').reduce((acc, char) => {
    acc[char] = (acc[char] || 0) + 1;
    return acc;
  }, {});
}

console.log(countOccurrencesWithReduce("hello world"));
// Output: { h: 1, e: 1, l: 3, o: 2, ' ': 1, w: 1, r: 1, d: 1 }

```

```js

let d = str.split("").reduce((acc, curr) => {
  if (acc[curr] === undefined) {
    acc[curr] = 1;
  } else {
    acc[curr] += 1;
  }
  return acc; // Make sure to return the accumulator here
}, {});

console.log(d); // Expected output: { h: 1, e: 1, l: 3, o: 2, ' ': 1, w: 1, r: 1, d: 1 }

```

## 6.How to check if a given number is an integer?

```js
console.log(Number.isInteger(123))
```

## 7.Sort a given array of strings?

```js
const arr = ["apple", "banana", "orange", "grape", "mango"];
```

```js
arr.sort((a, b) => a.localeCompare(b));
console.log(arr);
```

## 8.find unique elements in an array

```js
const arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
```
```js
const unique = arr.filter((item, index) => arr.indexOf(item) === index);
console.log(unique);
```
```js
const uniqueArr = [...new Set(arr)];
```

## 9.Find maximum value in a numbered array?

```js
let arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
```

```js
Math.max(...arr);
```

```js

let max = arr.reduce((prev,curr)=>{
    return prev > curr ? prev : curr
})

```

## 10.How can you uppercase the first character in a string array?

```js
const stringArray = ["hello", "world", "javascript", "developer"];

```
```js
const capitalizedArray = stringArray.map(str => 
  str.charAt(0).toUpperCase() + str.slice(1)
);
```

## 11.How to make a sentence out of the given string array?

```js
const stringArray = ["Hello", "world", "this", "is", "JavaScript"];
```
```js 
const sentence = stringArray.join(' '); // Joins the array with spaces between words

console.log(sentence); // Output: "Hello world this is JavaScript"
```

## 12.How to check if an array contains any element of another array?

```js
const array1 = [1, 2, 3, 4, 5];
const array2 = [4, 6, 7];
```

```js
const hasCommonElement = array2.some(element => array1.includes(element));
```

## 13.How to check if an array contains all elements of another array?

```js
let array1 = [1, 2, 3, 4, 5];
let array2 = [4, 6, 7];
```

```js
array2.every(element => array1.includes(element));
```

## 14.How to check if an array contains all elements of another array?

```js
let array1 = [1, 2, 3, 4, 5];
let array2 = [4, 6, 7];

function containsAllElements(array1, array2) {
  return array2.every(element => array1.includes(element));
}
```

## 15.Check which elements are common in two arrays?

```js
let array1 = [1, 2, 3, 4, 5];
let array2 = [4, 6, 7];
```

```js
function commonElements(array1, array2) {
  return array1.filter(element => array2.includes(element));
}

console.log(commonElements(array1, array2));
```

## 16.Given two strings, how can you check if the strings are anagram for each other?

```js
function areAnagrams(str1, str2) {
  // Remove whitespace and convert both strings to lowercase
  const normalize = str => str.replace(/\s+/g, '').toLowerCase();

  // Sort the characters in the string
  const sortedStr1 = normalize(str1).split('').sort().join('');
  const sortedStr2 = normalize(str2).split('').sort().join('');

  // Check if sorted strings are equal
  return sortedStr1 === sortedStr2;
}

// Test cases
console.log(areAnagrams("listen", "silent")); // Output: true
console.log(areAnagrams("triangle", "integral")); // Output: true
console.log(areAnagrams("apple", "pale")); // Output: false

```

## 17.Filter the given object based on certain conditions and return the corresponding object?

age >= 15 ; roll <= 200 ; marks >= 80

```js
var obj = {
    'Students': [{
            "name": "Raj",
            "Age": "15",
            "RollNumber": "123",
            "Marks": "99",
        }, {
            "name": "Aman",
            "Age": "14",
            "RollNumber": "223",
            "Marks": "69",
        }, {
            "name": "Vivek",
            "Age": "13",
            "RollNumber": "253",
            "Marks": "89",
        }]
};
```

```js
const filteredStudents = obj.Students.filter(student => 
    parseInt(student.Age) >= 15 &&
    parseInt(student.RollNumber) <= 200 &&
    parseInt(student.Marks) >= 80
);

console.log({ 'FilteredStudents': filteredStudents });

```

## 18.Reverse a given string?

```js
let str = "Hello World";
```

```js
str.split("").reverse().join("");
```

## 19.How to check if a given string is a palindrome?

```js
let str = "racecar";
```

```js
str === str.split("").reverse().join("");
```

## 20.How to check if an object is present in an Array or not?

```js
const array = [
  { id: 1, name: 'John' },
  { id: 2, name: 'Alice' },
  { id: 3, name: 'Bob' }
];

const objectToFind = { id: 2, name: 'Alice' };

```

```js
const isPresent = array.some(item => 
  item.id === objectToFind.id && item.name === objectToFind.name
);
```