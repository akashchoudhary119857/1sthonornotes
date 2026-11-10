  

## 1: JavaScript Before ES6

### ![🧠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) The Origins of JavaScript (1995)

Talking points:

JavaScript was created by Brendan Eich at Netscape in 1995, in just 10 days.

Goal: add small interactivity to web pages (form validation, button clicks, etc.).

Originally called Mocha, then LiveScript, and finally JavaScript (for marketing reasons — Java was popular).

It wasn’t meant for complex applications — just little scripts to make the browser dynamic.

Example:

<button onclick="alert('Hello!')">Click Me!</button>

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “This was what JavaScript was made for — lightweight scripting in the browser.”

### ![⚖️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) The Browser Wars and Chaos (1995–1996)

Netscape had its version of JS.

Microsoft copied it for Internet Explorer — they called it JScript.

Both versions behaved slightly differently!

There was no single rulebook — developers had to write different code for each browser.

Example:

// Netscape document.layers['menu'].visibility = "show"; // Internet Explorer document.all['menu'].style.visibility = "visible";

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “So a simple thing like showing a menu worked differently across browsers. Developers were going crazy.”

### ![📘](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) The Birth of ECMAScript (Standardization)

 ![💡](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) The Big Problem:

JavaScript was everywhere but had no standard definition.

Each browser implemented its own version → inconsistent behavior → web chaos.

 ![💥](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) The Solution:

In 1996, Netscape submitted JavaScript to ECMA International, a standards organization in Europe.

ECMA’s job: define a single official specification that all browsers must follow.

That specification was named ECMAScript.

JavaScript is the implementation.

ECMAScript is the rulebook.

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “Think of ECMAScript as the constitution, and JavaScript as a citizen following its rules.”

### ![📅](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) 4. Timeline of ECMAScript Versions (Quick Context)

|Version|Year|Major Additions|Nickname|
|---|---|---|---|
|ES1|1997|First official standard|The starting point|
|ES2|1998|Minor editorial fixes|Maintenance|
|ES3|1999|try/catch<br><br>, regex, better strings|The first real update|
|ES4|(Never released)|Too ambitious; canceled|Chaos again|
|ES5|2009|strict mode<br><br>,<br><br>JSON<br><br>, array methods|The foundation of modern JS|
|ES6|2015|Classes,<br><br>let/const<br><br>, modules, promises|The big reboot|

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “There was a 10-year gap between ES5 (2009) and ES6 (2015) — that’s how much pressure had built up for change.”

### ![🧱](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) JavaScript Before ES6: The Pain Point

Transition Line:

> “So yes, JS got standardized, but even with ES5, it was still limited. Let’s see what life was like before ES6 came to the rescue.”

Then continue with the previously covered pain points:

## 2 .Let’s Start with a Story

> “Before ES6, we only had var to create variables. It worked… but it often caused weird bugs that even experienced developers found confusing.”

Then, open the console or a live coding environment and start with basic examples.

### ![⚠️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Problem #1 –

var

Ignores Block Scope

#### Scenario (very relatable)

> “Imagine we’re keeping track of a student’s score during a quiz.”

#### Example:

var score = 0; if (true) { var score = 10; // same variable! console.log("Inside if:", score); } console.log("Outside if:", score);

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Ask:

> “What do you think the last line prints?”

Output:

Inside if: 10 Outside if: 10

​

Explain:

> Even though we created a new variable inside the if block, var doesn’t care — it treats both as the same variable.
> 
> It’s function-scoped, not block-scoped. So both refer to the same memory location.

#### ![🧠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Analogy

> “Think of var as a loudspeaker — once declared, its voice echoes throughout the whole function or script. No walls can stop it.”

### ![⚠️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Problem #2 – Redeclaration Is Allowed

var name = "Alice"; var name = "Bob"; // no error! console.log(name); // Bob

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “Imagine two students both trying to use the same name tag — JavaScript just overwrites it silently.”

![💡](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Problem: Large programs with many

var

s could accidentally override variables without warning.

### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) ES6 Solution:

let

and

const

#### ![1️⃣](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

let

— Block Scoped and Safe

let score = 0; if (true) { let score = 10; // different variable console.log("Inside if:", score); } console.log("Outside if:", score);

​

Output:

Inside if: 10 Outside if: 0

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “This is what we expected!

let

respects the curly braces — it stays inside its block.”

#### ![2️⃣](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

let

Does Not Allow Redeclaration

let city = "Delhi"; // let city = "Mumbai"; ❌ Error: Identifier 'city' has already been declared

​

![✅](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Safer, more predictable behavior.

#### ![3️⃣](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

const

— Values That Don’t Change

const pi = 3.14159; pi = 3.14; // ❌ TypeError: Assignment to constant variable.

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “If you never plan to reassign the variable, use

const

. It makes your code more reliable.”

But clarify:

const fruits = ["apple", "banana"]; fruits.push("mango"); // ✅ Works console.log(fruits);

​

> const protects the binding, not the contents.
> 
> You can still modify arrays or objects inside.

### ![🧠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) 6. Best Practice Rules

|Use|When|
|---|---|
|const|Default — when the value shouldn’t change|
|let|When the value will be reassigned|
|var|![❌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Avoid it in modern code|

### ![🎮](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) 7. Practice Tasks

#### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Task 1 — Predict the Output

let num = 5; if (num > 3) { let num = 10; console.log("Inside:", num); } console.log("Outside:", num);

​

#### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Task 2 — Quiz Game Setup

> “Let’s build a small ‘score tracker’ to test our understanding.

let score = 0; const playerName = "Riya"; function answerQuestion(isCorrect) { if (isCorrect) { score += 10; } } answerQuestion(true); answerQuestion(false); console.log(playerName + "'s score is:", score);

​

Ask them:

Can we change

playerName

midway? (No)

Why did we use

let

for score? (Because it changes)

### ![🎯](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Wrap-Up Summary

Key takeaways to repeat aloud:

var

→ function-scoped, can be redeclared → confusing and unsafe.

let

→ block-scoped, can be reassigned.

const

→ block-scoped, cannot be reassigned.

Prefer

const

>

let

>

var

.

## 3: Arrow Functions — Cleaner, Simpler, Smarter

### ![🧠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Quick Recap — What’s a Function?

Start with something visual and simple:

> “A function is like a recipe — you give it ingredients (inputs), it returns a dish (output).”

#### Example

function add(a, b) { return a + b; } console.log(add(2, 3)); // 5

​

note:

> “This is how functions worked since the beginning of JavaScript (ES3/ES5). But as apps grew, developers started writing hundreds of small functions — and the old syntax became a bit heavy.”

### ![⚠️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Pain Point #1 – Verbose Syntax

Example:

function square(x) { return x * x; }

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “Every time we create a small function, we type

function

, parentheses, curly braces, return — a lot of typing for something so simple!”

### ![⚠️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Pain Point #2 – Losing Context with

this

(Intro only, no deep dive yet)

Explain briefly:

> “In old JS, the keyword this behaved differently inside functions depending on how they were called — which confused developers a lot. Arrow functions simplified that by keeping this consistent.”

(We’ll revisit

this

later when they know objects.)

### ![🌟](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) The ES6 Solution — Arrow Function

#### ![✅](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) New, cleaner way to write functions:

const add = (a, b) => { return a + b; };

​

Compare side-by-side:

|ES5|ES6 (Arrow Function)|
|---|---|
|function add(a, b) { return a + b; }|const add = (a, b) => { return a + b; };|

Say:

> “The arrow (=>) replaces the function keyword — it points from inputs to the output.”

### ![✨](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Implicit Return (Shortcuts)

If the function has only one line, we can skip

{}

and

return

.

const square = (x) => x * x; console.log(square(5)); // 25

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “If there’s just one expression, JS automatically returns the result!”

### ![✨](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Even Shorter (Single Parameter)

If there’s only one argument, you can skip the parentheses too:

const double = n => n * 2;

​

### ![🎮](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Practice Tasks

#### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Task 1 — Convert to Arrow Functions

// 1. Turn these into arrow functions: function greet(name) { return "Hello, " + name + "!"; } function add(a, b) { return a + b; } function isEven(num) { return num % 2 === 0; } greet("Dushyant")

​

![➡️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Answers:

const greet = name => `Hello, ${name}!`; const add = (a, b) => a + b; const isEven = num => num % 2 === 0;

​

#### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Task 2 — Use Arrows with Arrays

Introduce them to

.map()

briefly (you can say “it’s a way to apply a function to every element in an array”).

const numbers = [1, 2, 3, 4, 5]; const squares = numbers.map(num => num * num); console.log(squares);

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “This is where arrow functions shine — short, powerful, and readable.”

#### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Task 3 — Make It Fun

> “Let’s create a quick mini-score system using arrow functions!”

const addPoints = (score, points) => score + points; const losePoints = (score, points) => score - points; let score = 0; score = addPoints(score, 10); score = losePoints(score, 5); console.log("Final Score:", score);

​

Then ask:

> “Can you modify this to double the points if the player got a bonus?”

(Encourage creative thinking.)

### ![🎯](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Wrap-Up Summay

function

→ old way, longer syntax

() => {}

→ modern way, cleaner and shorter

Use

return

only when using

{}

Arrow functions are perfect for short logic and callbacks

Quick Quiz

Ask them to answer in chat/verbally:

What symbol replaces the

function

keyword?

When can we skip

return

?

What’s wrong with this code?

const multiply = (a, b) => { a * b; }

​

## 4: Template Literals — Making Strings Easier and Prettier

### ![🎯](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Goal

The pain of string concatenation before ES6

How Template Literals (

``

) solve it elegantly

How to use interpolation (

${}

)

How to write multi-line and formatted strings

Through small relatable examples and fun mini-tasks

### ![🧠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) The String Struggle

Start with a simple example that looks familiar and annoying:

const name = "Riya"; const age = 21; console.log("Hello, my name is " + name + " and I am " + age + " years old.");

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Ask:

> “Can you spot what’s messy here?”

Expected responses:

So many

+

signs

Hard to read

Easy to forget spaces or quotes

### ![⚠️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Pain Point — Concatenation Confusion

Show a more complex example (bonus: line breaks).

const product = "Laptop"; const price = 55000; const message = "You bought a " + product + " for ₹" + price + ". Thank you for shopping!"; console.log(message);

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “This looks like a broken sentence. Imagine maintaining 10 such strings — nightmare!”

Then say:

> “Developers used to spend more time fixing quotes and spaces than writing logic. That’s why ES6 gave us a better way…”

### ![🌟](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) ES6 Solution — Template Literals

Syntax:

Use backticks (

`

), not single ('') or double ("") quotes.

Use

${variable}

to insert variables inside strings.

#### Example 1 — Cleaner Interpolation

const name = "Riya"; const age = 21; console.log(`Hello, my name is ${name} and I am ${age} years old.`);

​

Output:

Hello, my name is Riya and I am 21 years old.

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “No more

+

signs, no broken quotes, no mental math — it reads like English!”

#### Example 2 — Multi-Line Strings (Before vs After)

Before ES6:

const text = "Dear Student,\n" + "Welcome to the JavaScript workshop!\n" + "Let's have some fun!";

​

With Template Literals:

const text = `Dear Student, Welcome to the JavaScript workshop! Let's have some fun!`; console.log(text);

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “Notice? We can write multi-line text exactly how we want it to appear!”

#### Example 3 — Embedding Expressions

const a = 5, b = 3; console.log(`The sum of ${a} and ${b} is ${a + b}`);

​

![✅](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Output:

The sum of 5 and 3 is 8

​

![🧠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “We can even run JS expressions inside

${}

— not just variables.”

### ![💡](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) When to Use Template Literals

|Old Way|ES6 Template Literal|
|---|---|
|String concatenation|Dynamic messages|
|Multi-line emails, alerts|Readable templates|
|Logging variables|Inline math or expressions|

### ![🎮](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Practice Tasks

#### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Task 1 — Convert Old Strings to Template Literals

const user = "Aman"; const points = 120; const message = "Hey " + user + ", you have " + points + " points!"; console.log(message);

​

![➡️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Convert to:

const message = `Hey ${user}, you have ${points} points!`;

​

#### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Task 2 — Multi-line Message

Ask them to create:

> “A 3-line welcome message for new players in your game.”

Example Output:

Welcome, Player! Get ready for your first challenge. Collect 5 coins to win.

​

Expected Code:

const player = "Riya"; const message = ` Welcome, ${player}! Get ready for your first challenge. Collect 5 coins to win. `; console.log(message);

​

#### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Task 3 — Expression Challenge

Give this:

const item = "Book"; const price = 299; const quantity = 3; // Write a message showing total price using template literals

​

![✅](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Expected:

const total = price * quantity; const message = `You bought ${quantity} ${item}s for ₹${total}.`; console.log(message);

​

### ![🎯](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Wrap-Up Summary

Key takeaways:

Use backticks (

`

), not quotes

${}

lets you embed variables and expressions

Supports multi-line strings

Cleaner, readable, and professional code

Quick Quiz (3 mins):

Ask them:

Which symbol do we use for template literals?

What happens if we use single quotes with

${}

?

Can we write multi-line strings using template literals?

![✅](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) (Answers: backticks, won’t interpolate, yes!)

## 5: Understanding JavaScript Objects

### ![🎯](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Goal

What objects are and why we use them

How to create, access, and modify object properties

How to add methods (functions inside objects)

The difference between

.

and

[]

access

Through relatable examples and easy practice tasks

> “So far, we’ve stored small pieces of information — like name, age, or score — in separate variables.
> 
> But what if we want to keep all information about one person or thing together?”

#### Example

const name = "Riya"; const age = 20; const city = "Delhi";

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Ask:

> “If I have 100 students, will I make 300 variables? That’s messy! We need a better way.”

### What Is an Object?

Explain visually or with analogy:

> “An object is like a box that can hold multiple pieces of related information, each with a name tag.”

#### Example

const student = { name: "Riya", age: 20, city: "Delhi" };

​

![🧠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “Here,

student

is the box. Inside, we have properties like

name

,

age

, and

city

.”

### Accessing Object Properties

#### ![1️⃣](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Dot Notation

console.log(student.name); // "Riya" console.log(student.city); // "Delhi"

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “We use the dot when we know the exact property name.”

#### ![2️⃣](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Bracket Notation

console.log(student["age"]); // 20

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “Brackets are like saying ‘look up this property by its name (a string).’”

#### Example: Dynamic Property Access

const key = "city"; console.log(student[key]); // "Delhi"

​

> “This works when the property name is stored in a variable — dot notation won’t work there.”

### Adding & Updating Properties

student.email = "riya@example.com"; // add new property student.age = 21; // update existing property console.log(student);

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “Objects are flexible — you can add or change data anytime.”

### Deleting Properties

delete student.city; console.log(student);

​

> “You can remove a property using delete, though it’s rarely needed.”

### Methods — Functions Inside Objects

> “Objects can not only store data but also actions — functions that belong to them.
> 
> These functions are called methods.”

#### Example:

const student = { name: "Riya", age: 20, greet: function() { console.log("Hi! I'm " + this.name); } }; student.greet(); // "Hi! I'm Riya"

​

![🧠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “Here,

greet

is a method — an action the student can perform.”

Explain the

this

keyword lightly:

> “this means ‘the current object’ — so inside student.greet(), this.name means student.name.”

### Practice Tasks

#### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Task 1 — Create Your Own Object

> “Make an object for your favourite movie with at least 3 properties — title, year, and rating — and log it.”

Example:

const movie = { title: "Inception", year: 2010, rating: 8.8 }; console.log(movie.title); // Inception

​

#### Task 2 — Add a Method

> “Add a method describe() that prints something like:
> 
> Inception (2010) has a rating of 8.8
> 
> .”

Example:

movie.describe = function() { console.log(`${this.title} (${this.year}) has a rating of ${this.rating}`); }; movie.describe();

​

#### Task 3 — Access Properties Dynamically

> “Create a variable called key = "rating" and print the rating using that variable.”

Example:

const key = "rating"; console.log(movie[key]); // 8.8

​

### ![🎯](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) 8. Wrap-Up Summary

|Concept|Explanation|
|---|---|
|Object|A collection of key–value pairs|
|Property|A variable inside an object|
|Method|A function inside an object|
|Dot Notation|object.property<br><br>(known property name)|
|Bracket Notation|object["property"]<br><br>(dynamic property name)|
|this|Refers to the current object|

Transition Line:

> “Now that we can store and access complex data using objects, ES6 introduced a super cool way to extract or combine that data easily — called Destructuring and Spread/Rest Operators. Let’s learn those next!”

## 6: Destructuring, Spread & Rest Operators — Smarter Data Handling

### ![🎯](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Goal

Extract values from arrays/objects easily using destructuring

Copy and merge arrays/objects using the spread operator (

...

)

Handle multiple parameters or leftover data using the rest operator (

...

)

Understand how these features made JS code cleaner and more readable compared to ES5.

### Problem Before ES6

Start with a relatable scenario:

> “Let’s say we have a student object and we want to access its values.”

#### Example — Before ES6:

const student = { name: "Riya", age: 20, city: "Delhi" }; const name = student.name; const age = student.age; const city = student.city; console.log(name, age, city);

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “That’s a lot of repetition! Imagine doing this for 10 properties or multiple objects.”

> “ES6 introduced a shortcut — Destructuring — to grab values easily.”

### Object Destructuring

#### Syntax:

const { name, age, city } = student; console.log(name, age, city);

​

![🧠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “This automatically creates variables

name

,

age

, and

city

from the object.”

Explain:

Left side

{}

matches object structure

Order doesn’t matter (it’s based on property names)

#### ![✅](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Example Practice

const laptop = { brand: "Apple", model: "MacBook Air", price: 120000 }; const { brand, price } = laptop; console.log(`The ${brand} costs ₹${price}`);

​

Ask Students:

> “What if I only want to take one property?
> 
> Or rename a property while destructuring?”

#### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Bonus: Renaming

const { model: laptopModel } = laptop; console.log(laptopModel);

​

### Array Destructuring

> “Same idea, but now for arrays — order matters!”

#### Example:

const colors = ["red", "green", "blue"]; const [first, second, third] = colors; console.log(first, second, third);

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “Positions matter here, not names.”

#### Skipping values:

const [primary, , tertiary] = colors; console.log(primary, tertiary); // red blue

​

#### ![✅](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Quick Practice Task:

> Create an array fruits = ["apple", "banana", "mango"]
> 
> Destructure the first and third fruit into variables and log them.

### ![🌀](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Spread Operator — Copying & Merging

> “Before ES6, copying or merging arrays and objects was tricky — now it’s one line!”

#### ![📘](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Spread with Arrays

const fruits = ["apple", "banana"]; const moreFruits = [...fruits, "mango", "grapes"]; console.log(moreFruits);

​

![🧠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “

...

spreads the elements out — like unpacking the array.”

#### ![📘](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Spread with Objects

const student = { name: "Riya", age: 20 }; const updatedStudent = { ...student, city: "Delhi" }; console.log(updatedStudent);

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “Useful for cloning or adding new properties without changing the original.”

#### ![⚠️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Show ES5 Way (to contrast)

// Old way (clunky) const newFruits = fruits.concat(["mango", "grapes"]);

​

> “The spread operator made this easier, more readable, and less error-prone.”

### Rest Operator — Gathering Values (8 mins)

> “If spread unpacks, rest packs things up.”

#### Example 1 — In Arrays

const [first, ...others] = ["HTML", "CSS", "JS", "React"]; console.log(first); // "HTML" console.log(others); // ["CSS", "JS", "React"]

​

#### Example 2 — In Functions

function sum(...numbers) { console.log(numbers); } sum(1, 2, 3, 4); // [1, 2, 3, 4]

​

![🧠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “

...numbers

collects all arguments into an array — very handy!”

### Practice Tasks

#### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)Task 1 — Object Destructuring

const player = { name: "Virat", runs: 12000, team: "India" };

​

![👉](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Extract all properties and log

![👉](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Extract only

name

and

team

#### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Task 2 — Array Destructuring

const scores = [50, 80, 90, 100];

​

![👉](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Extract top 2 scores

![👉](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Store remaining scores in another array using rest (

...restScores

)

#### Task 3 — Spread Operator

const arr1 = [1, 2, 3]; const arr2 = [4, 5];

​

![👉](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Merge them into

allNumbers

using spread

![👉](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Add one more number at the end

#### Task 4 — Rest Operator in Function

> Create a function multiplyAll(...nums) that multiplies all numbers passed to it.

function multiplyAll(...nums) { return nums.reduce((acc, n) => acc * n, 1); } console.log(multiplyAll(2, 3, 4)); // 24

​

### ![🎯](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Summary Recap Table

|Feature|Symbol|Purpose|Example|
|---|---|---|---|
|Destructuring|{}<br><br>/<br><br>[]|Extract values easily|const {name} = obj|
|Spread|...|Copy or merge|[...arr1, ...arr2]|
|Rest|...|Gather multiple values|function sum(...nums)|

### ![🎓](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Wrap-Up:

> “With destructuring, spread, and rest — ES6 gave JavaScript a powerful, cleaner way to handle data.
> 
> Next, we’ll learn how ES6 made objects themselves smarter — with Enhanced Object Literals.”

## 7: Enhanced Object Literals — Writing Cleaner Objects in ES

### ![🎯](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Goal

Understand what Enhanced Object Literals are

Learn how ES6 made object creation shorter & more expressive

Use property shorthand, method shorthand, and computed property names

Refactor old-style objects into clean ES6-style code

### Objects Before ES6

> “Before ES6, writing objects could get repetitive — especially when property names matched variable names.”

#### Example (Pre-ES6):

const name = "Riya"; const age = 20; const city = "Delhi"; const student = { name: name, age: age, city: city, greet: function() { console.log("Hi! I'm " + this.name); } };

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “Notice how we’re repeating ourselves?

name: name

,

age: age

— feels redundant, right?”

### ![✨](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Property Shorthand

> “If your property name and variable name are the same, ES6 lets you skip the duplication.”

#### Example:

const name = "Riya"; const age = 20; const city = "Delhi"; const student = { name, age, city }; console.log(student);

​

![🧠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “Here, JavaScript automatically assumes

name: name

,

age: age

, etc.”

#### ![✅](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Practice Task 1

const brand = "Apple"; const model = "iPhone 16"; const price = 80000; // create a phone object using shorthand

​

Expected Output:

{ brand: 'Apple', model: 'iPhone 16', price: 80000 }

​

### ![⚙️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Method Shorthand

> “Before ES6, we had to write methods like greet: function() {...}.
> 
> Now, ES6 lets us skip the word
> 
> function
> 
> .”

#### Example:

const student = { name: "Riya", greet() { console.log("Hi! I'm " + this.name); } }; student.greet(); // "Hi! I'm Riya"

​

![🧠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Cleaner and shorter — no need for the

function

keyword inside objects.

#### ![✅](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Practice Task 2

Create an object

car

:

const car = { brand: "Tesla", model: "Model 3", start() { console.log(`${this.brand} ${this.model} is starting...`); } }; car.start();

​

### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Combine All Three Features

> “Let’s combine shorthand properties, shorthand methods, and computed property names!”

#### Example:

const name = "Virat"; const runs = 12000; const player = { name, runs, average: 56.2, showStats() { console.log(`${this.name} has scored ${this.runs} runs with an average of ${this.average}`); } }; player.showStats();

​

![🧠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “See how clean that looks?

This is what Enhanced Object Literals mean — shorter, smarter, and easier to read.”

### ![🧭](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Summary

|Feature|What It Does|Example|
|---|---|---|
|Property Shorthand|Skip repeating variable names|{ name, age }<br><br>instead of<br><br>{ name: name, age: age }|
|Method Shorthand|Skip<br><br>function<br><br>keyword|greet() { ... }|
|Computed Property Names|Use dynamic keys|{ [key]: value }|

### ![🎓](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Wrap-Up :

> “With these shortcuts, ES6 made object creation clean and expressive — no more clutter!
> 
> Now that we’ve made objects smarter, let’s learn how ES6 also made asynchronous JavaScript easier — using Promises.”

## 8: Asynchronous JavaScript & Promises

Goal: Understand what “asynchronous” means in JavaScript, learn

setTimeout

,

setInterval

, and how Promises solved callback chaos.

### ![🎯](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Learning Outcomes

Use

setTimeout()

and

setInterval()

confidently

Understand why callbacks caused problems

Learn how Promises make asynchronous code easier and cleaner

### ![🧠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) 1. Start With a Story

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “Imagine you’re cooking maggi ![🍜](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) — you boil water, then add noodles, and while it cooks, you chop vegetables.”

> “You don’t wait staring at the pot for 2 minutes — you multitask.”

That’s asynchronous behavior — doing one thing while waiting for another.

### ![🕰️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) 2. Synchronous vs Asynchronous

Explain visually or step by step:

#### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Synchronous Example

console.log("Task 1"); console.log("Task 2"); console.log("Task 3");

​

![🧠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “Here, JS runs one line at a time — top to bottom.”

Output:

Task 1 Task 2 Task 3

​

#### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Asynchronous Example

console.log("Task 1"); setTimeout(() => { console.log("Task 2"); }, 2000); console.log("Task 3");

​

Output:

Task 1 Task 3 Task 2

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “See that?

Task 2

waited for 2 seconds while the rest of the code continued.”

> “That’s asynchronous behavior — code that runs later, without blocking the rest.”

### ![⏰](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) 3. setTimeout() — Do Something After Some Time

#### Syntax

setTimeout(callback, delayInMs);

​

#### Example

console.log("Hello!"); setTimeout(() => { console.log("Welcome to JS after 3 seconds!"); }, 3000); console.log("Program Ended");

​

![🧠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “JS sets a timer for 3 seconds, continues running other code, and when the time’s up, it calls back the function.”

#### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Practice Task 1:

> “Show 3 messages one after another with a delay between each using multiple setTimeouts.”

setTimeout(() => console.log("3..."), 1000); setTimeout(() => console.log("2..."), 2000); setTimeout(() => console.log("1..."), 3000); setTimeout(() => console.log("Go!"), 4000);

​

### ![⏱️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) 4. setInterval() — Repeat Something

#### Syntax

setInterval(callback, intervalInMs);

​

#### Example:

let count = 1; const timer = setInterval(() => { console.log("Hello " + count); count++; if (count > 5) clearInterval(timer); // stops after 5 times }, 1000);

​

![🧠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “It repeats every second until you stop it with

clearInterval()

.”

#### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Practice Task 2:

> “Make a countdown timer from 10 to 1 using setInterval() and stop it when it hits 0.”

### ![🌀](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) 5. The Callback Problem

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “Now imagine you want to do something after something after something. You might write nested callbacks — this is called callback hell.”

#### Example:

setTimeout(() => { console.log("Step 1"); setTimeout(() => { console.log("Step 2"); setTimeout(() => { console.log("Step 3"); }, 1000); }, 1000); }, 1000);

​

![🧠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “Works fine for small tasks, but for real projects, this becomes unreadable fast.”

> “That’s why ES6 introduced Promises — to make async code more readable and manageable.”

### ![🌈](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Promises — The ES6 Fix

#### ![💬](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) What Is a Promise?

> “A Promise is like a container for a value that will be available in the future — either success or failure.”

> “You can ‘promise’ to do something and let JS know what to do when it’s done.”

#### Basic Structure:

const myPromise = new Promise((resolve, reject) => { const success = true; if (success) { resolve("Task completed!"); } else { reject("Something went wrong!"); } }); myPromise .then((message) => console.log("Success:", message)) .catch((error) => console.log("Error:", error));

​

![🧠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==)

.then()

runs when it’s successful

.catch()

runs if there’s an error

#### ![✅](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Example: Using Promise with setTimeout

const wait = new Promise((resolve) => { setTimeout(() => { resolve("3 seconds later..."); }, 3000); }); wait.then((msg) => console.log(msg));

​

![🗣️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) “This looks much cleaner than nested callbacks!”

#### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Practice Task 3:

> “Create a function makeTea() that returns a Promise:
> 
> After 2 seconds, it should
> 
> resolve("Tea is ready!")
> 
> .
> 
> Then print it using
> 
> .then()
> 
> .”

![✅](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Example:

function makeTea() { return new Promise((resolve) => { setTimeout(() => { resolve("☕ Tea is ready!"); }, 2000); }); } makeTea().then((msg) => console.log(msg));