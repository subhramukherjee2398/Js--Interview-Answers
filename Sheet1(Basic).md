
# Basic

## 1 .What is the difference between var, let, and const?

Ans : 

**var** : 

Scope: Function-scoped or globally scoped. If declared outside a function, it is accessible anywhere in the script. Inside a function, it is only accessible within that function.

Hoisting: Variables declared with var are hoisted to the top of their containing function or global context. This means they can be referenced before their declaration, but their value will be undefined until the declaration line is reached.

Re-declaration: You can re-declare a var variable within the same scope.

**let** :

Scope: Block-scoped. Variables declared with let are only accessible within the block {} they are defined in.

Hoisting: Similar to var, let variables are hoisted, but they cannot be accessed until the declaration is encountered (this is known as the "temporal dead zone").

Re-declaration: You cannot re-declare a let variable in the same scope.

**const** :

Scope: Block-scoped, like let.

Hoisting: Also hoisted, with the same temporal dead zone behavior as let.
Re-declaration: You cannot re-declare a const variable in the same scope.

Mutability: Variables declared with const cannot be reassigned. However, if the variable is an object or an array, you can still modify its properties or elements


## 2. What is the use of "use strict" in js ?

Ans : Basuically use strict is a optional flag that can be used to enable stricter parsing and error handling in ECMAScript modules.

Restrictions:

1.Prevents Undeclared Variables.

2.Disallows Duplicate Parameter Names.

3.Eliminates this Binding to Global Object: ( does not allow gert access global object).

4.Prohibits Deleting Variables/Objects/Functions:

## Global context value if different in different environments?

Ans :

| **JavaScript Environment**       | **Global Object**                       | **Access Example**                               | **Notes**                                                                                     |
|----------------------------------|-----------------------------------------|------------------------------------------------|---------------------------------------------------------------------------------------------|
| **Browser**                      | `window` / `self` / `frames` / `globalThis` | ```console.log(window);```                       | `window` is the main global object in browsers. `globalThis` is standard and cross-platform. |
| **Node.js**                      | `global` / `globalThis`                 | ```console.log(global);```                       | `global` is specific to Node.js. `globalThis` is the cross-platform standard.               |
| **Web Workers**                  | `self` / `globalThis`                   | ```console.log(self);```                         | `self` is used as the global object in Web Workers.                                         |
| **Deno**                         | `globalThis`                            | ```console.log(globalThis);```                   | Deno follows the standard `globalThis`.                                                     |
| **Shell (e.g., Rhino, SpiderMonkey)** | `global`                              | ```console.log(global);```                       | Some command-line environments use `global`.                                                |
| **Electron (Renderer Process)**  | `window` / `global`                     | ```console.log(window);```                       | Electron has access to both `window` (Browser) and `global` (Node.js).                      |

```
console.log(globalThis); // Works in Browser, Node.js, Deno, Web Workers, etc.
```

## What is scope in JavaScript?

Ans : 

Scope refers to the visibility or accessibility of variables, functions, and objects in some particular part of your code during runtime.

There are different types of scopes in JavaScript:

1. **Global Scope**: Variables declared outside of any function or block have global scope. These variables can be accessed from anywhere in your code.

2. **Local Scope**: Variables declared inside a function or block have local scope. These variables can only be accessed within that function or block.

3. **Block Scope**: Variables declared inside a block, such as an if statement or a loop, have block scope. These variables can only be accessed within that block.

4. **Function Scope**: Variables declared inside a function have function scope. These variables can only be accessed within that function.

5. **Lexical Scope**: Functions can access varaibles from their parent or outer scopes. This is called lexical scope.


## What is Hoisting in JavaScript?

Ans : Hoisting is a JavaScript mechanism where variable and function declarations are moved to the top of their containing scope during the compile phase. This means that you can use variables and functions before they are declared in the code. However, only the declarations are hoisted, not the initializations.

- Only declarations are hoisted, not initializations.
- var variables are hoisted to the top of their scope and initialized with undefined.
- let and const are also hoisted but are in a "Temporal Dead Zone" until declared.
- Function declarations are fully hoisted, while function expressions are not.

## what is closure in JavaScript?

Ans : In javascript ,if we have a child function inside a parent function, the child function can access the variables of the parent function even after the parent function has finished executing. That Means closure allows a function to "remember" its surrounding context or environment, even after that context has finished executing.

so we can say that a function always binds with it's lexical scope that forms a closure.

```

function outerFunction() {
    let outerVariable = 'I am from the outer scope!';

    function innerFunction() {
        console.log(outerVariable); // Accessing the outer variable
    }

    return innerFunction; // Returning the inner function
}

const closureFunc = outerFunction(); // outerFunction is executed
closureFunc(); // Output: "I am from the outer scope!"


```