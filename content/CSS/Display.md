# CSS `display` Property — Complete Notes

## 1. What is `display` in CSS?

The `display` property tells the browser **how an HTML element should participate in the layout**.

```
.box {
    display: block;
}
```

Think of it as:

> **"How should this element behave and how should its children be arranged?"**

Common values:

```
display: block;
display: inline;
display: inline-block;
display: flex;
display: inline-flex;
display: grid;
display: none;
```

For now, focus on:

```
block
   ↓
inline
   ↓
inline-block
   ↓
flex
   ↓
inline-flex
   ↓
flex properties
   ↓
position + display
```

---

# 2. Before `display`: Understand Normal Flow

HTML elements normally appear in a particular flow.

```
<div>One</div>
<div>Two</div>
<div>Three</div>
```

Normally:

```
One
Two
Three
```

Each `<div>` starts on a new line because `<div>` is normally:

```
display: block;
```

But:

```
<span>One</span>
<span>Two</span>
<span>Three</span>
```

appears approximately as:

```
One Two Three
```

because `<span>` is normally:

```
display: inline;
```

This difference is the foundation of `display`.

---

# 3. `display: block`

A block element generally:

- starts on a new line
- takes the available width by default
- allows `width` and `height`
- allows `margin` and `padding`
- pushes the next block to the next line

Example:

```
.box {
    display: block;
    width: 200px;
    height: 100px;
}
```

HTML:

```
<div class="box">Box 1</div>
<div class="box">Box 2</div>
```

Result:

```
┌──────────────┐
│    Box 1     │
└──────────────┘

┌──────────────┐
│    Box 2     │
└──────────────┘
```

### Common block elements

```
<div>
<p>
<h1>
<section>
<header>
<footer>
```

---

# 4. `display: inline`

Inline elements behave like **text inside a line**.

```
span {
    display: inline;
}
```

Example:

```
<span>Hello</span>
<span>World</span>
<span>CSS</span>
```

Result:

```
Hello World CSS
```

### Important limitation

For normal inline elements, `width` and `height` do not behave the way they do on block/inline-block elements.

```
span {
    display: inline;
    width: 200px;
    height: 100px;
}
```

You should **not expect a normal inline element to become a 200 × 100 box**.

This is one reason `inline-block` exists.

---

# 5. `display: inline-block`

This combines useful characteristics of both.

```
.box {
    display: inline-block;
    width: 150px;
    height: 100px;
}
```

Think:

> **Inline outside + block-like box inside**

Example:

```
<div class="box">One</div>
<div class="box">Two</div>
<div class="box">Three</div>
```

```
┌─────────┐ ┌─────────┐ ┌─────────┐
│   One   │ │   Two   │ │  Three  │
└─────────┘ └─────────┘ └─────────┘
```

You can control:

```
width
height
padding
margin
```

while the elements can sit beside each other.

### When is `inline-block` useful?

Older/common use cases include:

- navigation items
- buttons
- small cards
- badges
- labels
- horizontally arranged elements

---

# 6. `block` vs `inline` vs `inline-block`

|Property|Block|Inline|Inline-block|
|---|---|---|---|
|New line|Yes|No|No|
|Width works normally|Yes|No|Yes|
|Height works normally|Yes|No|Yes|
|Padding|Yes|Yes, but behavior differs|Yes|
|Margin|Yes|Horizontal mainly|Yes|
|Can sit beside another|Usually no|Yes|Yes|

The easiest memory trick:

```
BLOCK
"I want my own line."

INLINE
"I behave like text."

INLINE-BLOCK
"I want to sit beside others but still behave like a box."
```

---

# 7. Now comes `display: flex`

This is where CSS becomes much more powerful.

Suppose you have:

```
<div class="container">
    <div>One</div>
    <div>Two</div>
    <div>Three</div>
</div>
```

If you write:

```
.container {
    display: flex;
}
```

the `.container` becomes a **flex container**.

Its direct children become **flex items**.

```
.container
┌───────────────────────────────┐
│ One     Two     Three         │
└───────────────────────────────┘
```

So remember:

```
display: flex;
```

doesn't mean:

> "Make this element flexible."

More accurately:

> **"Make this element a flex container and arrange its direct children using the Flexbox layout system."**

---

# 8. Parent vs Child — VERY IMPORTANT

Consider:

```
<div class="parent">
    <div class="child">A</div>
    <div class="child">B</div>
    <div class="child">C</div>
</div>
```

When you write:

```
.parent {
    display: flex;
}
```

The **parent** becomes the flex container.

The children:

```
A
B
C
```

become flex items.

This distinction is extremely important.

---

# 9. Flex Direction

By default:

```
.container {
    display: flex;
}
```

has:

```
flex-direction: row;
```

So:

```
A   B   C
→ → →
```

You can change it:

```
flex-direction: column;
```

Result:

```
A
↓
B
↓
C
```

So:

```
flex-direction: row;
```

means horizontal main direction.

```
flex-direction: column;
```

means vertical main direction.

---

# 10. Main Axis and Cross Axis

This is the key to understanding Flexbox.

### `row`

```
flex-direction: row;
```

Main axis:

```
──────────────→
```

Cross axis:

```
│
│
↓
```

### `column`

```
flex-direction: column;
```

Main axis:

```
│
│
↓
```

Cross axis:

```
──────────────→
```

Remember:

> **`justify-content` works on the MAIN axis.**

> **`align-items` works on the CROSS axis.**

---

# 11. `justify-content`

It controls how flex items are distributed along the **main axis**.

Example:

```
.container {
    display: flex;
    justify-content: center;
}
```

For a row:

```
        A   B   C
```

Other values:

### `flex-start`

```
A B C
```

### `center`

```
        A B C
```

### `flex-end`

```
                    A B C
```

### `space-between`

```
A          B          C
```

### `space-around`

```
   A       B       C
```

### `space-evenly`

```
     A      B      C
```

---

# 12. `align-items`

`align-items` controls alignment on the **cross axis**.

Example:

```
.container {
    display: flex;
    align-items: center;
}
```

If direction is row:

```
        A B C
        ↑
   vertically centered
```

For example:

```
.container {
    display: flex;
    height: 300px;
    align-items: center;
}
```

The children are vertically centered.

---

# 13. The Most Common Flexbox Centering

You will frequently see:

```
.container {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

This means:

```
justify-content
        ↓
horizontal center

align-items
        ↓
vertical center
```

For a normal row:

```
┌─────────────────────────────┐
│                             │
│           BOX               │
│                             │
└─────────────────────────────┘
```

This is one of the most important CSS patterns to learn.

---

# 14. `gap`

Instead of giving margins to every child:

```
.container {
    display: flex;
    gap: 20px;
}
```

Result:

```
A    20px    B    20px    C
```

You can use:

```
gap: 20px;
```

or:

```
row-gap: 20px;
column-gap: 30px;
```

---

# 15. `flex-wrap`

Normally:

```
display: flex;
```

tries to keep items on one line.

If there isn't enough space:

```
A B C D E F G
```

can become cramped.

Use:

```
flex-wrap: wrap;
```

Then:

```
A B C D
E F G
```

Example:

```
.container {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
}
```

This is very useful for:

- cards
- product layouts
- responsive designs
- tags
- buttons

---

# 16. Now the Important One: `flex: 1`

You will see this everywhere:

```
.child {
    flex: 1;
}
```

What does it mean?

It tells the flex item to **take available space proportionally**.

Example:

```
<div class="container">
    <div class="box">A</div>
    <div class="box">B</div>
    <div class="box">C</div>
</div>
```

```
.container {
    display: flex;
}

.box {
    flex: 1;
}
```

Result:

```
┌────────┬────────┬────────┐
│   A    │   B    │   C    │
└────────┴────────┴────────┘
```

Each gets approximately one-third of the available space.

---

# 17. Why `flex: 1`?

Suppose container width is:

```
900px
```

and:

```
.box {
    flex: 1;
}
```

with three boxes.

Available space is distributed approximately:

```
A = 300px
B = 300px
C = 300px
```

Now:

```
.box:nth-child(1) {
    flex: 2;
}

.box:nth-child(2) {
    flex: 1;
}

.box:nth-child(3) {
    flex: 1;
}
```

The ratio becomes:

```
A : B : C
2 : 1 : 1
```

So roughly:

```
A = 450px
B = 225px
C = 225px
```

assuming the relevant available space is 900px.

---

# 18. What does `flex: 1` actually represent?

The shorthand:

```
flex: 1;
```

is commonly interpreted as:

```
flex-grow: 1;
flex-shrink: 1;
flex-basis: 0%;
```

For beginners, remember:

> **`flex: 1` is commonly used when you want flex items to share available space.**

---

# 19. `flex-grow`

Suppose:

```
.container {
    display: flex;
}

.a {
    flex-grow: 1;
}

.b {
    flex-grow: 2;
}
```

The available extra space is distributed:

```
A : B
1 : 2
```

So B receives twice as much of the **extra available space** as A.

---

# 20. `flex-shrink`

This controls how items shrink when there isn't enough room.

```
.a {
    flex-shrink: 1;
}
```

Default:

```
flex-shrink: 1;
```

A value of:

```
flex-shrink: 0;
```

means the item should not shrink because of flex shrinking.

---

# 21. `flex-basis`

`flex-basis` defines the item's initial size along the main axis.

```
.box {
    flex-basis: 200px;
}
```

If direction is row:

```
initial width ≈ 200px
```

If direction is column:

```
initial height ≈ 200px
```

So:

```
flex-basis
    ↓
size along MAIN AXIS
```

---

# 22. `flex` Shorthand

Instead of:

```
.box {
    flex-grow: 1;
    flex-shrink: 1;
    flex-basis: 0%;
}
```

you commonly write:

```
.box {
    flex: 1;
}
```

Another example:

```
.box {
    flex: 2 1 200px;
}
```

means approximately:

```
grow   = 2
shrink = 1
basis  = 200px
```

---

# 23. `align-self`

`align-items` controls **all children**.

But what if one child needs different alignment?

Use:

```
align-self: center;
```

Example:

```
.container {
    display: flex;
    align-items: flex-start;
}

.special {
    align-self: center;
}
```

So:

```
Normal children → start
Special child   → center
```

---

# 24. `display: inline-flex`

Now an important difference:

```
display: flex;
```

vs

```
display: inline-flex;
```

### `display: flex`

The element behaves as a **block-level flex container**.

### `display: inline-flex`

The element behaves as an **inline-level flex container**.

Example:

```
.box {
    display: inline-flex;
}
```

It can sit beside another element:

```
[BOX] [BOX] [BOX]
```

while its children are still controlled using Flexbox.

Think:

```
flex
= block outside + flex inside

inline-flex
= inline outside + flex inside
```

---

# 25. `display: flex` vs `inline-flex`

||`flex`|`inline-flex`|
|---|---|---|
|Outside behavior|Block-like|Inline-like|
|Children|Flex items|Flex items|
|Can sit beside another element|Usually not as an inline box|Yes|
|Flexbox features|Yes|Yes|

---

# 26. Now Let's Understand `position`

This is a **different CSS concept**.

`display` primarily answers:

> **How does the element participate in layout?**

`position` answers:

> **How is the element positioned relative to its normal position or another reference?**

Common values:

```
position: static;
position: relative;
position: absolute;
position: fixed;
position: sticky;
```

---

# 27. `position: static`

This is the default.

```
.box {
    position: static;
}
```

The element follows normal document flow.

For example:

```
.box {
    top: 20px;
}
```

with:

```
position: static;
```

`top` doesn't move it in the way you might expect.

---

# 28. `position: relative`

```
.box {
    position: relative;
}
```

The element **remains in the normal flow**, but you can offset it using:

```
top
right
bottom
left
```

Example:

```
.box {
    position: relative;
    top: 20px;
    left: 30px;
}
```

It visually moves:

```
↓ 20px
→ 30px
```

But its original space is generally still preserved.

---

# 29. Why is `relative` extremely important?

Because it is commonly used as a **reference point for an absolutely positioned child**.

Example:

```
<div class="card">
    <span class="badge">New</span>
</div>
```

```
.card {
    position: relative;
}

.badge {
    position: absolute;
    top: 10px;
    right: 10px;
}
```

Now the badge can be positioned relative to the card.

Conceptually:

```
┌──────────────────────────┐
│                    New   │ ← absolute
│                          │
│        CARD              │
│                          │
└──────────────────────────┘
        ↑
 position: relative
```

This pattern is extremely common.

---

# 30. `position: absolute`

An absolutely positioned element is removed from normal document flow.

```
.badge {
    position: absolute;
    top: 10px;
    right: 10px;
}
```

It is positioned relative to an appropriate containing block, commonly established by a positioned ancestor such as:

```
.card {
    position: relative;
}
```

This is used for:

- badges
- overlays
- icons
- dropdowns
- tooltips
- close buttons
- notification indicators

---

# 31. `position: fixed`

```
position: fixed;
```

The element is positioned relative to the viewport in typical use.

Example:

```
.chat-button {
    position: fixed;
    right: 20px;
    bottom: 20px;
}
```

Result:

```
┌───────────────────────────┐
│                           │
│                           │
│                           │
│                     (💬)  │
└───────────────────────────┘
```

Useful for:

- floating buttons
- fixed navigation
- chat buttons
- persistent controls

---

# 32. `position: sticky`

This is a combination of normal-flow behavior and sticky positioning.

Example:

```
.header {
    position: sticky;
    top: 0;
}
```

It can behave normally until a scroll threshold is reached, after which it sticks according to the specified inset.

Common use:

```
Page
 ↓
Header
 ↓
Content

scroll ↓

Header remains at top
```

Useful for:

- sticky headers
- table headings
- sidebars
- section navigation

---

# 33. `display` + `position` — VERY IMPORTANT

These properties solve **different problems**.

For example:

```
.card {
    display: flex;
    position: relative;
}
```

There is nothing wrong with using both.

They answer different questions:

```
display: flex
       ↓
How should the card's CHILDREN be arranged?

position: relative
       ↓
How should the card itself participate in positioning?
AND potentially:
Where should absolute children use it as a reference?
```

---

# 34. Example: Card with Flexbox + Absolute Badge

```
<div class="card">
    <div class="content">
        <h2>CSS Course</h2>
        <p>Learn Flexbox</p>
    </div>

    <span class="badge">New</span>
</div>
```

CSS:

```
.card {
    display: flex;
    position: relative;
    padding: 20px;
}

.badge {
    position: absolute;
    top: 10px;
    right: 10px;
}
```

Here:

```
.card
│
├── display:flex
│      ↓
│   controls children
│
└── position:relative
       ↓
    establishes positioning context
    for .badge
```

---

# 35. Another Very Common Example: Navbar

```
<nav class="navbar">
    <div class="logo">MySite</div>

    <div class="links">
        <a href="#">Home</a>
        <a href="#">About</a>
        <a href="#">Contact</a>
    </div>

    <button>Login</button>
</nav>
```

CSS:

```
.navbar {
    display: flex;
    align-items: center;
    justify-content: space-between;
}
```

Here:

```
display:flex
      ↓
Logo | Links | Login
```

`justify-content` controls the main-axis distribution.

`align-items` controls cross-axis alignment.

---

# 36. A Very Important Pattern: `flex: 1`

Consider:

```
<div class="navbar">
    <div class="logo">Logo</div>
    <div class="search">Search</div>
    <button>Login</button>
</div>
```

CSS:

```
.navbar {
    display: flex;
    align-items: center;
    gap: 20px;
}

.search {
    flex: 1;
}
```

Result conceptually:

```
Logo       Search Area................       Login
           ↑
           flex: 1
```

The search area takes the remaining available space.

This is why you frequently see:

```
input {
    flex: 1;
}
```

---

# 37. Another Important Pattern: `margin-left: auto`

You may also see:

```
.navbar {
    display: flex;
}

.login {
    margin-left: auto;
}
```

This pushes Login toward the right.

```
Logo       Links                 Login
                                ↑
                         margin-left:auto
```

This is another important Flexbox technique.

---

# 38. `justify-content` vs `align-items`

This is one of the biggest beginner confusions.

Don't memorize:

> justify = horizontal  
> align = vertical

That is **not always correct**.

Instead remember:

> **`justify-content` → main axis**

> **`align-items` → cross axis**

For:

```
flex-direction: row;
```

usually:

```
justify-content → horizontal
align-items     → vertical
```

For:

```
flex-direction: column;
```

they effectively switch orientation:

```
justify-content → vertical
align-items     → horizontal
```

---

# 39. Complete Flexbox Mental Model

Whenever you see:

```
.container {
    display: flex;
}
```

ask these questions **in this sequence**:

### Step 1

What is the direction?

```
flex-direction: row;
```

or:

```
flex-direction: column;
```

### Step 2

What is the main axis?

```
row    → horizontal
column → vertical
```

### Step 3

How should items be distributed?

```
justify-content
```

### Step 4

How should items align on the cross axis?

```
align-items
```

### Step 5

Should items wrap?

```
flex-wrap
```

### Step 6

What space should exist between them?

```
gap
```

### Step 7

Should individual children take extra space?

```
flex
flex-grow
flex-shrink
flex-basis
```

---

# 40. A Practical Example

```
<div class="container">
    <div class="box">HTML</div>
    <div class="box">CSS</div>
    <div class="box">JavaScript</div>
</div>
```

```
.container {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    gap: 20px;
}

.box {
    flex: 1;
    padding: 20px;
}
```

Read it like English:

> Make the container a flex container.

```
display: flex;
```

> Arrange children horizontally.

```
flex-direction: row;
```

> Distribute them along the main axis.

```
justify-content: space-between;
```

> Align them along the cross axis.

```
align-items: center;
```

> Keep a gap between them.

```
gap: 20px;
```

> Let each box share available space.

```
flex: 1;
```

---

# 41. `display: none`

Another important value:

```
display: none;
```

This removes the element from the layout.

```
.menu {
    display: none;
}
```

The element doesn't occupy its normal layout space.

Compare:

```
display: none;
```

with:

```
visibility: hidden;
```

### `display: none`

```
Element disappears
Space disappears
```

### `visibility: hidden`

```
Element disappears
Space generally remains
```

---

# 42. `display` Does NOT Mean Everything About an Element

This is important.

Don't think:

```
display: flex;
```

means:

> "This element is positioned."

No.

Think in separate categories:

```
DISPLAY
   ↓
Layout model

POSITION
   ↓
Positioning behavior

MARGIN / PADDING
   ↓
Spacing

WIDTH / HEIGHT
   ↓
Dimensions

JUSTIFY / ALIGN
   ↓
Flex/Grid alignment

TOP / LEFT / RIGHT / BOTTOM
   ↓
Position offsets
```

---

# 43. One Complete Diagram

```
                    CSS LAYOUT
                        │
          ┌─────────────┴─────────────┐
          │                           │
       DISPLAY                     POSITION
          │                           │
    ┌─────┼─────┐              ┌──────┼──────┐
    │     │     │              │      │      │
  block inline flex          relative absolute fixed
          │     │
          │     ├── flex-direction
          │     ├── justify-content
          │     ├── align-items
          │     ├── flex-wrap
          │     ├── gap
          │     └── flex
          │
      inline-block
      inline-flex
```

---

# 44. The Most Important Difference

If you remember only this, remember:

### `display`

Controls the **layout model**.

```
display: block;
display: inline;
display: inline-block;
display: flex;
```

### `position`

Controls the **positioning behavior**.

```
position: relative;
position: absolute;
position: fixed;
position: sticky;
```

### `flex`

Controls how a **flex item uses available space**.

```
flex: 1;
```

### `justify-content`

Controls distribution along the **main axis**.

### `align-items`

Controls alignment along the **cross axis**.

### `gap`

Controls spacing **between flex/grid items**.

---

# 45. Recommended Learning Sequence

Don't try to learn everything at once. Follow this order:

### Level 1 — Basic display

Learn:

```
display: block;
display: inline;
display: inline-block;
display: none;
```

Practice:

```
div
span
button
a
```

---

### Level 2 — Flexbox foundation

Learn:

```
display: flex;
```

Then:

```
flex-direction
justify-content
align-items
gap
```

---

### Level 3 — Flexbox sizing

Learn:

```
flex
flex-grow
flex-shrink
flex-basis
```

Especially:

```
flex: 1;
```

---

### Level 4 — Advanced Flexbox

Learn:

```
flex-wrap
align-self
order
```

---

### Level 5 — Position

Learn:

```
position: static;
position: relative;
position: absolute;
position: fixed;
position: sticky;
```

Then:

```
top
right
bottom
left
z-index
```

---

### Level 6 — Combine Them

Start building real components:

```
Navbar
     ↓
Cards
     ↓
Buttons
     ↓
Badge
     ↓
Dropdown
     ↓
Modal
     ↓
Tooltip
     ↓
Dashboard
```

For example, a real card may use:

```
.card {
    display: flex;
    flex-direction: column;
    gap: 10px;
    position: relative;
}

.badge {
    position: absolute;
    top: 10px;
    right: 10px;
}
```

Here you are using **two different systems together**:

```
display:flex
     ↓
controls the internal layout

position:relative
     ↓
provides positioning context
```

That distinction will make CSS much easier to understand.

## Quick Cheat Sheet

|Property|Main purpose|
|---|---|
|`display: block`|Element behaves as a block|
|`display: inline`|Element behaves like text/inline content|
|`display: inline-block`|Inline placement + box dimensions|
|`display: flex`|Creates a flex container|
|`display: inline-flex`|Inline-level flex container|
|`display: none`|Removes element from layout|
|`flex-direction`|Chooses main-axis direction|
|`justify-content`|Distributes items on main axis|
|`align-items`|Aligns items on cross axis|
|`align-self`|Overrides alignment for one item|
|`gap`|Space between items|
|`flex-wrap`|Allows items to move to another line|
|`flex: 1`|Shares available flex space|
|`flex-grow`|Controls growth|
|`flex-shrink`|Controls shrinking|
|`flex-basis`|Initial main-axis size|
|`position: relative`|Keeps flow + establishes positioning context|
|`position: absolute`|Removes from normal flow and positions against a containing block|
|`position: fixed`|Positions relative to viewport in typical use|
|`position: sticky`|Sticks after reaching a scroll threshold|

### One sentence to remember

> **`display` decides the layout system, Flexbox properties decide how children are arranged inside that system, and `position` decides how an element participates in positioning relative to its normal flow or positioning context.**