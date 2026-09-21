# 1. CSS **Transform**

---

### 🔹 What is Transform?

The `transform` property lets you visually manipulate an element — move, rotate, scale, skew, or a combination — **without disturbing the layout around it**.

Think of it as picking up the element and twisting, resizing, or moving it in 2D or 3D space.

---

### 🔹 Transform Functions

### 1. `translate(x, y)`

- Moves an element from its current position.
- `x` = left/right, `y` = up/down.

```css
.box {
  transform: translate(50px, 30px);
}

```

👉 Moves the box **50px right, 30px down**.

---

### 2. `rotate(angle)`

- Rotates the element around its center.
- Positive = clockwise, Negative = counter-clockwise.

```css
.box {
  transform: rotate(45deg);
}

```

👉 Rotates box **45 degrees clockwise**.

---

### 3. `scale(x, y)`

- Enlarges or shrinks the element.
- `1` = original size, `>1` = bigger, `<1` = smaller.

```css
.box {
  transform: scale(1.5, 0.5);
}

```

👉 **Wider (1.5×)** and **shorter (0.5×)**.

---

### 4. `skew(x-angle, y-angle)`

- Slants the element like pushing one side.

```css
.box {
  transform: skew(20deg, 10deg);
}

```

👉 Skews horizontally **20°** and vertically **10°**.

---

### 5. `matrix(a, b, c, d, e, f)` (Advanced)

- A single function combining all transformations (rarely used manually).
- If you are eager to learn you can have a look at this blog:

[Matrices and how to use them in CSS](https://medium.com/front-end-weekly/matrices-and-how-to-use-them-in-css-b946fbce4a26)

---

### 6. 3D Transforms

- `translateZ(…)`, `rotateY(…)`, `scaleZ(…)` → create 3D effects.
- Needs perspective for depth.

```css
.card {
  transform: rotateY(45deg);
}

```

---

✅ Example: Transform Playground

```html
<style>
.box {
  width: 100px;
  height: 100px;
  background: tomato;
  margin: 20px;
  display: inline-block;
  transition: transform 0.5s;
}

.box:hover {
  transform: rotate(45deg) scale(1.2);
}
</style>

<div class="box"></div>
<p>Hover the box → rotates + grows 🎉</p>

```

---

# 🌟 2. CSS **Transition**

### 🔹 What is Transition?

A **transition makes property changes smooth instead of instant**.

E.g. instead of a button suddenly turning red, it **fades** to red.

---

### 🔹 Syntax

```css
transition: property duration timing-function delay;

```

- **property** → which CSS property to animate (`color`, `background`, `transform`, `all`)
- **duration** → how long it takes (`0.5s`, `200ms`)
- **timing-function** → speed curve (`ease`, `linear`, `ease-in`, `ease-out`, `cubic-bezier`)
- **delay** → when it should start

---

### 🔹 Timing Functions Explained

- `ease` → starts slow, speeds up, slows down (default).
- `linear` → same speed throughout.
- `ease-in` → starts slow, ends fast.
- `ease-out` → starts fast, ends slow.
- `ease-in-out` → slow → fast → slow.
- `cubic-bezier(x1, y1, x2, y2)` → custom speed curve.

---

✅ Example: Button Hover

```html
<style>
button {
  padding: 10px 20px;
  background: steelblue;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;

  transition: background 0.3s ease, transform 0.2s ease-in-out;
}

button:hover {
  background: limegreen;
  transform: scale(1.1);
}
</style>

<button>Hover me</button>

```

👉 Button smoothly changes **color** and **size** when hovered.

---

# 🌟 3. CSS **Animation**

### 🔹 What is Animation?

Animations use `@keyframes` to define **multiple stages of change** (not just start & end).

Unlike transitions, animations **don’t need user interaction** — they can run automatically, loop, and have multiple steps.

---

### 🔹 Syntax

```css
@keyframes animationName {
  0% { property: value; }
  50% { property: value; }
  100% { property: value; }
}

.selector {
  animation: animationName duration timing-function delay iteration-count direction fill-mode;
}

```

---

### 🔹 Animation Properties

- **animation-name** → which keyframes to use.
- **animation-duration** → how long one cycle lasts.
- **animation-timing-function** → speed curve.
- **animation-delay** → when to start.
- **animation-iteration-count** → how many times (`1`, `infinite`).
- **animation-direction** → `normal`, `reverse`, `alternate` (forwards then backwards).
- **animation-fill-mode** → whether final state stays (`forwards`) or resets (`none`).

---

### 🔹 Examples

### 1. Spinning Square

```html
<style>
@keyframes spin {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

.square {
  width: 80px;
  height: 80px;
  background: dodgerblue;
  animation: spin 2s linear infinite;
}
</style>

<div class="square"></div>

```

👉 Spins continuously.

---

### 2. Bouncing Ball

```html
<style>
@keyframes bounce {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-100px); }
}

.ball {
  width: 50px;
  height: 50px;
  background: orange;
  border-radius: 50%;
  animation: bounce 1s ease-in-out infinite;
}
</style>

<div class="ball"></div>

```

👉 Ball moves up and down like bouncing.

---

### 3. Pulsing Heart ❤️

```html
<style>
@keyframes pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.2); }
}

.heart {
  font-size: 100px;
  color: red;
  animation: pulse 0.8s ease-in-out infinite;
}
</style>

<div class="heart">❤️</div>

```

👉 Heart grows/shrinks like it’s beating.

---

### 4. Typewriter Effect ✍️

```html
<style>
@keyframes typing {
  from { width: 0 }
  to { width: 100% }
}
@keyframes blink {
  50% { border-color: transparent; }
}

.typewriter {
  font-size: 1.5rem;
  font-family: monospace;
  white-space: nowrap;
  overflow: hidden;
  border-right: 3px solid black;
  width: 0;
  animation: typing 3s steps(20) forwards, blink 0.7s step-end infinite;
}
</style>

<p class="typewriter">Hello, I’m learning CSS 🎉</p>

```

👉 Text appears letter by letter.

---

## 🌟 4. Transition vs Animation vs Transform (Comparison)

|Feature|Transform|Transition|Animation|
|---|---|---|---|
|Purpose|Change element visually (move, scale, rotate, skew)|Smoothly change between states|Create continuous or multi-step changes|
|Trigger|Immediate|Needs event (hover/click/focus)|Runs automatically or loops|
|Stages|One-time effect|Start → End|Multiple stages (0%, 50%, 100%)|
|Example|Rotate box|Button hover effect|Bouncing ball|

---

## 🌟 5. Best Practices

✅ Use **transform + transition** for small UI interactions (buttons, menus, hover effects).

✅ Use **animations** for larger, continuous effects (loaders, banners, bounce).

✅ Keep durations short for responsiveness (`0.2s–0.5s` typical for UI).

✅ Avoid animating properties like `width`, `left`, `top` → prefer `transform` for better performance.

✅ Use `will-change: transform;` if heavy animations affect performance.