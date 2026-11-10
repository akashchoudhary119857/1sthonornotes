# Events In Detail

## 🧩 1. What is an Event?

An **event** is something that happens in your webpage —

like clicking, typing, scrolling, or submitting a form.

Think of events as _notifications from the browser saying: “Hey! The user did something!”_

Examples of common events:

|Category|Examples|
|---|---|
|Mouse|click, dblclick, mouseover, mouseout, mousedown, mouseup, mousemove|
|Keyboard|keydown, keyup, keypress (deprecated)|
|Form|input, change, submit, focus, blur|
|Window|load, resize, scroll|
|Clipboard|copy, cut, paste|
|Drag & Drop|dragstart, dragover, drop|
|Touch|touchstart, touchmove, touchend|
|Custom|your own events created with `CustomEvent()`|

---

## 🎮 2. How to Listen to an Event

### 💥 Using `addEventListener()`

```jsx
element.addEventListener("eventType", function(event) {
  // do something when event occurs
});

```

---

### 🧪 Example:

```html
<button id="btn">Click me!</button>

<script>
  const btn = document.getElementById('btn');
  btn.addEventListener('click', function() {
    alert('You clicked me!');
  });
</script>

```

**💡 Output:**

When you click the button, an alert pops up saying _“You clicked me!”_

---

### 🎯 Task 1:

Make a `<button>` that changes its background color every time you click it.

Hint: use `Math.random()` and template literals for random color generation.

---

## 🖱️ 3. Mouse Events

### Common mouse events:

|Event|Trigger|
|---|---|
|click|when user clicks (down + up)|
|dblclick|double-click|
|mousedown|mouse button pressed|
|mouseup|mouse button released|
|mouseover|pointer enters element|
|mouseout|pointer leaves element|
|mousemove|pointer moves within element|

---

### 💥 Example: “The Curious Circle”

```html
<div id="circle" style="
  width:100px; height:100px;
  border-radius:50%; background:skyblue;
  margin:50px auto; transition:0.3s;">
</div>

<script>
const circle = document.getElementById('circle');

circle.addEventListener('mouseover', () => {
  circle.style.background = 'orange';
  circle.style.transform = 'scale(1.2)';
});

circle.addEventListener('mouseout', () => {
  circle.style.background = 'skyblue';
  circle.style.transform = 'scale(1)';
});

circle.addEventListener('click', () => {
  circle.style.background = 'lime';
});
</script>

```

**💡 Output:**

Hover → circle turns orange

Click → circle turns lime

Leave → back to skyblue

---

### 🎯 Task 2:

Create a "Dancing Box" that moves 10px right each time you double-click it.

Use `dblclick` and `style.marginLeft`.

---

## ⌨️ 4. Keyboard Events

### Common keyboard events:

|Event|Trigger|
|---|---|
|keydown|key is pressed down|
|keyup|key is released|
|keypress|key pressed (deprecated; use keydown)|

---

### 💥 Example: “Move the Emoji”

```html
<div id="emoji" style="font-size:60px; position:absolute; top:100px; left:100px;">😎</div>

<script>
let x = 100, y = 100;
const emoji = document.getElementById('emoji');

document.addEventListener('keydown', e => {
  if (e.key === 'ArrowUp') y -= 20;
  if (e.key === 'ArrowDown') y += 20;
  if (e.key === 'ArrowLeft') x -= 20;
  if (e.key === 'ArrowRight') x += 20;
  emoji.style.top = y + 'px';
  emoji.style.left = x + 'px';
});
</script>

```

**💡 Output:**

Use arrow keys → the emoji moves around!

---

### 🎯 Task 3:

Make a “Typewriter Effect”:

- Create an empty `<p>` tag.
    
- Each time the user types a key, append that key to the `<p>` text.
    
    Hint: use `e.key` in the `keydown` event.
    

---

## 🧾 5. Form Events

### Common form events:

|Event|Trigger|
|---|---|
|input|value changes (live)|
|change|value changes (on blur)|
|submit|form submitted|
|focus|element gains focus|
|blur|element loses focus|

---

### 💥 Example: “Live Typing Preview”

```html
<input id="name" placeholder="Type your name" />
<p id="output"></p>

<script>
const input = document.getElementById('name');
const output = document.getElementById('output');

input.addEventListener('input', e => {
  output.textContent = `Hello, ${e.target.value || 'stranger'}!`;
});
</script>

```

**💡 Output:**

As you type, the paragraph updates live.

---

### 🎯 Task 4:

Make a simple form:

- Input for email
    
- “Submit” button
    
- When submitted, show “Welcome, [email]!” below
    
    Use `preventDefault()` to stop page reload.
    

---

## 🪟 6. Window & Document Events

### Common ones:

|Event|Trigger|
|---|---|
|load|when page fully loads|
|resize|window resized|
|scroll|user scrolls|
|beforeunload|user tries to leave|
|DOMContentLoaded|DOM ready (faster than `load`)|

---

### 💥 Example: “Scroll Progress Bar”

```html
<div id="progress" style="position:fixed;top:0;left:0;height:5px;background:blue;width:0;"></div>

<script>
window.addEventListener('scroll', () => {
  const scrollTop = window.scrollY;
  const docHeight = document.body.scrollHeight - window.innerHeight;
  const scrolled = (scrollTop / docHeight) * 100;
  document.getElementById('progress').style.width = scrolled + '%';
});
</script>

```

**💡 Output:**

A progress bar shows how far you’ve scrolled down the page.

---

### 🎯 Task 5:

Add an event listener to `resize` that logs the current window size each time you resize it.

---

## 🖋️ 7. Clipboard Events

|Event|Trigger|
|---|---|
|copy|when user copies text|
|cut|when user cuts|
|paste|when user pastes|

---

### 💥 Example: “Clipboard Police”

```html
<p id="text">Copy me if you dare...</p>

<script>
const text = document.getElementById('text');
text.addEventListener('copy', e => {
  e.preventDefault();
  alert('No copying allowed 😤');
});
</script>

```

**💡 Output:**

Try copying → browser stops it and warns you.

---

### 🎯 Task 6:

Allow paste into an input but automatically transform it to **uppercase**.

Hint: use `paste` + `e.clipboardData.getData('text')`.

---

## 🧲 8. Drag & Drop Events

|Event|Trigger|
|---|---|
|dragstart|dragging begins|
|dragover|dragging over target|
|drop|released on target|
|dragend|drag ends|

---

### 💥 Example: “Drag the Emoji into the Box”

```html
<div id="dropzone" style="width:150px;height:150px;border:2px dashed gray;text-align:center;line-height:150px;">
Drop here
</div>
<div id="emoji" draggable="true" style="font-size:50px;cursor:grab;">🐱‍👤</div>

<script>
const drop = document.getElementById('dropzone');
const emoji = document.getElementById('emoji');

drop.addEventListener('dragover', e => e.preventDefault());

drop.addEventListener('drop', e => {
  e.preventDefault();
  drop.textContent = "Nice drop!";
  emoji.remove();
});
</script>

```

**💡 Output:**

Drag the emoji → drop it into the box → “Nice drop!”

---

### 🎯 Task 7:

Make two boxes (“To Do” and “Done”) and drag items between them.

---

## 🧠 9. Event Object Deep Dive

Whenever an event fires, a special **event object** is passed to your handler:

```jsx
element.addEventListener('click', function(event) {
  console.log(event.type); // "click"
  console.log(event.target); // element clicked
});

```

### Important properties:

|Property|Description|
|---|---|
|`type`|Type of event (“click”, “keydown”)|
|`target`|Element that triggered event|
|`currentTarget`|Element whose listener is running|
|`key`|Key pressed (for keyboard events)|
|`clientX`, `clientY`|Mouse pointer position|
|`ctrlKey`, `altKey`, `shiftKey`|Modifier keys|
|`preventDefault()`|Stops default behavior|
|`stopPropagation()`|Stops bubbling|

---

### 💥 Example: “Mouse Tracker”

```html
<div id="board" style="height:200px;border:2px solid black"></div>
<p id="coords"></p>

<script>
const board = document.getElementById('board');
const coords = document.getElementById('coords');

board.addEventListener('mousemove', e => {
  coords.textContent = `X: ${e.clientX}, Y: ${e.clientY}`;
});
</script>

```

**💡 Output:**

Move the mouse inside → coordinates update live.

---

### 🎯 Task 8:

Show an alert only if `Alt` key was held during a click event.

Hint: use `e.altKey`.

---

## 🪄 10. Event Bubbling & Capturing

When you click a child inside nested elements:

1. The event goes **down** (capture phase)
2. Reaches target
3. Then **bubbles up** (bubble phase)

---

### 💥 Example:

```html
<div id="outer" style="padding:40px;background:#f88;">
  Outer
  <div id="inner" style="padding:40px;background:#8f8;">Inner</div>
</div>

<script>
document.getElementById('outer').addEventListener('click', () => console.log('Outer bubble'));
document.getElementById('inner').addEventListener('click', () => console.log('Inner bubble'));
document.getElementById('outer').addEventListener('click', () => console.log('Outer capture'), true); 
</script>

```

**💡 Output order:**

Outer capture → Inner bubble → Outer bubble

---

### 🎯 Task 9:

Create three nested divs (red, green, blue).

Log messages in both capture and bubble phases and analyze the order.

---

## 🎯 11. `preventDefault()` & `stopPropagation()`

### 💥 Example:

```html
<a id="link" href="<https://google.com>">Go to Google</a>
<div id="parent">
  <button id="child">Click me!</button>
</div>

<script>
document.getElementById('link').addEventListener('click', e => {
  e.preventDefault();
  alert("No redirecting today!");
});

document.getElementById('parent').addEventListener('click', () => alert('Parent clicked!'));
document.getElementById('child').addEventListener('click', e => {
  e.stopPropagation();
  alert('Child only!');
});
</script>

```

---

### 🎯 Task 10:

Make a nested set of buttons.

- Inner one shows “Child Clicked!”
- Outer shows “Parent Clicked!”
- Stop propagation so only one fires.

---

## 🧩 12. Event Delegation

Attach one listener to a parent — handle all children dynamically.

### 💥 Example: “Dynamic List”

```html
<ul id="list">
  <li>🍎 Apple</li>
  <li>🍌 Banana</li>
  <li>🍇 Grapes</li>
</ul>

<script>
document.getElementById('list').addEventListener('click', e => {
  if (e.target.tagName === 'LI') {
    e.target.style.textDecoration = 'line-through';
  }
});
</script>

```

**💡 Output:**

Click any list item → it gets crossed off!

---

### 🎯 Task 11:

Create a `<ul>` with “Add” and “Delete” buttons for each item using delegation so new items also work.

---

## 🧠 13. Custom Events

### 💥 Example:

```jsx
const box = document.createElement('div');
box.textContent = 'Box';
box.style = 'width:100px;height:100px;background:skyblue;';
document.body.appendChild(box);

box.addEventListener('powerUp', e => alert(`Power level: ${e.detail.level}`));

box.dispatchEvent(new CustomEvent('powerUp', {detail:{level:9000}}));

```

**💡 Output:**

Alert says “Power level: 9000”

---

---

# EVENT FLOW — Capturing → Target → Bubbling

When you click (or trigger any event) inside nested HTML elements,

the event **doesn’t just fire once** — it travels through **three phases**:

### 🧩 Example structure

```html
<div id="grandparent">
  <div id="parent">
    <div id="child">Click Me</div>
  </div>
</div>

```

---

## 📜 Phase 1: Capturing (a.k.a. trickling down)

The event starts from the **top (window/document)** and travels **down the DOM tree**

until it reaches the target element.

If you register a listener with `{capture: true}`, it will run **during this phase**.

---

## 🎯 Phase 2: Target

When the event reaches the actual element that triggered it (e.g. the `child` div),

its **target phase** executes. Handlers attached directly to that element fire here.

---

## ⬆️ Phase 3: Bubbling (default)

After reaching the target, the event **bubbles up** — traveling _back up_ the DOM tree.

Handlers attached without `capture:true` fire during this **bubbling** phase.

---

## 🧠 Analogy:

Think of it like **throwing a stone in water**:

- The ripple spreads outward (capture phase — top → down),
- Hits the center (target),
- Then waves come back outward (bubbling phase — bottom → up).

---

## 🧩 Example: Observe Capturing vs Bubbling

```html
<style>
div { padding: 20px; border: 2px solid; margin: 10px; cursor: pointer; }
#grandparent { border-color: red; }
#parent { border-color: green; }
#child { border-color: blue; }
</style>

<div id="grandparent">Grandparent
  <div id="parent">Parent
    <div id="child">Child</div>
  </div>
</div>

<script>
const log = (msg) => console.log(msg);

grandparent.addEventListener('click', () => log('Grandparent (capture)'), true);
parent.addEventListener('click', () => log('Parent (capture)'), true);
child.addEventListener('click', () => log('Child (capture)'), true);

grandparent.addEventListener('click', () => log('Grandparent (bubble)'));
parent.addEventListener('click', () => log('Parent (bubble)'));
child.addEventListener('click', () => log('Child (bubble)'));
</script>

```

### 💡 Output when clicking the **child**:

```
Grandparent (capture)
Parent (capture)
Child (capture)
Child (bubble)
Parent (bubble)
Grandparent (bubble)

```

---

### 🎯 **Task 1: Visualize**

Add `backgroundColor` changes in each phase:

- Red for capturing,
    
- Blue for bubbling.
    
    Reset colors after 1s.
    
    You’ll _see_ the flow happen visually.
    

---

# ⚙️ `e.preventDefault()` — Stopping Default Browser Behavior

---

### 💡 Definition:

`event.preventDefault()` **prevents the browser’s default action** for that event.

**It does NOT stop the event from bubbling or capturing** —

it only stops the **browser’s automatic behavior** that normally happens.

---

### 🧾 Common Default Behaviors It Can Stop:

|Element|Event|Default Action|
|---|---|---|
|`<a href="...">`|click|Navigates to URL|
|`<form>`|submit|Reloads the page|
|`<input type="checkbox">`|click|Toggles checked state|
|`<input type="text">`|keydown|Inserts text|
|`<contextmenu>`|right-click|Opens context menu|
|`<drag>`|dragstart|Starts drag operation|
|`<scroll>`|wheel|Scrolls page|
|`<textarea>`|keydown + Enter|Creates new line|

---

### 💥 Example 1: Stop Link Navigation

```html
<a href="<https://google.com>" id="link">Go to Google</a>

<script>
document.getElementById('link').addEventListener('click', e => {
  e.preventDefault();
  alert("Navigation stopped!");
});
</script>

```

**💡 Output:**

When you click the link → it doesn’t navigate. Instead, it shows an alert.

---

### 💥 Example 2: Prevent Form Reload

```html
<form id="myForm">
  <input placeholder="Your name" required />
  <button type="submit">Submit</button>
</form>

<script>
myForm.addEventListener('submit', e => {
  e.preventDefault(); // stops reload
  alert('Form submitted without reload!');
});
</script>

```

**💡 Output:**

You’ll see an alert but the page doesn’t reload — form submission prevented.

---

### 🎯 **Task 2: Creative Prevent Default**

Create a form with:

- A checkbox “I agree to terms”
- A submit button

Prevent submission unless the checkbox is checked.

Use `preventDefault()` to stop the form and show a warning.

---

# 🛑 `event.stopPropagation()` — Stop Event from Bubbling/Capturing Further

---

### 💡 Definition:

`e.stopPropagation()` prevents the event from **traveling further** in the event flow.

- If called during **bubbling**, it stops the event from reaching **ancestors**.
- If called during **capturing**, it stops it from reaching **descendants**.
- The event still executes _other handlers_ on the same element (use `stopImmediatePropagation()` to stop those too).

---

### 💥 Example 1: Stop Bubbling Up

```html
<div id="outer" style="padding:20px; background:lightcoral">
  Outer
  <button id="inner">Click Me</button>
</div>

<script>
document.getElementById('outer').addEventListener('click', () => {
  alert('Outer clicked!');
});

document.getElementById('inner').addEventListener('click', e => {
  e.stopPropagation();
  alert('Inner clicked only!');
});
</script>

```

**💡 Output:**

When you click the **button**, only “Inner clicked!” shows — the outer handler doesn’t fire.

---

### 💥 Example 2: Capturing Stop

```jsx
parent.addEventListener('click', e => {
  e.stopPropagation();
  console.log('Stopped at parent during capture!');
}, true);

```

This prevents event from going down further to children.

---

### 🎯 **Task 3: Color Game**

Three nested boxes:

- Red (outer), green (middle), blue (inner).
    
    Each on click:
    
- Logs its color name.
    
    When inner box clicked → stop propagation.
    
    Expected: only “Blue clicked!” logs.
    

---

## 🧩 `stopImmediatePropagation()`

Stops:

1. Other listeners on the _same element_, and
2. The event from continuing to ancestors.

```jsx
button.addEventListener('click', e => {
  e.stopImmediatePropagation();
  console.log('First handler');
});
button.addEventListener('click', () => console.log('Second handler'));

```

**💡 Output:**

Only “First handler” appears.

---

# ⚡ Summary Cheat Sheet

|Method|Purpose|Stops Bubbling?|Stops Default Behavior?|
|---|---|---|---|
|`preventDefault()`|Prevents browser’s native behavior (like link navigation, form submit)|❌|✅|
|`stopPropagation()`|Stops event from traveling further up or down the DOM|✅|❌|
|`stopImmediatePropagation()`|Stops other handlers on same element + bubbling|✅✅|❌|

---

# 🧠 Complete Example: “Click Control Lab”

```html
<style>
div { padding:20px; border:2px solid black; margin:10px; cursor:pointer; }
#outer { background: #f88; }
#middle { background: #8f8; }
#inner { background: #88f; }
</style>

<div id="outer">Outer
  <div id="middle">Middle
    <div id="inner">Inner</div>
  </div>
</div>

<a href="<https://example.com>" id="link">Go to Example.com</a>

<script>
outer.addEventListener('click', () => console.log('Outer clicked!'));
middle.addEventListener('click', () => console.log('Middle clicked!'));
inner.addEventListener('click', e => {
  e.stopPropagation();
  console.log('Inner clicked only!');
});

link.addEventListener('click', e => {
  e.preventDefault();
  console.log('Navigation prevented!');
});
</script>

```

### 🧩 Try:

1. Click the inner div → only “Inner clicked!” logs.
2. Click middle → “Middle” then “Outer” logs.
3. Click the link → no navigation happens.

---

# 💬 Fun Analogy Recap

- **Capturing:** A message passed _down the chain of command_.
- **Bubbling:** The reply bubbles _back up_.
- **preventDefault():** “Don’t perform your usual duty!”
- **stopPropagation():** “Don’t tell anyone else about this!”