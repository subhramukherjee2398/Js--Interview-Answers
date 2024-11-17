
# Coding Challenge : Javascript

## How to define a class with properties and methods in JavaScript?


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

## How to implement class inheritance in JavaScript?

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

## How to find duplicate elements in a given array?

```js
let arr = [1,2,3,4,5,6,7,8,9,10,1,2,3,4,5,6,7,8,9,10]
```
```js
let duplicate = arr.filter(function(item, index, array){
    return array.indexOf(item) !== index;
});
console.log(duplicate)
```
## How to find duplicate elements in a given array?

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

## Count Occurrences of a Character in a String

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

## How to check if a given number is an integer?

```js
console.log(Number.isInteger(123))
```

## Sort a given array of strings?

```js
const arr = ["apple", "banana", "orange", "grape", "mango"];
```

```js
arr.sort((a, b) => a.localeCompare(b));
console.log(arr);
```

## find unique elements in an array

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

## Find maximum value in a numbered array?

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

## How can you uppercase the first character in a string array?



