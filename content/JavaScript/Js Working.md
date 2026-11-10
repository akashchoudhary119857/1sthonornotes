# Let’s See How JS Actually Works

# 1) Scope — what it is, simply

**Simple idea:**

Scope decides **where a variable is visible** — which parts of your code can see and use that variable.

Think of scope like **rooms in a house**:

- A variable declared in the kitchen is visible inside the kitchen.
- A variable in the living room is visible in the living room.
- Some variables are in the whole house (global) and every room can see them.

## Types of scope in JS (simple list)

1. **Global scope** — visible everywhere.
2. **Function scope** — variables declared inside a function are only visible inside that function.
3. **Block scope** — variables declared with `let`/ `const` inside `{}` are visible only inside that block.
4. **Lexical scope** — inner functions can see variables of outer functions (this leads to _closures_).

---

## Examples you can run in the browser console

### Global scope

```jsx
var name = "Abhi";   // global (var in top level)
console.log(name);   // "Abhi" (visible anywhere)

```

### Function scope

```jsx
function greet() {
  var local = "hello";
  console.log(local); // "hello"
}
greet();
console.log(local); // ReferenceError: local is not defined

```

> Variables declared with var inside a function live only inside that function.

### Block scope (let / const)

```jsx
{
  let x = 10;
  const y = 20;
  console.log(x, y); // 10 20
}
console.log(x); // ReferenceError
console.log(y); // ReferenceError

```

> let and const are block-scoped (they live only inside the {}).

### `var` vs `let` difference (block)

```jsx
{
  var a = 1;
  let b = 2;
}
console.log(a); // 1   (var is not block-scoped)
console.log(b); // ReferenceError (let is block-scoped)

```

### Temporal Dead Zone (TDZ) — quick note

```jsx
console.log(z); // ReferenceError (TDZ)
let z = 5;

```

> let/const are hoisted but not initialized — you cannot use them before the declaration.

### Lexical scope and closures (short demo)

```jsx
function outer() {
  let count = 0;
  function inner() {
    count++;
    console.log(count);
  }
  return inner; // inner *remembers* `count`
}
const c = outer();
c(); // 1
c(); // 2

```

> The inner function “remembers” the outer variable count. That remembered environment = a closure.

---

## takeaways (short)

- Use `const` by default, `let` when you need to reassign; avoid `var` unless you know why.
- **Block scope** (from `let`/`const`) prevents many bugs because variables are limited to the `{ }` where they belong.
- **Closures** let inner functions access outer function variables _even after the outer function has finished_ — powerful and common in JS.

# 🧩 **Execution Context** — How JavaScript _actually_ runs your code

---

## 💭 Step 1: Think of the JS Engine as a Chef 🍳

Imagine you (the browser) hire a chef (the JavaScript Engine).

- The chef’s job: **read your recipe (code)** and **execute it step by step**.
    
- But before the chef starts cooking, he must **set up a kitchen** with all tools and ingredients in place.
    
    That setup is called the **Execution Context**.
    

---

## ⚙️ Step 2: What is an Execution Context?

An **Execution Context (EC)** is simply the **environment in which your code runs** —

it stores all the information the JS engine needs to execute that piece of code.

Every time your JavaScript runs something, it runs _inside_ some context.

There are **two main types** of execution contexts:

1. **Global Execution Context (GEC)**
2. **Function Execution Context (FEC)**

(There’s also **Eval Execution Context**, but it’s rarely used — we’ll skip that for now.)

---

## 🌍 Step 3: Global Execution Context (GEC)

When your JS file runs for the first time,

JavaScript creates a **Global Execution Context** (the base environment).

This happens **before** any of your code executes.

### Example:

```jsx
let x = 10;
function greet() {
  console.log("Hello");
}

```

Here’s what happens:

1. JS engine starts your file → creates a **Global Execution Context**.
2. Inside it, it sets up:
    - A **Global Object** → in browser it’s `window`.
    - A special variable called `this` → also points to `window` in browser.
    - A **Memory Space** for all variables and functions (called _Variable Environment_).

---

## 🧱 Step 4: Two Phases of an Execution Context

Every context is created in **two steps**:

### 🔹 1. Creation Phase (Memory Creation Phase)

JS scans the code **before executing** it.

In this phase:

- It allocates memory for variables and functions.
- Variables declared with `var` are set to `undefined`.
- `let` and `const` are set aside in the **Temporal Dead Zone (TDZ)**.
- Entire function definitions are stored in memory.

Example:

```jsx
console.log(a);
var a = 5;
function sayHi() {
  console.log("Hi!");
}

```

During the **Creation Phase**:

- `a` → memory allocated with `undefined`
- `sayHi` → entire function stored

During the **Execution Phase**:

- `console.log(a)` → prints `undefined`
- Then `a` becomes `5`.

So the **output** is:

```
undefined

```

This process is called **Hoisting** —

because variable and function declarations are “moved to the top” in memory setup.

---

### 🔹 2. Execution Phase

Now the engine runs the code **line by line**:

- Assigns values to variables.
- Executes functions.
- Evaluates expressions.

---

## ⚡ Step 5: Function Execution Context (FEC)

Every time a **function is called**, JS creates a _new mini environment_ for that function — its **own Execution Context**.

Example:

```jsx
let name = "John";

function greet() {
  let message = "Hello " + name;
  console.log(message);
}

greet();

```

Here’s what happens:

1. JS creates **Global Execution Context** for the whole file.
2. When `greet()` is called → JS creates a **new Function Execution Context**.
3. Inside that FEC:
    - A new memory space is created for its local variables (`message`).
    - It also gets access to variables from its outer scope (because of **lexical scope**).

When the function finishes, that context is **destroyed**.

---

## 🧠 Step 6: Call Stack — The “To-Do List” of Execution Contexts

JS is single-threaded → it can do only **one thing at a time**.

So, it uses a **Call Stack** to manage multiple execution contexts.

Think of it like a stack of plates 🍽️:

- The **Global Context** goes at the bottom.
- Each time a function is called → a new “plate” (execution context) is added on top.
- When the function finishes → its plate is removed.

### Example:

```jsx
function first() {
  console.log("First");
  second();
}

function second() {
  console.log("Second");
}

first();
console.log("Done");

```

**Call Stack Flow:**

1. GEC created → put on the stack.
2. `first()` called → new FEC pushed on stack.
3. Inside `first()`, `second()` is called → new FEC pushed.
4. `second()` finishes → popped.
5. `first()` finishes → popped.
6. Back to GEC → runs last `console.log("Done")`.

Output:

```
First
Second
Done

```

---

## 🧩 Step 7: Why Understanding Execution Context Matters

Because **everything** in JS happens inside these contexts.

When you understand how they’re **created**, **stacked**, and **destroyed**,

you understand:

- Why hoisting happens
- How closures keep memory alive
- Why `this` behaves differently inside functions
- How async code (event loop) runs after synchronous code

---

✅ **In short:**

> JavaScript runs everything inside an Execution Context.
> 
> Each context goes through a **creation** (setup) and **execution** (run) phase.
> 
> All contexts are managed using a **Call Stack**.

---

# 🧩 The Call Stack — How JavaScript Keeps Track of Function Calls

---

## 🧠 Imagine this:

Think of JavaScript as a **single chef** in a kitchen 🍳 —

this chef can **cook only one dish at a time**.

He keeps a **stack of recipe cards** to remember what he’s currently cooking.

Each time he starts a new dish (a function call),

he puts a **new recipe card** on top of the stack.

When that dish is done, he removes that card and goes back to the previous one.

That’s exactly what the **Call Stack** does in JavaScript.

---

## ⚙️ What is the Call Stack?

It’s a **data structure** (specifically, a _stack_ — LIFO = Last In, First Out*) that the JavaScript engine uses to **keep track of where it is in your code**.

- When you **call a function**, JS **pushes** that function’s _execution context_ on the stack.
- When the function finishes, JS **pops** it off.
- The engine always executes the function on the **top** of the stack.

---

## 🧩 Step-by-Step Example

Let’s write some code 👇

```jsx
function one() {
  console.log("Inside one");
  two();
}

function two() {
  console.log("Inside two");
  three();
}

function three() {
  console.log("Inside three");
}

one();

```

Let’s walk through this **exactly how the JS engine does**.

---

### 🔹 Step 1: Start the program

JS creates the **Global Execution Context (GEC)**

and **pushes it** to the **Call Stack**.

🧱 Stack:

```
[ Global Execution Context ]

```

---

### 🔹 Step 2: Run `one()`

When JS sees `one()`,

it creates a new **Function Execution Context** for it

and pushes it on top of the stack.

🧱 Stack:

```
[ one() Execution Context ]
[ Global Execution Context ]

```

JS starts running the code _inside `one()`_.

---

### 🔹 Step 3: Inside `one()` → calls `two()`

JS now creates a new **Execution Context** for `two()`

and pushes it onto the stack.

🧱 Stack:

```
[ two() Execution Context ]
[ one() Execution Context ]
[ Global Execution Context ]

```

JS executes `console.log("Inside two")`, then encounters `three()`.

---

### 🔹 Step 4: Inside `two()` → calls `three()`

JS creates an **Execution Context** for `three()`

and pushes it to the top.

🧱 Stack:

```
[ three() Execution Context ]
[ two() Execution Context ]
[ one() Execution Context ]
[ Global Execution Context ]

```

It logs `"Inside three"` and then finishes.

---

### 🔹 Step 5: `three()` finishes

When `three()` is done,

its context is **popped** off the stack.

🧱 Stack:

```
[ two() Execution Context ]
[ one() Execution Context ]
[ Global Execution Context ]

```

JS resumes where it left off in `two()` —

no more lines left → `two()` finishes → popped off.

---

### 🔹 Step 6: Pop everything as functions finish

```
[ one() Execution Context ]
[ Global Execution Context ]

```

→ `one()` finishes → popped off.

Finally only:

```
[ Global Execution Context ]

```

Then when all code is done → the stack becomes empty.

---

### ✅ Output:

```
Inside one
Inside two
Inside three

```

---

## 💡 Key Points to Remember

- JavaScript is **single-threaded** → only one call stack.
- The function currently on **top** of the stack is the one being executed.
- When the stack is empty, JS is idle (ready for new tasks).
- If the stack takes too long → it causes a **“Stack Overflow”** (browser freezes).

---

### Example of Stack Overflow:

```jsx
function repeat() {
  repeat();
}
repeat(); // ❌ Maximum call stack size exceeded

```

The function keeps calling itself → new contexts pile up forever → memory overflows → error.

---

## 🧩 Summary (in plain words)

- The **Call Stack** is like a to-do list of what functions need to run.
- Each function call adds a new “task” (execution context).
- When a function finishes, it’s removed.
- JS always runs the **topmost** function in the stack.

---

# ⚙️ How JavaScript Handles Code That Takes Time

---

## 💭 First, remember this:

JavaScript is **single-threaded**.

That means → it can only **do one thing at a time** (one line of code in the call stack).

So what happens when something takes **time** (like waiting 3 seconds, fetching data from a server, etc.)?

If JS waited for it in the main thread, the **whole browser would freeze**.

To fix this, browsers gave JS some **extra helpers** outside the main engine —

these are called the **Web APIs**.

---

## 🌐 What are Web APIs?

They’re like **helpers provided by the browser**, not by JavaScript itself.

JS engine only knows:

- how to run code (execution context)
- manage functions (call stack)
- and handle the event loop.

But the browser provides **extra abilities**, like:

- `setTimeout()`
- `DOM` (document manipulation)
- `fetch()` (network requests)
- `addEventListener()` (user clicks, etc.)

So when JS sees these — it doesn’t execute them itself.

It **hands them off to the Web APIs** to deal with.

---

## ⚙️ Let’s see this with an example:

```jsx
console.log("Start");

setTimeout(() => {
  console.log("Timeout finished!");
}, 2000);

console.log("End");

```

Let’s walk through what really happens.

---

### 🧠 Step-by-step under the hood:

1️⃣ **Global Execution Context** is created and pushed to the **Call Stack**.

2️⃣ JS starts executing line by line.

- Line 1 → `console.log("Start")`
    
    → runs immediately → prints **Start**.
    

🧱 Stack right now:

```
[ console.log("Start") ]
[ Global Execution Context ]

```

then the console.log finishes → popped off.

---

3️⃣ JS sees `setTimeout(...)`.

Now, the **JS Engine itself** doesn’t know how to wait for 2 seconds —

so it gives that job to the **Web API** part of the browser.

So the flow is:

- JS Engine says: “Hey Web API, here’s a timer function. Wait for 2 seconds, then run this callback.”
- Web API starts the timer **outside** the call stack.

🧱 Stack after sending to Web API:

```
[ Global Execution Context ]

```

Web API (in background):

```
Timer running for 2 seconds...

```

---

4️⃣ JS moves to the next line —

`console.log("End")` → executes immediately → prints **End**.

---

5️⃣ After **2 seconds**, Web API says:

“Timer finished! Here’s the callback function you gave me.”

But — the **Call Stack** might not be empty at that moment.

So Web API doesn’t run it directly.

It sends the callback to the **Callback Queue** (also called **Task Queue**).

---

### 🧾 Callback Queue:

A waiting line for functions that are ready to run —

but can only run when the call stack is empty.

---

6️⃣ **Event Loop** comes into play now.

Think of it as a **watchman** 👀 constantly checking:

> “Is the Call Stack empty? If yes, let me move the next callback from the queue into the stack.”

So once the main code (all synchronous tasks) is done,

and the stack is empty —

the Event Loop moves the callback (`console.log("Timeout finished!")`)

from the **Callback Queue** into the **Call Stack**.

---

7️⃣ JS executes it → prints:

```
Timeout finished!

```

✅ Final output:

```
Start
End
Timeout finished!

```

---

## 🧩 Summary in simple words

- **Call Stack** → runs all normal (synchronous) code.
- **Web APIs** → handle tasks that take time (timers, DOM events, network requests).
- **Callback Queue** → holds the “ready-to-run” callbacks from Web APIs.
- **Event Loop** → moves callbacks from the queue to the call stack **when the stack is empty**.

---

## ⚡ Quick Analogy

Imagine:

- The **Call Stack** is a chef’s cooking station 👨‍🍳.
    
- The **Web APIs** are the assistants (timer guy, waiter, etc.) who do side tasks.
    
- The **Callback Queue** is the “completed orders” counter.
    
- The **Event Loop** is the waiter checking:
    
    > “Is the chef free now? If yes, give him the next plate to finish!”
    

---

So the browser + JS engine together look like this:

```
JS Engine:
 ├── Call Stack
 ├── Event Loop
 └── Heap (memory)

Browser:
 ├── Web APIs (timers, DOM, fetch)
 ├── Callback Queue
 └── Microtask Queue (for promises, later)

```

---

We’ll cover **Microtask Queue** and how its priority works next —

but only when you’re ready. It’s the queue for Promises, Mutation Observers, etc.,

and it has _higher priority_ than the normal callback queue.

---

# 🧠 What is a Closure?

A **closure** happens when a **function “remembers” variables from the place it was created**,

**even after that place (the outer function) is gone**.

That’s the whole concept.

It’s like a function carrying a little backpack 🎒 that contains variables from where it was born.

---

Let’s understand this **with an example.**

```jsx
function outer() {
  let counter = 0;  // a local variable in outer

  function inner() {
    counter++;
    console.log(counter);
  }

  return inner;
}

const fn = outer(); // outer() runs once
fn(); // ?
fn(); // ?

```

What do you think gets printed?

Let’s find out slowly.

---

## Step 1️⃣ — Execution starts

When JS runs `outer()`,

it creates an **execution context** for `outer`.

Inside it:

- It creates a variable `counter` and sets it to `0`.
- It defines a new function `inner`.

At this point, the **inner function** has access to everything inside `outer`

(because functions are created with access to their parent scope — this is called **lexical scoping**).

---

## Step 2️⃣ — Returning the inner function

Now, `outer()` returns `inner` — but **not by calling it** —

it just _returns the function itself._

So after:

```jsx
const fn = outer();

```

`fn` now holds the returned `inner` function.

🧠 BUT — here’s the key part:

Even though `outer()` has finished executing and its execution context is popped off the stack…

…the `inner` function still **remembers** `counter`

because of **closure**.

---

## Step 3️⃣ — Using the closure

When we now call `fn()` (which is really the `inner` function):

```jsx
fn(); // counter = 1
fn(); // counter = 2

```

Each time it runs:

- It looks for `counter` inside its own scope (none found)
- Then it looks into its **lexical parent scope** (the `outer` function’s variables)
- It finds `counter` there → updates it → and logs it.

Even though `outer()` is long gone from the call stack,

its variables (`counter`) are _kept alive_ inside memory

because something (`inner`) is still **referencing them**.

That is a **closure**.

---

## 📦 So, closure = function + its lexical environment

Every function in JavaScript forms a closure by default.

But you _notice_ it only when the inner function **outlives** the outer one.

---

## 🎯 Real-life analogy

Think of a **child (inner function)** who moves out of their **parent’s house (outer function)**,

but still remembers where their family money is kept.

Even if the parent moves away, the child can still access that hidden safe —

because they were given the key 🔑 (the closure).

---

## 🧩 How JavaScript stores this

When `outer()` returns `inner`, JS doesn’t destroy `counter` immediately.

The **memory for `counter`** stays alive in a structure called the **closure environment**

— as long as some function (like `inner`) still needs it.

When there are **no references** to `inner`,

then garbage collection can clean up that memory.

---

## 🧪 Example 2 — Creating multiple closures

```jsx
function createCounter() {
  let count = 0;

  return function() {
    count++;
    console.log(count);
  };
}

const counter1 = createCounter();
const counter2 = createCounter();

counter1(); // 1
counter1(); // 2
counter2(); // 1

```

Here:

- `counter1` has its _own_ closure with its own `count`.
- `counter2` has a _different_ closure with a separate `count`.

They **don’t interfere** with each other,

because each call to `createCounter()` creates a **new lexical environment**.

---

## ⚙️ What’s happening inside JS

Each time `createCounter()` runs:

- A new **execution context** is created.
- A new `count` variable is stored in memory.
- The inner function forms a **closure** around _that specific_ `count`.

When you call `counter1()` or `counter2()`,

they each use their _own_ preserved environment.

---

## 🚀 Closures in real-world use

Closures are powerful because they let you:

1. **Preserve state** between function calls.
    
    (like in the counter example)
    
2. **Create private variables** (data hiding).
    
    Variables inside closure can’t be accessed directly from outside.
    
3. **Build function factories** (functions that create customized functions).
    

---

## Example 3 — Private variables

```jsx
function secretMessage() {
  let message = "JavaScript is awesome";

  return {
    getMessage: function() {
      return message;
    },
    setMessage: function(newMsg) {
      message = newMsg;
    }
  };
}

const msg = secretMessage();
console.log(msg.getMessage());  // "JavaScript is awesome"
msg.setMessage("Closures are cool!");
console.log(msg.getMessage());  // "Closures are cool!"

```

Here, `message` acts like a **private variable** —

you can’t directly access it (e.g., `msg.message` doesn’t exist),

but you can manipulate it through the closure functions.

That’s **data encapsulation** — like private fields in OOP.

---

So to sum it up (teacher mode 🎓):