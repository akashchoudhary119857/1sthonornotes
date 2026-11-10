## `for...of` in JavaScript

### Overview

The **`for...of`** loop is used to **iterate over iterable objects** — such as arrays, strings, maps, sets, and other data structures that implement the **iterator protocol**.  
It allows you to **access the values directly**, not the keys or indexes.

---

### Syntax

`for (let variable of iterable) {   // code to execute }`

- `variable`: A local variable that stores the current value in each iteration.
    
- `iterable`: An object that can be iterated (like an array, string, Map, or Set).
    

---

### 1. Using `for...of` with Arrays

**Example:**

`let numbers = [10, 20, 30];  for (let num of numbers) {   console.log(num); }`

**Output:**

`10 20 30`

**Explanation:**

- The loop iterates through array **values** directly.
    
- It does not give indexes (use `for...in` for indexes).
    

---

### 2. Using `for...of` with Strings

**Example:**

`let word = "HELLO";  for (let ch of word) {   console.log(ch); }`

**Output:**

`H E L L O`

**Explanation:**

- Loops through each character of the string.
    

---

### 3. Using `for...of` with Sets

**Example:**

`let mySet = new Set(["apple", "banana", "cherry"]);  for (let fruit of mySet) {   console.log(fruit); }`

**Output:**

`apple banana cherry`

**Explanation:**

- Loops through unique values of a Set.
    
- No duplicates, and order is preserved as insertion order.
    

---

### 4. Using `for...of` with Maps

**Example:**

`let myMap = new Map([   ["name", "Alice"],   ["age", 25],   ["city", "Delhi"] ]);  for (let [key, value] of myMap) {   console.log(key + " = " + value); }`

**Output:**

`name = Alice age = 25 city = Delhi`

**Explanation:**

- Each iteration returns a `[key, value]` pair.
    

---

### 5. Using `for...of` with NodeList or HTMLCollection (in Browser)

**Example:**

`let buttons = document.querySelectorAll("button");  for (let btn of buttons) {   console.log(btn.textContent); }`

**Explanation:**

- Useful in DOM manipulation for looping over HTML elements.
    

---

### 6. Using `for...of` with `break` and `continue`

**Example:**

`let arr = [1, 2, 3, 4, 5];  for (let num of arr) {   if (num === 3) continue;   if (num === 5) break;   console.log(num); }`

**Output:**

`1 2 4`

**Explanation:**

- `continue` skips the current iteration.
    
- `break` exits the loop completely.
    

---

### 7. Comparing `for...of` and `for...in`

|Feature|`for...of`|`for...in`|
|---|---|---|
|Works On|Iterable objects (arrays, strings, sets, maps)|Objects and arrays|
|Returns|Values|Keys or indexes|
|Use Case|Reading values|Reading property names or indexes|
|Skips Prototype Properties|Yes|No|

**Example:**

`let arr = ["a", "b", "c"];  for (let i in arr) {   console.log(i); // 0, 1, 2 }  for (let val of arr) {   console.log(val); // a, b, c }`

---

### 8. Using `for...of` with Custom Iterables

You can make your own object iterable using `[Symbol.iterator]`.

**Example:**

`let myObject = {   start: 1,   end: 3,   [Symbol.iterator]() {     let current = this.start;     let last = this.end;     return {       next() {         if (current <= last) {           return { value: current++, done: false };         } else {           return { done: true };         }       }     };   } };  for (let num of myObject) {   console.log(num); }`

**Output:**

`1 2 3`

---

### Summary

|Feature|Description|
|---|---|
|Purpose|Iterates over values of iterable objects|
|Works On|Arrays, Strings, Maps, Sets, NodeLists, custom iterables|
|Access Type|Values directly|
|Skips Prototype Properties|Yes|
|Supports break/continue|Yes|
|Common Mistake|Using on plain objects (will cause TypeError)|