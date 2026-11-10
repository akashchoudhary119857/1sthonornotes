JavaScript support different data types as per our the convenience of our user: 
There are different data types available in JavaScript to store different data:
JavaScript has several data types, which can be broadly categorized into **primitive** and **non-primitive** types.

### Primitive Data Types

1. **Number**: Represents both integer and floating-point numbers.
    ```javascript
    let num = 42;
    let floatNum = 3.14;
    ```

2. **String**: Represents a sequence of characters.

    ```javascript
    let str = "Hello, World!";
    ```

3. **Boolean**: Represents a logical entity and can have two values: `true` or `false`.

    ```javascript
    let isTrue = true;
    ```

4. **Undefined**: A variable that has been declared but not assigned a value.

    ```javascript
    let undefinedVar;
    ```

5. **Null**: Represents the intentional absence of any object value.

    ```javascript
    let nullVar = null;
    ```

6. **Symbol**: A unique and immutable primitive value, often used as keys for object properties.

    ```javascript
    let sym = Symbol("unique");
    ```

7. **BigInt**: Represents whole numbers larger than the `Number` type can safely represent.

    ```javascript
    let bigInt = 1234567890123456789012345678901234567890n;
    ```

### Non-Primitive Data Types

1. **Object**: A collection of properties, where each property is a key-value pair.

    ```javascript
    let obj = { name: "Alice", age: 30 };
    ```
    * obj["name"] or obj.name is used to access the value of particular key 

2. **Array**: A special type of object used for storing ordered collections.

    ```javascript
    let arr = [1, 2, 3, 4, 5];
    ```

3. **Function**: A block of code designed to perform a particular task.

    ```javascript
    function greet() {
      console.log("Hello!");
    }
    ```

4. **Date**: Represents dates and times.

    ```javascript
    let date = new Date();
    ```

5. **Map**: A collection of keyed data items, similar to an object but with some differences.

    ```javascript
    let map = new Map();
    map.set('key', 'value');
    ```

6. **Set**: A collection of unique values.

    ```javascript
    let set = new Set([1, 2, 3, 4, 5]);
    ```

7. **WeakMap**: A collection of key-value pairs where the keys are weakly referenced.

    ```javascript
    let weakMap = new WeakMap();
    ```

8. **WeakSet**: A collection of objects, where the objects are weakly referenced.

    ```javascript
    let weakSet = new WeakSet();
    ```

### Example Usage

Here’s an example that demonstrates some of these data types:

```javascript
let num = 42; // Number
let str = "Hello, World!"; // String
let isTrue = true; // Boolean
let undefinedVar; // Undefined
let nullVar = null; // Null
let sym = Symbol("unique"); // Symbol
let bigInt = 1234567890123456789012345678901234567890n; // BigInt

let obj = { name: "Alice", age: 30 }; // Object
let arr = [1, 2, 3, 4, 5]; // Array
function greet() { console.log("Hello!"); } // Function
let date = new Date(); // Date
let map = new Map(); // Map
let set = new Set([1, 2, 3, 4, 5]); // Set
let weakMap = new WeakMap(); // WeakMap
let weakSet = new WeakSet(); // WeakSet
```
 we can use typeof variable name

[[Interview Question]]


