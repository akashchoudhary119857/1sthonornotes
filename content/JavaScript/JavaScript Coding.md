We can use our browser to perform the javaScript coding use its console screen or bind up your javaScript code inside HTML file and read it over browser
 Lets understand the concept of print in javaScript.
First clear the console by using ctrl + k
alert("apni dukaan");
apni dukaan via alert box 
==
 Hope you understand why would we use alert and double quotation here
console.log("hello");
console.warn("hello");

hello
```javascript
undefined // The return value of console.log() is undefined
```
console.error("hello");

1. **`console.log()`**: This is the most frequently used method to print messages or variables to the console.
    ```javascript
    console.log("Hello, World!");
    console.log(42);
    console.log({ name: "Alice", age: 30 });

    ```
    
2. **`console.error()`**: Used to output error messages.
    ```javascript
    console.error("This is an error message");
    ```
    
3. **`console.warn()`**: Used to display warnings.
    ```javascript
    console.warn("This is a warning message");
    ```
    
4. **`console.info()`**: Similar to `console.log()`, but intended for informational messages.
    ```javascript
    console.info("This is an informational message");
```

5. **`console.table()`**: Displays data in a table format, which is useful for arrays or objects.
    ```javascript
    const users = [
      { name: "Alice", age: 30 },
      { name: "Bob", age: 25 }
    ];
    console.table(users);
    ```

6. **`console.assert()`**: Writes an error message to the console if the assertion is false.
    ```javascript
    console.assert(1 === 2, "This will log an error because the assertion is false");
    ```
7. **`console.clear()`**: Clears the console.
    ```javascript
    console.clear();
    ```

8. **`console.count()`**: Logs the number of times this line has been called with the given label.
    ```javascript
    console.count("counter");
    console.count("counter");
    ```

9. **`console.dir()`**: Displays an interactive list of the properties of the specified JavaScript object.

    ```javascript
    console.dir(document.body);
    ```

10. **`console.group()` and `console.groupEnd()`**: Groups messages together, making the console output more readable.
    ```javascript
    console.group("User Details");
    console.log("Name: Alice");
    console.log("Age: 30");
    console.groupEnd();
    ```
11. **`console.time()` and `console.timeEnd()`**: Starts and stops a timer, useful for measuring how long an operation takes.
    ```javascript
    console.time("Timer");
    // some code
    console.timeEnd("Timer");
    ```
12. **`console.trace()`**: Outputs a stack trace to the console.
    ```javascript
    function foo() {
      function bar() {
        console.trace("Trace");
      }
      bar();
    }
    foo();
    ```

[[Variable ]]

