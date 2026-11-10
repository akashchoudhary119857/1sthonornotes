### `var`

- **Scope**: `var` is function-scoped, meaning it is accessible within the function it is declared in. If declared outside a function, it is globally scoped.
- **Hoisting**: Variables declared with `var` are hoisted to the top of their scope and initialized with `undefined`.
- **Re-declaration and Re-assignment**: You can re-declare and re-assign `var` variables within the same scope.

    ```javascript
    var x = 10;
    var x = 20; // Re-declaration is allowed
    x = 30;    // Re-assignment is allowed
    ```
### `let`

- **Scope**: `let` is block-scoped, meaning it is only accessible within the block (e.g., `{}`) it is declared in.
- **Hoisting**: Variables declared with `let` are hoisted but not initialized. Accessing them before declaration results in a `ReferenceError`.
- **Re-declaration and Re-assignment**: You cannot re-declare `let` variables within the same scope, but you can re-assign them.

    ```javascript
    let y = 10;
    // let y = 20; // Re-declaration is not allowed
    y = 30;      // Re-assignment is allowed
    ```
### `const`

- **Scope**: `const` is also block-scoped.
- **Hoisting**: Similar to `let`, `const` variables are hoisted but not initialized.
- **Re-declaration and Re-assignment**: You cannot re-declare or re-assign `const` variables. They must be initialized at the time of declaration.

    ```javascript
    const z = 10;
    // const z = 20; // Re-declaration is not allowed
    // z = 30;      // Re-assignment is not allowed
    ```
### Key Differences

1. **Scope**:
    
    - `var` is function-scoped.
    - `let` and `const` are block-scoped.
2. **Hoisting**:
    
    - `var` is hoisted and initialized with `undefined`.
    - `let` and `const` are hoisted but not initialized.
3. **Re-declaration**:
    
    - `var` can be re-declared within the same scope.
    - `let` and `const` cannot be re-declared within the same scope.
4. **Re-assignment**:
    
    - `var` and `let` can be re-assigned.
    - `const` cannot be re-assigned.

### Example

Here’s an example to illustrate these differences:

JavaScript

```javascript
function example() {
  if (true) {
    var a = 1;
    let b = 2;
    const c = 3;
  }
  console.log(a); // 1
  console.log(b); // ReferenceError: b is not defined
  console.log(c); // ReferenceError: c is not defined
}
example();
```

Let and const was introduced in 2015 i.e ES 6 before that we just had var 
Var is globar and re-declared and updated
const is block specific and cannot re-declared not even update
let is block specific and cannot re-declared but we can update its value as it is a variable 
curly braces {} are define as blocks / scope
``` Example
{
let num = 23;
console.log(num)
}
```

``` ExampleError
{
let num = 23;
let num = 56;
console.log(num)
}
```
``` ExampleBlockSpecific
{
let num = 23;
console.log(num)
}
{
let num = 34;
console.log(num)
}
```
[[Data Types In JavaScript]]
