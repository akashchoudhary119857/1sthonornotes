# JavaScript `this` Behavior: Regular vs Arrow Functions

## 1. Regular Function

```javascript
function greet(name) {
    return "Hello " + name;
}

console.log(greet("hi")); // Output: Hello hi
```

- Regular functions behave normally, using arguments as expected.
    

---

## 2. Arrow Function

```javascript
const greet1 = () => "Hello";
console.log(greet1()); // Output: Hello
```

- Arrow functions are concise and do not have their own `this`.
    

---

## 3. `this` in Arrow Functions (Lexical `this`)

```javascript
function data() {
    this.age = 20;
    setTimeout(() => {
        console.log(this.age); // Output: 20
    }, 2000);
}

const d = new data();
```

- Arrow functions inherit `this` from the surrounding scope (`data` instance here).
    

---

## 4. `this` in Traditional Function (Dynamic `this`)

```javascript
function showThis() {
    console.log(this);
}

const obj = { name: "Akki", fn: showThis };

obj.fn();   // Output: obj
showThis(); // Output: window (or global object in Node.js)
```

- In traditional functions, `this` is dynamic:
    
    - If called as a method, it points to the object.
        
    - If called standalone, it points to the global object.
        

---

## 5. Lexical `this` in Arrow Functions

```javascript
function outer() {
    this.value = 100;

    const arrowFn = () => {
        console.log(this.value); // Output: 100
    };

    arrowFn();
}

const obj1 = new outer();
```

- Arrow functions inherit `this` from the parent scope (`outer` instance here).
    

---

## 6. `this` in `setInterval` Example

### a. Normal Function (Dynamic `this`)

```javascript
function Person() {
    this.age = 0;

    setInterval(function() {
        this.age++; // ❌ 'this' points to global object
    }, 1000);
}
```

- The callback inside `setInterval` creates its own `this`, not pointing to the `Person` instance.
    
- `this.age` will be `undefined` or `NaN`.
    

### b. Using `.bind(this)`

```javascript
function Person() {
    this.age = 0;

    setInterval(function() {
        this.age++; //  'this' is bound to Person instance
    }.bind(this), 1000);
}
```

- `.bind(this)` locks `this` to the `Person` instance.
    

### c. Arrow Function Version

```javascript
function Person() {
    this.age = 0;

    setInterval(() => {
        this.age++; //  'this' comes from lexical scope (Person)
    }, 1000);
}
```

- Arrow functions do not have their own `this`.
    
- They inherit `this` from the surrounding context (lexical `this`).
    

---

###  Key Takeaways:

1. **Regular Functions**: `this` is dynamic and depends on how the function is called.
    
2. **Arrow Functions**: `this` is lexical — inherits from the surrounding scope.
    
3. **`bind(this)`**: Forces a function to use a specific `this`.
    
4. **setTimeout/setInterval**: Use arrow functions or `.bind(this)` to refer to the parent context.