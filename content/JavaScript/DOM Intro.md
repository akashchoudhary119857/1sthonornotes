# Introduction to DOM

## ![🌐](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) JavaScript DOM (Document Object Model)

![](https://www.notion.so/image/attachment%3A22ffb506-c8b4-4d56-b578-43a598bb5b8e%3Aimage.png?table=block&id=2a10ff2a-cf3b-80e5-869d-e06548d0fc7a&spaceId=44e5511d-13d9-4d27-a2a2-02dd31b923e5&width=1060&userId=&cache=v2)

### ![🧠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) 1. What is the DOM?

DOM (Document Object Model) is a programming interface that represents the HTML structure of a webpage as a tree of objects.

![👉](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) It allows JavaScript to interact with, manipulate, and change the structure, style, and content of a webpage dynamically.

In simple terms:

> The DOM turns your HTML into a live object that JavaScript can modify.

Example:

HTML

<h1 id="title">Hello World</h1>

​

JS

document.getElementById("title").textContent = "Welcome to DOM!";

​

### ![🌳](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) 2. DOM Tree Structure

Every HTML page becomes a hierarchical tree of nodes.

Example:

<html> <body> <h1>Hello</h1> <p>Welcome!</p> </body> </html>

​

Visual DOM Tree:

Document └── html └── body ├── h1 └── p

​

Everything inside the DOM is a “node”:

Document Node →

document

Element Node →

<h1>

,

<p>

, etc.

Text Node → text inside an element

Attribute Node → attributes like

id

,

class

### ![📜](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) 3. Accessing DOM Elements

We can select elements in multiple ways:

#### ![✅](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) a) By ID

const title = document.getElementById("title");

​

#### ![✅](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) b) By Class

const items = document.getElementsByClassName("list-item");

​

#### ![✅](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) c) By Tag Name

const paras = document.getElementsByTagName("p");

​

#### ![✅](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) d) Using Query Selectors (Modern & Preferred)

const heading = document.querySelector("h1"); // first match const allParas = document.querySelectorAll("p"); // all matches

​

### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) 4. Manipulating Content

Once selected, you can read or modify content:

#### ![🔹](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) textContent

document.getElementById("title").textContent = "DOM Updated!";

​

#### ![🔹](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) intertext

element.innerText = "Visible text only";

​

#### ![🔹](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) innerHTML

document.querySelector("#container").innerHTML = "<h2>New HTML added</h2>";

​

![👉](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Use

.innerHTML

carefully — it can re-render or introduce security issues (XSS).

### ![🎨](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) 5. Manipulating Styles

You can modify CSS directly via

.style

:

const box = document.querySelector(".box"); box.style.backgroundColor = "lightblue"; box.style.padding = "20px";

​

Or add/remove CSS classes dynamically:

box.classList.add("active"); box.classList.remove("hidden"); box.classList.toggle("highlight");

​

### ![🧱](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) 6. Working with Attributes

<img id="photo" src="old.png" alt="photo" />

​

JS:

const img = document.getElementById("photo"); console.log(img.getAttribute("src")); // "old.png" img.setAttribute("src", "new.png"); img.removeAttribute("alt");

​

### ![🪄](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) 7. Creating and Removing Elements

#### ![🔹](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Creating

const newDiv = document.createElement("div"); newDiv.textContent = "Hello from JS!"; document.body.appendChild(newDiv);

​

#### ![🔹](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Inserting Before / After

const list = document.querySelector("ul"); const item = document.createElement("li"); item.textContent = "New item"; list.appendChild(item); // adds at end // or list.insertBefore(item, list.firstChild); // adds at start

​

#### ![🔹](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Removing

item.remove(); // modern way // or list.removeChild(item);

​

### ![🔁](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) 8. Traversing the DOM

You can navigate through parent, child, and sibling nodes:

<div id="container"> <p class="text">Hello</p> </div>

​

JS:

const div = document.getElementById("container"); console.log(div.children); // HTMLCollection [p.text] console.log(div.firstElementChild); // <p class="text">Hello</p> console.log(div.parentElement); // <body>...</body> console.log(div.nextElementSibling); // next element

​

### ![⚡](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) 9. Events in the DOM

Events make pages interactive — they detect user actions like clicks, input, or keypresses.

#### Example:

<button id="btn">Click Me</button>

​

JS:

const btn = document.getElementById("btn"); btn.addEventListener("click", function() { alert("Button Clicked!"); });

​

#### Common Events

|Event|Description|
|---|---|
|click|Mouse click|
|mouseover|Mouse over an element|
|mouseout|Mouse leaves an element|
|keyup<br><br>/<br><br>keydown|Keyboard events|
|input|Value changed in input|
|submit|Form submission|

### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) 10. Event Object &

this

Every event listener automatically receives an event object:

btn.addEventListener("click", function(e) { console.log(e.target); // element clicked });

​

this

→ refers to the element that triggered the event.

### ![⚙️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) 11. Event Bubbling & Capturing

Events travel through the DOM in phases:

Capturing Phase (top → down)

Target Phase

Bubbling Phase (bottom → up)

Example:

<div id="parent"> <button id="child">Click</button> </div>

​

JS:

document.getElementById("parent").addEventListener("click", () => { console.log("Parent clicked"); }); document.getElementById("child").addEventListener("click", (e) => { console.log("Child clicked"); });

​

Clicking the child logs:

Child clicked Parent clicked

​

![👉](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) This is bubbling.

To stop it:

e.stopPropagation();

​

### ![🧠](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) 12. DOM vs BOM

|Feature|DOM|BOM|
|---|---|---|
|Full Form|Document Object Model|Browser Object Model|
|Focus|HTML elements|Browser environment|
|Example Objects|document<br><br>,<br><br>element|window<br><br>,<br><br>location<br><br>,<br><br>navigator<br><br>,<br><br>alert()|

Example:

// DOM document.body.style.background = "yellow"; // BOM window.alert("Hello!"); console.log(location.href);

​

### ![🧪](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) 13. Practice Tasks

#### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Task 1 — Change Background Color on Button Click

<button id="btn">Change Color</button> <script> const btn = document.getElementById("btn"); btn.addEventListener("click", () => { document.body.style.backgroundColor = `rgb(${Math.random()*255}, ${Math.random()*255}, ${Math.random()*255})`; }); </script>

​

#### ![🧩](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Task 2 — Create a List Dynamically from Array

<ul id="list"></ul> <script> const fruits = ["Apple", "Banana", "Cherry"]; const list = document.getElementById("list"); fruits.forEach(fruit => { const li = document.createElement("li"); li.textContent = fruit; list.appendChild(li); }); </script>