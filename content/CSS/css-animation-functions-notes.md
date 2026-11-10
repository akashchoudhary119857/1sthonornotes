# CSS Animation Functions — Beginner to Intermediate Notes

## Learning objectives

- Explain the difference between CSS transitions, animations, and timing functions.
- Use `linear`, `ease`, `ease-in`, `ease-out`, and `ease-in-out`.
- Understand `cubic-bezier()`, `steps()`, and `linear()`.
- Control duration, delay, iteration count, direction, and fill mode.
- Build practical animations and solve exercises.

---

# 1. What Are CSS Animation Functions?

CSS timing functions control how a style change progresses over time.

Imagine a box moving from the left side of a screen to the right. You can decide whether it moves at a constant rate, starts slowly and accelerates, starts quickly and slows down, or moves in discrete jumps.

**Remember:** `@keyframes` defines *what changes*. A timing function defines *how progress through that change happens over time*.

## Basic vocabulary

| Term | Meaning |
|---|---|
| Property | CSS value being changed, such as `transform` or `opacity` |
| Duration | How long the animation takes |
| Delay | How long to wait before it starts |
| Keyframes | Named points describing styles during an animation |
| Timing function | Controls the pace of progress |
| Iteration count | How many times an animation repeats |
| Direction | Whether it runs forward, backward, or alternates |
| Fill mode | Controls styles outside the active animation interval |

---

# 2. Transitions vs Animations

## CSS transition

A transition animates a change between styles, commonly when the user hovers over, focuses on, or activates an element.

```html
<button class="button">Hover over me</button>
```

```css
.button {
  background: royalblue;
  color: white;
  padding: 12px 20px;
  border: 0;
  border-radius: 8px;
  transition: background-color 300ms ease, transform 300ms ease;
}

.button:hover {
  background: darkblue;
  transform: translateY(-3px);
}
```

## CSS animation

An animation uses `@keyframes` to describe one or more stages and can run automatically.

```html
<div class="box"></div>
```

```css
.box {
  width: 70px;
  height: 70px;
  background: tomato;
  animation: move 2s ease-in-out infinite alternate;
}

@keyframes move {
  from { transform: translateX(0); }
  to { transform: translateX(200px); }
}
```

The box moves back and forth because the animation repeats and alternates direction.

---

# 3. Main CSS Timing Functions

## 3.1 `linear`

The animation progresses at a constant rate.

```css
.box {
  animation: move 2s linear infinite alternate;
}
```

**Use cases:** progress indicators, rotating objects, continuously moving decorations, and loaders.

Think of `linear` as a car moving at a constant speed.

## 3.2 `ease`

The animation starts slowly, speeds up, and slows down near the end.

```css
.box {
  animation: move 2s ease infinite alternate;
}
```

**Use cases:** general UI motion, cards, small decorative movements, and simple entrances.

## 3.3 `ease-in`

The animation starts slowly and accelerates.

```css
.box {
  animation: move 2s ease-in infinite alternate;
}
```

**Use cases:** movement that builds momentum or an element accelerating away.

## 3.4 `ease-out`

The animation starts quickly and slows near the end.

```css
.box {
  animation: move 2s ease-out infinite alternate;
}
```

**Use cases:** dropdowns, popups, elements entering the screen, and objects settling into place.

## 3.5 `ease-in-out`

The animation starts slowly, speeds up in the middle, and slows down at the end.

```css
.box {
  animation: move 2s ease-in-out infinite alternate;
}
```

**Use cases:** smooth entrances and exits, moving cards, and panels.

## Quick comparison

| Function | Speed pattern | Typical use |
|---|---|---|
| `linear` | Constant | Continuous movement |
| `ease` | Slow → fast → slow | General-purpose animation |
| `ease-in` | Slow → fast | Acceleration |
| `ease-out` | Fast → slow | Settling into place |
| `ease-in-out` | Slow → fast → slow | Smooth movement |

---

# 4. Try the Timing Functions Yourself

Save this as `timing-functions.html` and open it in a browser.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CSS Timing Functions</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 24px;
    }

    .track {
      margin: 20px 0;
      padding: 8px;
      border: 1px solid #ccc;
      border-radius: 8px;
    }

    .ball {
      width: 48px;
      height: 48px;
      border-radius: 50%;
      background: royalblue;
      animation: travel 2s infinite alternate;
    }

    .linear { animation-timing-function: linear; }
    .ease { animation-timing-function: ease; }
    .ease-in { animation-timing-function: ease-in; }
    .ease-out { animation-timing-function: ease-out; }
    .ease-in-out { animation-timing-function: ease-in-out; }

    @keyframes travel {
      from { transform: translateX(0); }
      to { transform: translateX(250px); }
    }
  </style>
</head>
<body>
  <h1>CSS Timing Functions</h1>

  <div class="track"><p>linear</p><div class="ball linear"></div></div>
  <div class="track"><p>ease</p><div class="ball ease"></div></div>
  <div class="track"><p>ease-in</p><div class="ball ease-in"></div></div>
  <div class="track"><p>ease-out</p><div class="ball ease-out"></div></div>
  <div class="track"><p>ease-in-out</p><div class="ball ease-in-out"></div></div>
</body>
</html>
```

Observe how the balls travel the same distance but have different speed patterns.

---

# 5. `cubic-bezier()`

`cubic-bezier()` lets you create a custom timing curve.

```css
.box {
  animation: move 2s cubic-bezier(0.42, 0, 0.58, 1) infinite alternate;
}
```

Syntax:

```css
cubic-bezier(x1, y1, x2, y2)
```

- `x1` and `x2` control positions along the time axis and must be between `0` and `1`.
- `y1` and `y2` control progress and may be outside that range, allowing overshoot effects.

A curve similar to `ease-in-out`:

```css
animation-timing-function: cubic-bezier(0.42, 0, 0.58, 1);
```

A more dramatic curve that can overshoot:

```css
animation-timing-function: cubic-bezier(0.68, -0.55, 0.27, 1.55);
```

**Use cases:** custom easing for polished interfaces, playful movement, and matching a design system's motion style.

---

# 6. `steps()`

`steps()` moves through a set number of discrete jumps rather than progressing smoothly.

```css
.box {
  animation: move 2s steps(5, end) infinite alternate;
}
```

Syntax:

```css
steps(number-of-steps, jump-term)
```

Common jump terms include `jump-end` (or `end`), `jump-start` (or `start`), `jump-none`, and `jump-both`.

## Example

```html
<div class="step-box"></div>
```

```css
.step-box {
  width: 40px;
  height: 40px;
  background: seagreen;
  animation: step-move 2s steps(4, end) infinite alternate;
}

@keyframes step-move {
  from { transform: translateX(0); }
  to { transform: translateX(200px); }
}
```

The box jumps between positions instead of moving smoothly.

**Use cases:** sprite-sheet animation, retro pixel effects, counters, and typing-style effects.

---

# 7. `linear()` — Advanced Custom Timing

The CSS `linear()` timing function lets you define custom progress points. Despite its name, a sequence of points can create non-uniform pacing.

```css
.box {
  animation: move 2s linear(0, 0.25, 1, 0.75, 1) infinite alternate;
}
```

The values describe progress points across the timing curve. Browser support for newer CSS features can vary, so test the browsers required by your project.

For most beginner projects, learn the standard timing functions and `steps()` first.

---

# 8. Animation Shorthand

The `animation` shorthand combines several animation properties in one declaration.

```css
.box {
  animation: move 2s ease-in-out 0.5s infinite alternate both;
}
```

This sets:

- `move`: animation name.
- `2s`: duration.
- `ease-in-out`: timing function.
- `0.5s`: delay.
- `infinite`: repeat indefinitely.
- `alternate`: reverse direction on alternate iterations.
- `both`: apply backwards and forwards fill behavior.

You can write the longhand properties instead:

```css
.box {
  animation-name: move;
  animation-duration: 2s;
  animation-timing-function: ease-in-out;
  animation-delay: 0.5s;
  animation-iteration-count: infinite;
  animation-direction: alternate;
  animation-fill-mode: both;
}
```

## Important animation properties

| Property | Example | Purpose |
|---|---|---|
| `animation-name` | `move` | Selects the `@keyframes` animation |
| `animation-duration` | `2s` | Sets how long one iteration takes |
| `animation-timing-function` | `ease-out` | Controls progress over time |
| `animation-delay` | `500ms` | Delays the start |
| `animation-iteration-count` | `3` or `infinite` | Sets repeat count |
| `animation-direction` | `alternate` | Controls direction on each iteration |
| `animation-fill-mode` | `forwards` | Controls styles before/after active animation |
| `animation-play-state` | `paused` | Pauses or runs the animation |

---

# 9. Keyframes: Define What Changes

A timing function alone does not create movement. The animation needs styles that change.

```css
@keyframes move {
  from {
    transform: translateX(0);
  }

  to {
    transform: translateX(200px);
  }
}
```

You can also use percentages:

```css
@keyframes color-and-move {
  0% {
    transform: translateX(0);
    background: tomato;
  }

  50% {
    transform: translateX(100px);
    background: gold;
  }

  100% {
    transform: translateX(200px);
    background: royalblue;
  }
}
```

Apply the animation:

```css
.box {
  animation: color-and-move 3s ease-in-out infinite alternate;
}
```

`from` is equivalent to `0%`, and `to` is equivalent to `100%`.

---

# 10. Practical Example: Button Hover

```html
<button class="action-button">Get Started</button>
```

```css
.action-button {
  padding: 12px 22px;
  border: 0;
  border-radius: 8px;
  background: royalblue;
  color: white;
  font-size: 16px;
  cursor: pointer;
  transition:
    transform 250ms ease-out,
    background-color 250ms ease-out;
}

.action-button:hover {
  transform: translateY(-4px);
  background: darkblue;
}

.action-button:active {
  transform: translateY(0);
}

.action-button:focus-visible {
  outline: 3px solid orange;
  outline-offset: 3px;
}
```

### What to learn

- `transition` animates changes between styles.
- `ease-out` makes the hover movement settle smoothly.
- `transform` changes visual position without changing normal document flow.
- `:hover` applies styles while the pointer is over the button.
- `:active` applies styles while the button is being activated.
- `:focus-visible` gives keyboard users a visible focus indicator.

---

# 11. Practical Example: Loading Spinner

```html
<div class="spinner" role="status" aria-label="Loading"></div>
```

```css
.spinner {
  width: 48px;
  height: 48px;
  border: 5px solid #ddd;
  border-top-color: royalblue;
  border-radius: 50%;
  animation: spin 800ms linear infinite;
}

@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}
```

Why use `linear`? A loader usually looks best when it rotates at a constant rate.

---

# 12. Practical Example: Fade In

```html
<div class="message">Welcome to our website!</div>
```

```css
.message {
  animation: fade-in 800ms ease-out both;
}

@keyframes fade-in {
  from {
    opacity: 0;
    transform: translateY(12px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}
```

This combines opacity and movement to create a subtle entrance.

---

# 13. Practical Example: Bounce

```html
<div class="ball"></div>
```

```css
.ball {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background: tomato;
  animation: bounce 700ms ease-in-out infinite alternate;
}

@keyframes bounce {
  from { transform: translateY(0); }
  to { transform: translateY(-100px); }
}
```

This creates a simple up-and-down motion. For a more realistic bounce, add intermediate keyframes and tune the timing function.

---

# 14. Performance and Accessibility Tips

- Prefer animating `transform` and `opacity` for many UI effects because they often avoid layout recalculation.
- Animating properties such as `width`, `height`, `top`, or `left` can cause layout work. Use them when needed, but test performance.
- Avoid constant motion that distracts users or makes a page hard to read.
- Respect the user's reduced-motion preference.

Example:

```css
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

For important interfaces, consider whether each animation should be removed or replaced with a less motion-heavy alternative.

---

# 15. Common Mistakes

## Mistake 1: Forgetting to define keyframes

```css
.box {
  animation: move 2s ease;
}
```

If there is no `@keyframes move`, the named animation has no definition to run.

## Mistake 2: Setting duration to zero

```css
animation-duration: 0s;
```

The animation will not visibly progress over time.

## Mistake 3: Expecting a timing function to move an element by itself

```css
.box {
  animation-timing-function: ease-in-out;
}
```

This alone does not create an animation. Define a transition or animation and the relevant style change as well.

## Mistake 4: Confusing transition and animation

- Use a transition for a style change triggered by a state change, such as hover or focus.
- Use `@keyframes` animation when you need multiple stages, automatic playback, or repeated motion.

## Mistake 5: Overusing `infinite`

Continuous movement can distract users. Use it only when repeated motion serves a clear purpose, such as a loading indicator.

---

# 16. Practice Tasks

Try these before checking the solutions.

## Beginner

- [ ] **Task 1:** Move a box 200 pixels using `linear`.
- [ ] **Task 2:** Repeat the same movement using `ease-in`.
- [ ] **Task 3:** Create a button that moves upward on hover using a transition.
- [ ] **Task 4:** Create a spinner using `linear` and `infinite`.
- [ ] **Task 5:** Create a fade-in message using `opacity`.

## Intermediate

- [ ] **Task 6:** Compare `ease`, `ease-in`, `ease-out`, and `ease-in-out` on the same movement.
- [ ] **Task 7:** Create a step animation using `steps(5, end)`.
- [ ] **Task 8:** Create a box that alternates between two positions.
- [ ] **Task 9:** Design a custom movement using `cubic-bezier()`.
- [ ] **Task 10:** Add a reduced-motion media query to your animation project.

## Challenge questions

1. What is the difference between `animation-duration` and `animation-delay`?
2. What does `animation-iteration-count: infinite` do?
3. Why is `linear` suitable for a spinner?
4. What is the difference between `ease-in` and `ease-out`?
5. When might `steps()` be more useful than `ease`?
6. What is the role of `@keyframes`?
7. Why should developers consider reduced-motion preferences?

---

# 17. Sample Solutions

## Solution: Move a box linearly

```css
.box {
  width: 50px;
  height: 50px;
  background: royalblue;
  animation: move 2s linear infinite alternate;
}

@keyframes move {
  from { transform: translateX(0); }
  to { transform: translateX(200px); }
}
```

## Solution: Fade in

```css
.message {
  animation: fade-in 1s ease-out both;
}

@keyframes fade-in {
  from { opacity: 0; }
  to { opacity: 1; }
}
```

## Solution: Button hover

```css
button {
  transition: transform 250ms ease-out;
}

button:hover {
  transform: translateY(-4px);
}
```

## Solution: Discrete steps

```css
.box {
  animation: step-move 2s steps(5, end) infinite alternate;
}

@keyframes step-move {
  from { transform: translateX(0); }
  to { transform: translateX(200px); }
}
```

---

# 18. Quick Revision

- `linear`: constant speed.
- `ease`: slow start, faster middle, slow end.
- `ease-in`: starts slowly and accelerates.
- `ease-out`: starts quickly and slows down.
- `ease-in-out`: slow start and end, faster middle.
- `cubic-bezier()`: creates a custom timing curve.
- `steps()`: creates discrete jumps.
- `linear()`: defines a custom sequence of timing progress points.
- `@keyframes`: defines styles at different animation stages.
- `transition`: animates changes between styles.
- `animation`: plays a keyframe sequence.
- `animation-duration`: sets duration.
- `animation-delay`: delays the start.
- `animation-iteration-count`: sets how many times it repeats.
- `animation-direction`: controls playback direction.
- `animation-fill-mode`: controls how animation styles apply outside the active interval.

## Final takeaway

Timing functions control **how an animation progresses over time**. Start with `linear`, `ease`, `ease-in`, `ease-out`, and `ease-in-out`. Then explore `steps()` and `cubic-bezier()` for more specific effects. Use motion purposefully, test on different devices, and respect reduced-motion preferences.
