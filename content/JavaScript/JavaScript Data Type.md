 # **JavaScript Data Types, Number vs BigInt & Expression Printing**

---

##  **1. JavaScript Data Types**

JavaScript data types are divided into **two main categories**:

---

### **1. Primitive Data Types**
Primitive types store **single values** and are **immutable** (cannot be changed directly).

|Data Type|Description|Example|
|---|---|---|
|**String**|Text values enclosed in quotes (`" "`, `' '`, or `` ` ` ``)|`"Hello"`, `'World'`, `` `Template` ``|
|**Number**|Numeric values (integer or floating-point)|`10`, `3.14`, `-5`|
|**Boolean**|Logical values — only `true` or `false`|`true`, `false`|
|**Undefined**|A variable declared but not assigned any value|`let a; // undefined`|
|**Null**|Represents intentional absence of any object value|`let data = null;`|
|**Symbol**|Unique and immutable value, often used as object keys|`let id = Symbol("id");`|
|**BigInt**|Represents very large integers beyond `Number.MAX_SAFE_INTEGER`|`let bigNum = 1234567890123456789012345n;`|

---

### **2. Non-Primitive (Reference) Data Types**
These hold **collections or complex structures** and are **mutable**.

|Data Type|Description|Example|
|---|---|---|
|**Object**|Collection of key–value pairs|`{ name: "Alex", age: 25 }`|
|**Array**|Ordered list of values|`[1, 2, 3, "four"]`|
|**Function**|Block of code designed to perform a task|`function greet() { console.log("Hi!"); }`|

---

### ⚙️ **Example in Action**

let name = "John";                                          // String 
let age = 25;                                                  // Number
let isStudent = true;                                      // Boolean 
let address;                                                   // Undefined 
let score = null;                                            // Null 
let id = Symbol("id");                                    // Symbol 
let big = 12345678901234567890n;             // BigInt  
let person = { name: "John", age: 25 };            // Object
let marks = [90, 85, 88];                                  // Array 
function greet() { console.log("Hello"); }          // Function`

---

### **`typeof` Operator**


Use the `typeof` operator to check a variable’s data type:
typeof "Hello";               // "string" 
typeof 10;                      // "number" 
typeof true;                   // "boolean"
typeof undefined;         // "undefined" 
typeof null;                   // "object"  // known JavaScript bug 
typeof Symbol();           // "symbol" 
typeof 123n;                 // "bigint"`

---

##  **2. Number vs BigInt in JavaScript**
Both represent numeric values but differ in **precision**, **range**, and **behavior**.

---
### **Number**
- Default numeric type in JavaScript
    
- Uses **64-bit floating-point** format
    
- Can represent integers and decimals
    
- Has **precision limits**
    

#### Range:

`Number.MAX_SAFE_INTEGER  // 9007199254740991  (2^53 - 1) Number.MIN_SAFE_INTEGER  // -9007199254740991`

#### ⚠️ Example:

let x = 9007199254740991;       // Max safe integer 
console.log(x + 1);                    // 9007199254740992 
console.log(x + 2);                    // 9007199254740992  (precision lost)

---

### **BigInt**

- Introduced in **ES2020**
    
- Stores integers **beyond the safe range**
    
- Created by appending `n` or using `BigInt()`
    

let big = 9007199254740991n; 
console.log(big + 2n);             // 9007199254740993n ( accurate)

---

###  **Comparison Table**

|Feature|**Number**|**BigInt**|
|---|---|---|
|Type|Floating-point (64-bit)|Arbitrary-precision integer|
|Range|±(2⁵³ − 1)|Unlimited|
|Supports decimals?|✅ Yes|❌ No|
|Performance|Faster for normal math|Slower for huge values|
|Creation|`let x = 42;`|`let y = 42n;` or `BigInt(42)`|
|Mixing allowed?|❌ No|Must convert manually|
|`typeof` result|`"number"`|`"bigint"`|

---

###  **Mixing Error Example**

let num = 10; 
let big = 20n; 
console.log(num + big);    //  TypeError`

 **Fix:**

`console.log(BigInt(num) + big); // Works fine`

---

### **Precision Example**

// Number loses precision 
let a = 12345678901234567890; 
console.log(a);           // 12345678901234567000 
// BigInt keeps precision 
let b = 12345678901234567890n; 
console.log(b);           // 12345678901234567890n `

---

## **3. Ways to Print Expression Values in JavaScript**

Let’s take an example:

`let x = 5, y = 3;`

Expression:

`x + y  // → 8`

---

### 🖥️ **Common Output Methods**

|Method|Example|Output|Use Case|
|---|---|---|---|
|**console.log()**|`console.log(x + y);`|`8`|Print to console|
|**console.warn()**|`console.warn("Warning:", x + y);`|⚠️ Warning text|Highlight warnings|
|**console.error()**|`console.error("Error:", x + y);`|❌ Red text|Errors/debug|
|**alert()**|`alert("Result is " + (x + y));`|Popup|Notify user|
|**document.write()**|`document.write("Sum = " + (x + y));`|On web page|Simple demo|
|**innerHTML**|`document.getElementById("out").innerHTML = x + y;`|In HTML element|Dynamic UI|
|**console.table()**|`console.table({ x, y, sum: x + y });`|Table view|Structured data|

---

### **Template Literal Example**

console.log(`The result of ${x} + ${y} = ${x + y}`);

---

## **4. Expression: (2 ** 53) − 1**

> Use `**` for exponentiation, not `^` (which means XOR).

`let value = (2 ** 53) - 1; console.log(value); // 9007199254740991`

Equivalent to:

`Number.MAX_SAFE_INTEGER`

---

### **Ways to Print `(2 ** 53) − 1`**

| Method             | Example                                                     | Output              |
| ------------------ | ----------------------------------------------------------- | ------------------- |
| `console.log()`    | `console.log((2 ** 53) - 1);`                               | `9007199254740991`  |
| `alert()`          | `alert((2 ** 53) - 1);`                                     | Popup with value    |
| `document.write()` | `document.write((2 ** 53) - 1);`                            | Displays on webpage |
| `innerHTML`        | `document.getElementById("out").innerHTML = (2 ** 53) - 1;` | Shows inside HTML   |
| `console.info()`   | `console.info("Value:", (2 ** 53) - 1);`                    | Info message        |
| `console.warn()`   | `console.warn("Limit:", (2 ** 53) - 1);`                    | Warning message     |
| `console.table()`  | `console.table({ "Max Safe Integer": (2 ** 53) - 1 });`     | Table format        |
|                    |                                                             |                     |

---

### **Complete Example**

<!DOCTYPE html>
<html>
<body>
  <h3>Ways to Print (2 ** 53 - 1)</h3>
  <p id="output"></p>

  <script>
    let value = (2 ** 53) - 1;

    // Console methods
    console.log("Using log:", value);
    console.info("Using info:", value);
    console.warn("Using warn:", value);
    console.error("Using error:", value);
    console.table({ "Max Safe Integer": value });

    // Browser methods
    alert("Using alert: " + value);
    document.write("Using document.write(): " + value + "<br>");
    document.getElementById("output").innerHTML = "Using innerHTML: " + value;
  </script>
</body>
</html>

---

###  **Bonus: Using BigInt for Larger Values**

`console.log((2n ** 53n) - 1n); // 9007199254740991n`

BigInt ensures **precision** for very large numbers.

---

## **Summary**

|Concept|Key Idea|
|---|---|
|**Primitive Types**|Basic immutable data (string, number, boolean, etc.)|
|**Non-Primitive Types**|Objects, arrays, and functions|
|**Number**|64-bit floating-point; limited precision|
|**BigInt**|Arbitrary-precision integers; use `n` suffix|
|**Printing Methods**|`console.log()`, `alert()`, `document.write()`, `innerHTML`, etc.|
|**(2 ** 53) − 1**|Maximum safe integer → `9007199254740991`|



GLA119857
GLA110103
GLA110102
GLA150085
GLA125230
GLA125236
GLA150275
GLA150284