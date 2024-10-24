
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

##