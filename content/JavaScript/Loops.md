## Types of Loops in JavaScript

JavaScript provides several looping structures to repeatedly execute a block of code until a specific condition is met.

---

### 1. **for Loop**

Used when the number of iterations is known.

**Syntax:**

`for (initialization; condition; increment/decrement) {   // code to be executed }`

**Example:**

`for (let i = 0; i < 5; i++) {   console.log(i); }`

**Explanation:**

- Initialization: runs once before the loop starts.
    
- Condition: checked before each iteration.
    
- Increment/Decrement: updates the counter after each loop.
    

---

### 2. **while Loop**

Used when the number of iterations is **not known** in advance and depends on a condition.

**Syntax:**

`while (condition) {   // code to execute }`

**Example:**

`let i = 0; while (i < 5) {   console.log(i);   i++; }`

**Explanation:**

- The loop continues as long as the condition is true.
    
- If the condition is false initially, the loop will not run.
    

---

### 3. **do...while Loop**

Similar to `while`, but executes the block **at least once**, even if the condition is false.

**Syntax:**

`do {   // code to execute } while (condition);`

**Example:**

`let i = 0; do {   console.log(i);   i++; } while (i < 5);`

**Explanation:**

- Executes the block once before checking the condition.
    

---

### 4. **for...in Loop**

Used to **iterate over the enumerable properties (keys)** of an object.

**Syntax:**

`for (let key in object) {   // code to execute }`

**Example:**

`let person = { name: "John", age: 25, city: "Delhi" };  for (let key in person) {   console.log(key + ": " + person[key]); }`

**Explanation:**

- Iterates through all enumerable keys, including inherited ones.
    
- Commonly used for objects, not arrays.
    

---

### 5. **for...of Loop**

Used to **iterate over iterable objects** like arrays, strings, sets, or maps.

**Syntax:**

`for (let element of iterable) {   // code to execute }`

**Example:**

`let numbers = [10, 20, 30];  for (let num of numbers) {   console.log(num); }`

**Explanation:**

- Accesses **values** directly (not indexes).
    
- Works on any object that implements an iterator.
    

---

### 6. **forEach() Loop (Array Method)**

The `forEach()` method is an array function that executes a callback for each element.

**Syntax:**

`array.forEach(function(element, index, array) {   // code to execute });`

**Example:**

`let fruits = ["apple", "banana", "mango"];  fruits.forEach(function(fruit, index) {   console.log(index + ": " + fruit); });`

**Explanation:**

- Cannot be stopped using `break` or `continue`.
    
- Best for performing operations on each array element.
    

---

### 7. **Nested Loops**

A loop inside another loop.

**Example:**

``for (let i = 1; i <= 3; i++) {   for (let j = 1; j <= 2; j++) {     console.log(`i = ${i}, j = ${j}`);   } }``

**Explanation:**

- The inner loop runs completely for every iteration of the outer loop.
    

---

### Summary Table

|Loop Type|Purpose|Works On|Executes at least once|Break/Continue Supported|
|---|---|---|---|---|
|for|Fixed number of iterations|Any|No|Yes|
|while|Unknown number, condition-based|Any|No|Yes|
|do...while|Condition-based, runs once minimum|Any|Yes|Yes|
|for...in|Iterates over object keys|Objects|No|Yes|
|for...of|Iterates over iterable values|Arrays, Strings, Maps, Sets|No|Yes|
|forEach()|Array iteration with callback|Arrays|No|No|
|Nested Loop|Loop inside a loop|Any|Depends|Yes|