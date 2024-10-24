# Object-Oriented Programming (OOP)

## What is Object-Oriented Programming (OOP)?

Ans : Object-Oriented Programming (OOP) is a programming paradigm or pattern that uses "objects" to design and structure software applications.

These objects represent real-world entities or concepts and are instances of "classes," which act as blueprints for creating objects.

The key principles of OOP are:

1.**Encapsulation** :

Encapsulation is the concept of bundling data (variables) and methods (functions) that manipulate the data into a single unit called a class. It restricts direct access to those data and prevent data misuse.

Example: In a Car class, attributes like speed and color are private, and you access them through public methods like accelerate() or getColor().

2.Abstraction : Abstraction is the concept of hiding complex implementation details and showing only the necessary features.
It allows you to interact with an object through a simplified interface without worrying about internal complexities.

Example: A CoffeeMachine class might have a method makeCoffee(), which you can use without needing to know the internal mechanics of coffee making.

3.Inheritance :

Inheritance is a mechanism that allows one class (child or subclass) to inherit attributes and methods from another class (parent or superclass)

Example : A Vehicle class can have subclasses like Car and Bike that inherit common features such as speed and fuel, while also having their unique attributes.

4.Polymorphism : Polymorphism allows methods or functions to take on different forms. It means that you can have multiple methods with the same name but different implementations.

It can be achieved through method overloading (same method name with different parameters)

and method overriding (subclass providing a specific implementation of a method inherited from a parent class).

## What is an object in JavaScript? How do you create one?

Ans : In JavaScript, an object is a collection of key-value pairs, where each key is a string (known as a property) and the value can be of any data type (number, string, array, function, another object, etc.)

#### Creating an Object in JavaScript

1.Object Literal Syntax

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

## What are classes in JavaScript?

Ans : In JavaScript, classes are a template for creating objects.

They provide a way to define object blueprints with properties and methods.

Syntax for JavaScript Classes

```
class Person {
  // Constructor is called when a new instance of the class is created
  constructor(name, age) {
    this.name = name; // 'this' refers to the instance of the class
    this.age = age;
  }

  // Method of the class
  greet() {
    console.log(`Hello, my name is ${this.name} and I'm ${this.age} years old.`);
  }
}

// Creating an instance of the class
const person1 = new Person('Alice', 30);

// Calling a method on the instance
person1.greet(); // Output: Hello, my name is Alice and I'm 30 years old.

```

## What are the Key Components of JavaScript Classes?

1.**Constructor**
A special method called when a new instance of the class is created. It is typically used to initialize object properties

```
constructor(parameter1, parameter2) {
  this.property1 = parameter1;
  this.property2 = parameter2;
}
```

2.**Methods**
Methods are functions that are defined within a class. They can be used to perform actions or manipulate data within the class.

```
greet() {
  console.log(`Hello, my name is ${this.name} and I'm ${this.age} years old.`);
}
```

3.**Instance**  An object created using the class blueprint.

```
const instance = new MyClass();
```

4.**Inheritance**  A class can inherit properties and methods from another class using the extends keyword.

```
class Animal {
  constructor(name) {
    this.name = name;
  }
  speak() {
    console.log(`${this.name} makes a noise.`);
  }
}

// Dog inherits from Animal
class Dog extends Animal {
  speak() {
    console.log(`${this.name} barks.`);
  }
}

const dog = new Dog('Buddy');
dog.speak(); // Output: Buddy barks.
```

5.**Static Methods** Methods that belong to the class itself and not to instances. They are defined using the static keyword.

```
class MathUtils {
  static add(num1, num2) {
    return num1 + num2;
  }
}
MathUtils.add(2, 3); // Output: 5
``` 
## What is the difference between a class and an object?

Ans :![objvsclass](./Images/objvsclass.png)

## How do you create an instance of a class in JavaScript?

Ans : To create an instance of a class in JavaScript, you use the new keyword followed by the class name and pass any necessary arguments to the class's constructor.

## What is a constructor function?

Ans : A special method called when a new instance of the class is created. 
It is typically used to initialize object properties by initial state of the object by assigning value.

 In a single class there should be ***only one constructor*** function.

## What is the this keyword in JavaScript? How does it behave inside a class?

Ans:  The this keyword in JavaScript is a special object that refers to the context in which a function or block of code is executed.

- Its value depends on where it is used, how a function is called, and the scope it is in.

- The behavior of this can vary, but inside a class, this typically refers to the instance of the class being created.(means the object)


| **Scope**                          | **Description**                                                                                                                                                 | **Value of `this`**                                                                                                                                                                        | **Example**                                                                                                                                                     |
|-----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Global Context**                 | Outside any function or class. In the global execution context.                                                                                                | In non-strict mode: the global object (`window` in browsers). In strict mode: `undefined`.                                                                                                 | ``` javascript\nconsole.log(this); // In browser, 'this' refers to 'window'.\n ``` |
| **Object Method**                  | Inside a method defined within an object.                                                                                                                      | Refers to the object that the method belongs to.                                                                                                                                           | ```javascript\nconst obj = { name: 'Alice', greet() { console.log(this.name); } };\nobj.greet(); // 'this' is 'obj', Output: Alice\n```                        |
| **Function (Regular Function)**    | Inside a regular function. Not called as a method.                                                                                                             | In non-strict mode: the global object (`window` in browsers). In strict mode: `undefined`.                                                                                                 | ```javascript\nfunction myFunction() { console.log(this); }\nmyFunction(); // In non-strict: 'this' is 'window'. In strict: 'undefined'.\n```                |
| **Arrow Function**                 | Inside an arrow function. Arrow functions do not have their own `this`; they inherit from the enclosing lexical scope.                                         | Inherits `this` from the surrounding lexical context.                                                                                                                                      | ```javascript\nconst arrowFunc = () => { console.log(this); };\narrowFunc(); // Inherits 'this' from the surrounding context.\n```                           |
| **Class (Constructor)**            | Inside a constructor function in a class.                                                                                                                      | Refers to the instance of the class being created.                                                                                                                                         | ```javascript\nclass Person { constructor(name) { this.name = name; } }\nconst person = new Person('Bob');\nconsole.log(person.name); // Output: Bob\n```   |
| **Class (Method)**                 | Inside a method defined in a class.                                                                                                                            | Refers to the instance of the class that called the method.                                                                                                                                | ```javascript\nclass Car { start() { console.log(this); } }\nconst myCar = new Car();\nmyCar.start(); // 'this' is 'myCar' instance.\n```                   |
| **Event Handler (DOM)**            | In an event handler (e.g., attached to a DOM element), `this` refers to the element that the event is attached to.                                            | Refers to the DOM element that triggered the event.                                                                                                                                         | ```javascript\ndocument.getElementById('myBtn').addEventListener('click', function() { console.log(this); }); // 'this' is the clicked button element.\n``` |
| **`call`, `apply`, `bind`**        | When using methods like `call`, `apply`, or `bind` to explicitly set the value of `this`.                                                                      | `this` is explicitly set to the first argument of `call`, `apply`, or `bind`.                                                                                                             | ```javascript\nfunction greet() { console.log(this.name); }\nconst user = { name: 'Alice' };\ngreet.call(user); // 'this' is 'user'. Output: Alice\n```      |
| **IIFE (Immediately Invoked)**     | Inside an Immediately Invoked Function Expression.                                                                                                             | In non-strict mode: the global object (`window` in browsers). In strict mode: `undefined`.                                                                                                 | ```javascript\n(function() { console.log(this); })(); // In non-strict: 'this' is 'window'. In strict: 'undefined'.\n```                                    |
| **Callback Function**              | Inside a callback function, if not bound or not an arrow function.                                                                                             | Depends on how the callback is called. Often `undefined` or the global object in non-strict mode unless context is set explicitly.                                                        | ```javascript\nsetTimeout(function() { console.log(this); }, 1000); // 'this' is 'window' in browsers (or 'undefined' in strict mode).\n```                 |

**Key Takeaways**
 - Global Context: this refers to the global object (or undefined in strict mode).
 - Object Method: this refers to the object containing the method.
- Regular Function: In non-strict mode, this is the global object; in strict mode, this is undefined.
- Arrow Function: this is inherited from the lexical (surrounding) context.
- Class Constructor/Method: this refers to the instance of the class.
- Event Handler: this refers to the DOM element that triggered the event.
- call, apply, bind: You can explicitly control this.

