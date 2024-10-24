# ✰ String and Maths in Javascript

## What is String?

Ans : String is a sequence of characters. It is used to represent text in JavaScript.

## Explain Popular Methods of String?

Ans : **source** : https://www.w3schools.com/js/js_string_methods.asp

## CharAt() Method vs at Method in String?

Ans : The at() method is a new addition to JavaScript.

It allows the use of negative indexes while charAt() do not.

## [] vs CharAt() Method in String?

Ans : If no character is found, [ ] returns undefined, while charAt() returns an empty string.

## Str[0] = "A" will replace the first character of the string str with the character A?

Ans : Strings are immutable.It is **read only**. str[0] = "A" gives no error (but does not work!)

## slice vs substring ?

Ans : The difference is that start and end values less than 0 are treated as 0 in substring(). That's mean it does not take negative values.

## substr vs slice vs substring ?

Ans : substr() second parameter specifies the length of the extracted part.(How manay character we want to extract)

```
let text = "Apple, Banana, Kiwi";


console.log(text.slice(1,4)) // ppl
console.log(text.substring(1,4)) // ppl
but,
console.log(text.substr(1,4)) // pple
```

## Does string methods return a new string or mutate the original string?

Ans : All string methods return a new string. They don't modify the original string.

Formally said:

Strings are immutable: Strings cannot be changed, only replaced.

## What is the use of padStart() and padEnd() methods in JavaScript?

Ans : It pads a string with another string (multiple times) until it reaches a given length.

padStart() and padEnd() methods are used to pad a string with a specified character or string.

```
console.log(text.padStart(40,"XXX")) // XXXXXXXXXXXXXXXXXXXXXApple, Banana, Kiwi
```

## How to make replace method case insensitive?

Ans : use regex with i flag

```
let text = "Please visit Microsoft!";
let newText = text.replace(/MICROSOFT/i, "W3Schools");
```
## By default replace only replace 1st match, how to replace all matches?

Ans : use regex with g flag

```
let text = "Please visit Microsoft and Microsoft!";
let newText = text.replace(/Microsoft/g, "W3Schools");
```

## indexOf vs search?

Ans : 

.searc() does not take second parameter.

.indexof() cannot use powerful search or regex.

## How match() and matchAll() works?

Ans : Basically used to check regex.
      
## What are Math methods in JavaScript?

Ans : **source** : https://www.w3schools.com/js/js_math.asp

## Math.round() vs Math.floor() vs Math.ceil() vs Math.trunc() in JS?

```
let numPositive = 4.6;
let numNegative = -4.6;

console.log("Math.round():");
console.log(Math.round(numPositive)); // 5
console.log(Math.round(numNegative)); // -5

console.log("Math.floor():");
console.log(Math.floor(numPositive)); // 4
console.log(Math.floor(numNegative)); // -5

console.log("Math.ceil():");
console.log(Math.ceil(numPositive));  // 5
console.log(Math.ceil(numNegative));  // -4

console.log("Math.trunc():");
console.log(Math.trunc(numPositive)); // 4
console.log(Math.trunc(numNegative)); // -4

```
## Math.random()?

Ans : which generates a floating-point number between 0 (inclusive) and 1 (exclusive).

## How do you generate a random integer between two numbers (inclusive)?

Ans : 
```
function getRandomInt(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}
console.log(getRandomInt(1, 10)); // Example output: random number between 1 and 10

```