## 1. **Use a Labelled Break (Recommended)**

JavaScript allows you to label loops and then `break` out of a **specific outer loop** from inside an inner loop.

### Example:

``outerLoop: for (let i = 1; i <= 3; i++) {   for (let j = 1; j <= 3; j++) {     console.log(`i = ${i}, j = ${j}`);     if (i === 2 && j === 2) {       break outerLoop; // breaks out of both loops     }   } } console.log("Loop ended");``

### Output:

`i = 1, j = 1 i = 1, j = 2 i = 1, j = 3 i = 2, j = 1 i = 2, j = 2 Loop ended`

**Explanation:**

- `outerLoop:` is a **label** that names the outer loop.
    
- `break outerLoop;` immediately exits that loop (and all inner loops inside it).
    

---

## 2. **Use a Flag Variable (Manual Control)**

You can set a **boolean flag** to indicate when to stop both loops.

### Example:

``let stop = false;  for (let i = 1; i <= 3 && !stop; i++) {   for (let j = 1; j <= 3; j++) {     console.log(`i = ${i}, j = ${j}`);     if (i === 2 && j === 2) {       stop = true;       break; // breaks inner loop     }   } } console.log("Loop ended");``

**Explanation:**

- The `stop` variable controls whether the outer loop should continue.
    
- After breaking the inner loop, the outer loop condition checks `!stop` and exits too.
    

---

## 3. **Use a Function and Return**

If both loops are inside a function, you can `return` from the function to exit both at once.

### Example:

``function testLoops() {   for (let i = 1; i <= 3; i++) {     for (let j = 1; j <= 3; j++) {       console.log(`i = ${i}, j = ${j}`);       if (i === 2 && j === 2) {         return; // exits both loops and the function       }     }   }   console.log("This will not execute"); }  testLoops(); console.log("Function ended");``

**Explanation:**

- `return` stops execution of both loops since it exits the function entirely.
    

---

## Summary

|Method|Description|Best For|
|---|---|---|
|**Labelled Break**|Uses a label to break outer loop directly|Nested loops|
|**Flag Variable**|Uses a boolean to control loop flow|When label usage is not preferred|
|**Return from Function**|Exits both loops and function|Loops inside a function|