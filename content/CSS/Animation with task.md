# HTML & CSS Animation — Beginner to Intermediate Notes

## Table of Contents

1. Introduction to CSS Animation
    
2. CSS Transition vs CSS Animation
    
3. Your First Animated Button
    
4. Understanding `@keyframes`
    
5. Creating a Moving Ball
    
6. Bouncing Ball Animation
    
7. Important Animation Properties
    
8. CSS Animation Shorthand
    
9. Fun Animation Examples
    
10. Animated To-Do List Project
    
11. Common Animation Mistakes
    
12. Practice Tasks: Beginner to Intermediate
    
13. Learning Roadmap
    

---

# 1. Introduction to CSS Animation

CSS animation allows us to change the appearance and behavior of HTML elements over time without requiring JavaScript.

We can use CSS animations to:

- Move elements from one position to another.
    
- Change background colors.
    
- Rotate objects.
    
- Increase or decrease element size.
    
- Fade elements in or out.
    
- Create loading spinners.
    
- Animate buttons, cards, notifications, and menus.
    
- Create engaging user interfaces.
    

### Real-World Examples

- A button grows when the user hovers over it.
    
- A loading spinner rotates while data is loading.
    
- A notification slides into view.
    
- A ball bounces up and down.
    
- A heading fades into the screen.
    
- A To-Do task receives a strike-through when completed.
    

### Why Do We Need CSS Animation?

Without animation, an interface may feel static. Animation can provide feedback, guide user attention, and make interactions feel smoother.

However, animations should be meaningful. Excessive movement can distract users and affect accessibility.

---

# 2. CSS Transition vs CSS Animation

Both transitions and animations help create movement and visual changes, but they serve different purposes.

|Feature|CSS Transition|CSS Animation|
|---|---|---|
|Purpose|Smoothly changes a property between states|Creates motion using defined keyframes|
|Trigger|Usually a state change, such as hover|Can start automatically|
|Multiple stages|Limited to a transition between states|Supports multiple keyframes|
|Repetition|Does not repeat automatically|Can repeat indefinitely|
|Main properties|`transition`|`animation`, `@keyframes`|
|Example|Button grows on hover|Ball continuously bounces|

## Example 1: CSS Transition

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Transition Example</title>

    <style>
        button {
            padding: 15px 30px;
            background-color: royalblue;
            color: white;
            border: none;
            border-radius: 10px;
            cursor: pointer;

            transition: transform 0.3s ease,
                        background-color 0.3s ease;
        }

        button:hover {
            transform: scale(1.15);
            background-color: darkorange;
        }
    </style>
</head>
<body>

    <button>Hover Over Me!</button>

</body>
</html>
```

### Explanation

- `transition` specifies which properties should change smoothly.
    
- `0.3s` specifies the transition duration.
    
- `ease` controls the speed pattern.
    
- `:hover` applies styles when the pointer moves over the button.
    
- `scale(1.15)` increases the button's size by 15%.
    

### Practice

1. Change `scale(1.15)` to `scale(1.5)`.
    
2. Change the background color.
    
3. Add `rotate(10deg)` to the hover effect.
    
4. Change the duration to `1s`.
    

---

# 3. Understanding CSS Transform

The `transform` property changes an element's position, size, rotation, or shape without changing the normal document flow.

## Important Transform Functions

|Function|Purpose|Example|
|---|---|---|
|`translateX()`|Moves horizontally|`translateX(100px)`|
|`translateY()`|Moves vertically|`translateY(-50px)`|
|`scale()`|Changes size|`scale(1.2)`|
|`rotate()`|Rotates an element|`rotate(45deg)`|
|`skew()`|Skews an element|`skew(10deg)`|

### Example

```
.box {
    transform: translateX(100px);
}

.box:hover {
    transform: scale(1.2) rotate(10deg);
}
```

**Important:** When multiple transforms are used together, they must be included in the same `transform` declaration.

---

# 4. Understanding `@keyframes`

The `@keyframes` rule defines the stages of a CSS animation.

It tells the browser what an element should look like at different points during the animation.

## Basic Syntax

```
@keyframes animationName {
    from {
        /* Starting styles */
    }

    to {
        /* Ending styles */
    }
}
```

The `from` keyword represents the beginning, while `to` represents the ending.

## Example: Change a Box's Color

```
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Keyframes Example</title>

    <style>
        .box {
            width: 100px;
            height: 100px;
            background-color: tomato;
            animation: colorChange 3s infinite alternate;
        }

        @keyframes colorChange {
            from {
                background-color: tomato;
            }

            to {
                background-color: royalblue;
            }
        }
    </style>
</head>
<body>

    <div class="box"></div>

</body>
</html>
```

### Explanation

- `.box` defines the HTML element's initial appearance.
    
- `animation: colorChange` connects the element to the named animation.
    
- `3s` specifies the duration.
    
- `infinite` repeats the animation.
    
- `alternate` reverses the direction on alternate iterations.
    

## Using Percentage Keyframes

We can define multiple animation stages using percentages.

```
@keyframes colorChange {
    0% {
        background-color: tomato;
    }

    25% {
        background-color: gold;
    }

    50% {
        background-color: limegreen;
    }

    75% {
        background-color: deepskyblue;
    }

    100% {
        background-color: tomato;
    }
}
```

### When Should We Use Percentages?

Use percentage keyframes when you want to control what happens at specific points during an animation.

For example, a box might change color at 25%, rotate at 50%, and return to its original state at 100%.

---

# 5. Creating a Moving Ball

In this example, a ball moves horizontally and then returns to its starting position.

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Moving Ball</title>

    <style>
        .ball {
            width: 70px;
            height: 70px;
            background-color: tomato;
            border-radius: 50%;

            animation: moveBall 2s infinite alternate;
        }

        @keyframes moveBall {
            from {
                transform: translateX(0);
            }

            to {
                transform: translateX(250px);
            }
        }
    </style>
</head>
<body>

    <div class="ball"></div>

</body>
</html>
```

### Explanation

1. `border-radius: 50%` makes the element circular.
    
2. `translateX(250px)` moves it 250 pixels to the right.
    
3. `2s` controls the duration of each directional iteration.
    
4. `infinite` repeats the animation.
    
5. `alternate` makes the ball move forward and backward.
    

### Practice Questions

1. What happens if `250px` is changed to `500px`?
    
2. What happens if the duration changes from `2s` to `0.5s`?
    
3. What happens if `alternate` is removed?
    
4. How would you change the animation to move vertically?
    

---

# 6. Bouncing Ball Animation

A bouncing ball demonstrates vertical movement, scaling, and timing functions.

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Bouncing Ball</title>

    <style>
        body {
            background-color: #eef2ff;
            min-height: 100vh;
            display: grid;
            place-items: center;
        }

        .scene {
            width: 300px;
            height: 180px;
            position: relative;
            border-bottom: 5px solid #475569;
        }

        .ball {
            width: 55px;
            height: 55px;
            background-color: #f43f5e;
            border-radius: 50%;

            position: absolute;
            bottom: 0;
            left: 120px;

            animation: bounce 0.8s ease-in-out infinite alternate;
        }

        @keyframes bounce {
            from {
                transform: translateY(0) scaleX(1.1) scaleY(0.9);
            }

            to {
                transform: translateY(-120px) scaleX(0.9) scaleY(1.1);
            }
        }
    </style>
</head>
<body>

    <div class="scene">
        <div class="ball"></div>
    </div>

</body>
</html>
```

### How It Works

- `position: relative` establishes the positioning context for the ball.
    
- `position: absolute` positions the ball within the scene.
    
- `translateY(-120px)` moves the ball upward.
    
- `scaleX()` and `scaleY()` create a slight squash-and-stretch effect.
    
- `ease-in-out` creates a smoother change in speed.
    
- `alternate` allows the ball to return to its original state.
    

### Practice

1. Reduce the height of the bounce to `-50px`.
    
2. Increase it to `-150px`.
    
3. Change the duration to `0.3s`.
    
4. Try a different color.
    
5. Add a shadow beneath the ball.
    

---

# 7. Important CSS Animation Properties

CSS animations have several properties that control their behavior.

|Property|Purpose|Example|
|---|---|---|
|`animation-name`|Specifies the keyframe name|`bounce`|
|`animation-duration`|Sets the duration|`2s`|
|`animation-timing-function`|Controls the speed pattern|`ease-in-out`|
|`animation-delay`|Delays the start|`1s`|
|`animation-iteration-count`|Sets the number of repetitions|`infinite`|
|`animation-direction`|Controls the playback direction|`alternate`|
|`animation-fill-mode`|Controls styles before or after playback|`forwards`|
|`animation-play-state`|Pauses or resumes an animation|`paused`|

## 7.1 Animation Name

The name connects the element to the corresponding keyframes.

```
.box {
    animation-name: slide;
}

@keyframes slide {
    from {
        transform: translateX(0);
    }

    to {
        transform: translateX(100px);
    }
}
```

## 7.2 Animation Duration

Specifies how long one iteration takes.

```
.box {
    animation-duration: 2s;
}
```

## 7.3 Animation Delay

Specifies how long to wait before starting.

```
.box {
    animation-delay: 1s;
}
```

## 7.4 Animation Iteration Count

Specifies the number of repetitions.

```
.box {
    animation-iteration-count: 3;
}
```

To repeat continuously:

```
.box {
    animation-iteration-count: infinite;
}
```

## 7.5 Animation Direction

```
.box {
    animation-direction: alternate;
}
```

Common values:

- `normal`: Plays forward each iteration.
    
- `reverse`: Plays backward.
    
- `alternate`: Alternates between forward and backward.
    
- `alternate-reverse`: Starts backward and alternates direction.
    

## 7.6 Animation Fill Mode

```
.box {
    animation: slide 2s forwards;
}
```

The `forwards` value keeps the final keyframe's applicable styles after the animation finishes.

Other values include:

- `none`: Does not retain animation styles outside playback.
    
- `backwards`: Applies relevant starting keyframe styles during the delay.
    
- `both`: Applies the effects of `backwards` and `forwards`.
    

## 7.7 Animation Play State

```
.box {
    animation: spin 2s linear infinite;
}

.box:hover {
    animation-play-state: paused;
}
```

The animation pauses while the pointer is over the element.

---

# 8. CSS Animation Shorthand

Instead of writing every animation property separately, we can combine them using the `animation` shorthand.

## Separate Properties

```
.box {
    animation-name: slide;
    animation-duration: 2s;
    animation-timing-function: ease-in-out;
    animation-delay: 1s;
    animation-iteration-count: infinite;
    animation-direction: alternate;
}
```

## Shorthand Version

```
.box {
    animation: slide 2s ease-in-out 1s infinite alternate;
}
```

Both examples specify the same animation settings.

The shorthand contains:

1. Animation name: `slide`
    
2. Duration: `2s`
    
3. Timing function: `ease-in-out`
    
4. Delay: `1s`
    
5. Iteration count: `infinite`
    
6. Direction: `alternate`
    

---

# 9. Fun Animation Examples

## 9.1 Glowing Pulse

A circle grows and shrinks continuously.

```
<!DOCTYPE html>
<html>
<head>
    <title>Pulse Animation</title>

    <style>
        body {
            display: grid;
            place-items: center;
            min-height: 100vh;
        }

        .glow {
            width: 100px;
            height: 100px;
            background-color: deepskyblue;
            border-radius: 50%;
            animation: pulse 1s ease-in-out infinite alternate;
        }

        @keyframes pulse {
            from {
                transform: scale(1);
                opacity: 1;
            }

            to {
                transform: scale(1.2);
                opacity: 0.6;
            }
        }
    </style>
</head>
<body>

    <div class="glow"></div>

</body>
</html>
```

## 9.2 Loading Spinner

```
<!DOCTYPE html>
<html>
<head>
    <title>Loading Spinner</title>

    <style>
        .spinner {
            width: 50px;
            height: 50px;
            border: 6px solid #ddd;
            border-top-color: royalblue;
            border-radius: 50%;

            animation: spin 0.8s linear infinite;
        }

        @keyframes spin {
            to {
                transform: rotate(360deg);
            }
        }
    </style>
</head>
<body>

    <div class="spinner"></div>

</body>
</html>
```

### Explanation

- The border creates the circular shape.
    
- `border-top-color` highlights one part of the circle.
    
- `rotate(360deg)` rotates the element.
    
- `linear` keeps the rotational speed consistent.
    
- `infinite` makes the spinner rotate continuously.
    

## 9.3 Fade-In Text

```
<!DOCTYPE html>
<html>
<head>
    <title>Fade-In Animation</title>

    <style>
        .message {
            animation: fadeIn 1s ease-out both;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
    </style>
</head>
<body>

    <h1 class="message">Welcome to CSS Animation!</h1>

</body>
</html>
```

The text starts transparent and slightly lower, then becomes visible in its final position.

## 9.4 Bouncing Loading Dots

```
<!DOCTYPE html>
<html>
<head>
    <title>Bouncing Dots</title>

    <style>
        .dot {
            display: inline-block;
            width: 14px;
            height: 14px;
            margin: 5px;
            background-color: tomato;
            border-radius: 50%;

            animation: jump 0.6s ease-in-out infinite alternate;
        }

        .dot:nth-child(2) {
            animation-delay: 0.2s;
        }

        .dot:nth-child(3) {
            animation-delay: 0.4s;
        }

        @keyframes jump {
            to {
                transform: translateY(-15px);
            }
        }
    </style>
</head>
<body>

    <div>
        <span class="dot"></span>
        <span class="dot"></span>
        <span class="dot"></span>
    </div>

</body>
</html>
```

### Explanation

- `nth-child(2)` selects the second dot.
    
- `nth-child(3)` selects the third dot.
    
- Different animation delays create a sequential bouncing effect.
    

---

# 10. Mini Project: Animated To-Do List

## Project Objective

Create a To-Do list using HTML and CSS with the following features:

- Tasks appear with a slide-in animation.
    
- Hovering over a task changes its appearance.
    
- Checkboxes mark tasks as complete.
    
- Completed tasks show a strike-through animation.
    
- The layout adjusts to smaller screens.
    
- Reduced-motion preferences are respected.
    

**Note:** This is a CSS-only version. Adding, deleting, or saving tasks dynamically requires JavaScript or a backend.

## Complete Code

Save the following code as `todo.html` and open it in your browser.

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">

    <meta name="viewport"
          content="width=device-width, initial-scale=1.0">

    <title>Animated To-Do List</title>

    <style>
        * {
            box-sizing: border-box;
        }

        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(135deg, #dbeafe, #fce7f3);
            min-height: 100vh;
            margin: 0;
            padding: 40px 16px;
        }

        .todo {
            max-width: 450px;
            margin: auto;
            padding: 25px;
            background: white;
            border-radius: 18px;
            box-shadow: 0 10px 30px #00000015;
        }

        h1 {
            color: #3730a3;
            text-align: center;
        }

        .task {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 14px;
            margin: 12px 0;
            background: #f8fafc;
            border-radius: 10px;

            animation: slideIn 0.5s ease both;

            transition:
                transform 0.25s,
                background 0.25s;
        }

        .task:nth-of-type(1) {
            animation-delay: 0.1s;
        }

        .task:nth-of-type(2) {
            animation-delay: 0.2s;
        }

        .task:nth-of-type(3) {
            animation-delay: 0.3s;
        }

        .task:nth-of-type(4) {
            animation-delay: 0.4s;
        }

        .task:hover {
            transform: translateX(6px);
            background: #eef2ff;
        }

        .task input {
            width: 18px;
            height: 18px;
            accent-color: #4f46e5;
            cursor: pointer;
        }

        .task span {
            position: relative;
            color: #334155;
        }

        .task input:checked + span {
            color: #94a3b8;
        }

        .task input:checked + span::after {
            content: "";
            position: absolute;
            left: 0;
            right: 0;
            top: 50%;
            height: 2px;
            background: #94a3b8;
            transform-origin: left;

            animation: strike 0.3s ease-out both;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(15px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes strike {
            from {
                transform: scaleX(0);
            }

            to {
                transform: scaleX(1);
            }
        }

        .hint {
            text-align: center;
            color: #64748b;
            font-size: 13px;
            margin-top: 20px;
        }

        @media (prefers-reduced-motion: reduce) {
            *,
            *::before,
            *::after {
                animation-duration: 0.01ms !important;
                animation-iteration-count: 1 !important;
                transition-duration: 0.01ms !important;
            }
        }
    </style>
</head>

<body>

    <main class="todo">

        <h1>My To-Do List</h1>

        <label class="task">
            <input type="checkbox">
            <span>Learn HTML basics</span>
        </label>

        <label class="task">
            <input type="checkbox">
            <span>Practice CSS Flexbox</span>
        </label>

        <label class="task">
            <input type="checkbox">
            <span>Understand CSS animations</span>
        </label>

        <label class="task">
            <input type="checkbox">
            <span>Build a mini project</span>
        </label>

        <p class="hint">
            Check a task when you complete it!
        </p>

    </main>

</body>
</html>
```

## Explanation of the To-Do List

|CSS Feature|Purpose|
|---|---|
|`display: flex`|Aligns the checkbox and task text|
|`animation: slideIn`|Animates tasks into view|
|`animation-delay`|Creates a staggered entrance|
|`:hover`|Applies hover effects|
|`:checked + span`|Selects the text next to a checked checkbox|
|`::after`|Creates the strike-through line|
|`scaleX(0)`|Starts the line at zero horizontal scale|
|`scaleX(1)`|Expands the line to full horizontal scale|
|`@media`|Applies styles based on device or user preferences|

### To-Do List Challenges

1. Add five more tasks.
    
2. Change the card's background gradient.
    
3. Change the hover movement from `6px` to `12px`.
    
4. Add a different color for completed tasks.
    
5. Add a small animated icon next to the heading.
    
6. Create a JavaScript version that allows users to add and delete tasks.
    
7. Save tasks using browser storage in the JavaScript version.
    

---

# 11. Common CSS Animation Mistakes

## Mistake 1: Forgetting `@keyframes`

An animation name must match a defined keyframe name.

Incorrect:

```
.box {
    animation: moveBox 2s infinite;
}
```

If `@keyframes moveBox` does not exist, the expected animation will not run.

## Mistake 2: Forgetting the Duration

```
.box {
    animation: moveBox;
}
```

The default animation duration is `0s`, so there will normally be no visible movement.

Correct:

```
.box {
    animation: moveBox 2s;
}
```

## Mistake 3: Using `transition` Without a Changing Property

```
.box {
    transition: transform 0.5s;
}
```

This declaration defines a transition but does not create movement by itself.

Add a changing state:

```
.box:hover {
    transform: scale(1.2);
}
```

## Mistake 4: Confusing `infinite` and `alternate`

- `infinite` repeats the animation.
    
- `alternate` changes the direction on alternate iterations.
    

They perform different functions and can be used together.

## Mistake 5: Animating Too Many Properties

Prefer `transform` and `opacity` for many common effects. Properties such as `width`, `height`, `top`, and `left` may trigger layout work and can be more expensive to animate.

## Mistake 6: Ignoring Accessibility

Continuous or rapid animations can be distracting or uncomfortable for some users.

Use `prefers-reduced-motion` to reduce or disable unnecessary animation when a user requests reduced motion.

---

# 12. Practice Tasks: Beginner to Intermediate

## Beginner-Level Tasks

### Task 1: Hover Button

Create a button that:

- Grows when hovered.
    
- Rotates slightly.
    
- Changes background color.
    
- Returns smoothly to its original appearance.
    

**Hint:** Use `:hover`, `transform`, and `transition`.

### Task 2: Spinning Loader

Create a circular loading spinner that rotates continuously.

**Hint:** Use `border`, `border-radius`, `@keyframes`, and `linear`.

### Task 3: Bouncing Ball

Create a ball that bounces vertically.

**Hint:** Use `translateY()`, `alternate`, and `animation-duration`.

### Task 4: Fade-In Heading

Make a heading appear from below when the page loads.

**Hint:** Animate `opacity` from `0` to `1` and `translateY()` from `20px` to `0`.

## Intermediate-Level Tasks

### Task 5: Animated Profile Card

Create a profile card that:

- Moves upward on hover.
    
- Zooms the profile image slightly.
    
- Animates the button.
    
- Uses rounded corners and shadows.
    

**Hint:** Combine `transition`, `transform`, `overflow`, and `border-radius`.

### Task 6: Traffic Light

Create a traffic light with red, yellow, and green lights.

Requirements:

- Only one light should be active at a time.
    
- Each light should illuminate in sequence.
    
- The sequence should repeat.
    

**Hint:** Use multiple animations with delays or percentage keyframes.

### Task 7: Animated Notification

Create a notification that:

- Slides into view.
    
- Remains visible.
    
- Fades away.
    

**Hint:** Use percentage keyframes and `animation-fill-mode`.

### Task 8: To-Do List Upgrade

Extend the To-Do project to:

- Animate task completion.
    
- Visually distinguish completed tasks.
    
- Add and delete tasks.
    
- Save tasks across page reloads.
    

**Hint:** CSS can handle the animations. JavaScript is required for dynamic task creation, deletion, and browser storage.

---

# 13. Learning Roadmap

## Stage 1: Beginner

Learn:

- `:hover`
    
- `transition`
    
- `transform`
    
- `scale()`
    
- `rotate()`
    
- `translate()`
    

**Projects:** Animated button and profile card.

## Stage 2: Core Animations

Learn:

- `@keyframes`
    
- Timing functions
    
- Animation delays
    
- Iteration counts
    
- Animation direction
    
- Animation fill modes
    

**Projects:** Bouncing ball and loading spinner.

## Stage 3: Intermediate

Learn:

- Percentage-based keyframes
    
- Multiple animation stages
    
- Animation sequencing
    
- Pseudo-elements
    
- Checkbox selectors
    
- Responsive layouts
    
- Reduced-motion support
    

**Projects:** Animated To-Do list, notifications, and dashboard cards.

---

# Final Learning Advice

Do not simply copy the examples. Change one CSS property at a time, predict the result, run the code, and observe the difference.

For every animation, ask yourself:

1. What is the starting state?
    
2. What is the ending state?
    
3. Which property changes?
    
4. How long does the change take?
    
5. Should the animation repeat?
    
6. Should it reverse direction?
    
7. What should happen when the user interacts with the element?
    

Once you can answer these questions, you will be ready to create your own animations and build more interactive interfaces using HTML and CSS.