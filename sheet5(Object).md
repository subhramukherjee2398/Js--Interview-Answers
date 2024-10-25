# ✰ Object in Javascript

## what is an Object?
Ans : In JavaScript, an object is a collection of key-value pairs where the keys (also called properties or attributes) are strings or symbols, and the values can be of any data type (such as numbers, strings, arrays, functions, or even other objects). Objects are one of the fundamental data types in JavaScript and are used to store and manage structured data.

## How to create Objects?

Ans : 1.Object Literal Syntax

```
const person = {
    firstName: "John",
    lastName: "Doe",
    age: 30,
    greet: function() {
        console.log(`Hello, my name is ${this.firstName} ${this.lastName}`);
    }
};

```

2.new Object() Constructor

```
const person = new Object();
person.firstName = "John";
person.lastName = "Doe";
person.age = 30;
person.greet = function() {
    console.log(`Hello, my name is ${this.firstName} ${this.lastName}`);
}

```

3.Using a Constructor Function

```
function Person(firstName, lastName, age) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.age = age;
    this.greet = function() {
        console.log(`Hello, my name is ${this.firstName} ${this.lastName}`);
    };
}

const person1 = new Person("Alice", "Smith", 25);
const person2 = new Person("Bob", "Johnson", 40);

```

4.Object.create()

```
const animalPrototype = {
    speak() {
        console.log(`${this.name} makes a sound.`);
    }
};

const cat = Object.create(animalPrototype);
cat.name = "Whiskers";
cat.speak(); // Output: Whiskers makes a sound.

```

5.class Syntax (ES6+)

```
class Animal {
    constructor(name, type) {
        this.name = name;
        this.type = type;
    }
    
    speak() {
        console.log(`${this.name} is a ${this.type} and says hello!`);
    }
}

const dog = new Animal("Buddy", "Dog");
dog.speak(); // Output: Buddy is a Dog and says hello!

```

## General Methods in Object

Ans : sorce : https://www.w3schools.com/js/js_object_methods.asp

## 