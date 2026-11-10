# CSS Flexbox and CSS Grid — Beginner to Intermediate Notes

## Learning Objectives

After completing these notes, you should be able to:

- Explain why CSS layout systems are useful.
- Understand normal document flow.
- Create a card without Flexbox or Grid.
- Use Flexbox to align content in a row or column.
- Use CSS Grid to arrange items in rows and columns.
- Build a responsive card layout.
- Decide when to use Flexbox, Grid, or both.

---

# 1. Why Do We Need Flexbox and Grid?

Imagine building a college website that displays student profiles, course cards, products, or dashboard widgets.

You can create each card using basic HTML and CSS. But when you need to align an image beside text, arrange many cards in columns, or adapt the layout to mobile screens, manually controlling every element becomes difficult.

Flexbox and Grid are CSS layout systems that make these tasks easier.

- **Flexbox** is designed primarily for arranging items along one direction: a row or a column.
- **CSS Grid** is designed for arranging items in two dimensions: rows and columns.
- **Normal document flow** is the browser's default layout behavior. Block elements generally stack vertically, while inline content flows within a line.

You do not need Flexbox or Grid for every element. Use them when they make a layout easier to control.

## Real-world examples

| Use case | Useful layout |
|---|---|
| Navigation bar with logo and links | Flexbox |
| Image and details inside a profile card | Flexbox |
| Buttons aligned in one row | Flexbox |
| Product gallery with multiple rows and columns | Grid |
| Course cards on a college website | Grid |
| Dashboard with multiple panels | Grid |
| A card gallery containing cards that each have an image and text | Grid outside, Flexbox inside when appropriate |

---

# 2. Understand Normal Document Flow

By default, many HTML elements follow normal document flow. A `div`, heading, paragraph, and similar block-level elements usually appear one below another.

## HTML

```html
<div class="card">
  <img src="https://placehold.co/100x100" alt="Student">
  <h2>Rahul Sharma</h2>
  <p>Full Stack Developer</p>
  <button>View Profile</button>
</div>
```

## CSS

```css
.card {
  width: 300px;
  padding: 20px;
  border: 1px solid #ccc;
}
```

## What happens?

- The card has a width, padding, and border.
- The image, heading, paragraph, and button appear in normal flow.
- This is valid CSS. Flexbox and Grid are not mandatory.
- If you want the image beside the details, you need another layout technique or additional CSS.

**Important:** Without Flexbox or Grid, you can still create complex layouts using normal flow, margins, positioning, inline-block, floats, and other CSS features. Flexbox and Grid simply make many modern layouts easier to build and maintain.

---

# 3. A Student Card Without Flexbox or Grid

Save this as `card-basic.html` and open it in a browser.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Basic Student Card</title>
  <style>
    .card {
      width: 300px;
      padding: 20px;
      border: 1px solid #ccc;
      border-radius: 10px;
      font-family: Arial, sans-serif;
    }

    .card img {
      width: 100px;
      height: 100px;
      object-fit: cover;
    }

    .card button {
      padding: 10px 14px;
      border: none;
      background: #2563eb;
      color: white;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div class="card">
    <img src="https://placehold.co/100x100" alt="Student photo">
    <h2>Rahul Sharma</h2>
    <p>Full Stack Developer</p>
    <p>Learning HTML, CSS, JavaScript, and React.</p>
    <button>View Profile</button>
  </div>
</body>
</html>
```

### Observation

The content appears one below another. That is perfectly fine for a simple vertical card. But what if the design asks for the image on the left and text on the right? Flexbox is a natural tool for that job.

---

# 4. CSS Flexbox

Flexbox means **Flexible Box Layout**. It helps arrange and align items along a main axis.

The main axis is horizontal for the default `flex-direction: row` and vertical for `flex-direction: column`.

## The most important Flexbox property

```css
.container {
  display: flex;
}
```

This makes the element a **flex container** and its direct children **flex items**.

## Important Flexbox properties

| Property | What it does |
|---|---|
| `display: flex` | Enables Flexbox |
| `flex-direction` | Sets the main direction: row or column |
| `justify-content` | Distributes items along the main axis |
| `align-items` | Aligns items along the cross axis |
| `gap` | Adds space between items |
| `flex-wrap` | Allows items to wrap onto another line |
| `flex` | Controls how a flex item grows or shrinks |
| `align-self` | Overrides cross-axis alignment for one item |

## 4.1 `flex-direction`

```css
.container {
  display: flex;
  flex-direction: row;
}
```

Common values:

```css
flex-direction: row;
flex-direction: column;
flex-direction: row-reverse;
flex-direction: column-reverse;
```

- `row`: items are laid out horizontally.
- `column`: items are laid out vertically.
- `row-reverse`: items are laid out in the reverse horizontal direction.
- `column-reverse`: items are laid out in the reverse vertical direction.

## 4.2 `justify-content`

This property distributes items along the main axis.

```css
.container {
  display: flex;
  justify-content: center;
}
```

Common values:

```css
justify-content: flex-start;
justify-content: flex-end;
justify-content: center;
justify-content: space-between;
justify-content: space-around;
justify-content: space-evenly;
```

Typical uses:

- `flex-start`: group items at the start.
- `center`: center the group.
- `flex-end`: group items at the end.
- `space-between`: place the first and last items at the edges, distributing space between them.
- `space-around`: distribute space around each item.
- `space-evenly`: distribute equal spaces between items and at both ends.

The exact visual direction depends on the flex direction and writing direction.

## 4.3 `align-items`

This property aligns items on the cross axis.

```css
.container {
  display: flex;
  align-items: center;
}
```

Common values:

```css
align-items: stretch;
align-items: flex-start;
align-items: flex-end;
align-items: center;
align-items: baseline;
```

A common beginner pattern for centering items in a row is:

```css
.container {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

## 4.4 `gap`

```css
.container {
  display: flex;
  gap: 20px;
}
```

`gap` creates space between items without adding margins to each child.

## 4.5 `flex-wrap`

```css
.container {
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
}
```

With `flex-wrap: wrap`, items can move onto another line when they no longer fit on the current line.

The default is `flex-wrap: nowrap`.

---

# 5. Create the Same Student Card With Flexbox

In this version, the image appears on the left and the information appears on the right.

Save as `card-flexbox.html`.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Student Card With Flexbox</title>
  <style>
    .card {
      display: flex;
      align-items: center;
      gap: 20px;
      max-width: 450px;
      padding: 20px;
      border: 1px solid #ccc;
      border-radius: 12px;
      font-family: Arial, sans-serif;
      box-shadow: 0 3px 8px #ddd;
    }

    .card img {
      width: 100px;
      height: 120px;
      object-fit: cover;
      border-radius: 8px;
    }

    .details h2 {
      margin-top: 0;
    }

    .details button {
      padding: 10px 14px;
      border: none;
      border-radius: 5px;
      background: #2563eb;
      color: white;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div class="card">
    <img src="https://placehold.co/100x120" alt="Student photo">

    <div class="details">
      <h2>Rahul Sharma</h2>
      <p>Full Stack Developer</p>
      <p>Learning HTML, CSS, JavaScript, and React.</p>
      <button>View Profile</button>
    </div>
  </div>
</body>
</html>
```

## What changed?

The most important change is:

```css
.card {
  display: flex;
  align-items: center;
  gap: 20px;
}
```

- `display: flex` lays out the direct children in a row by default.
- `align-items: center` aligns the image and details along the cross axis.
- `gap: 20px` creates space between them.

The HTML content is almost the same. The layout changes because of CSS.

**Use case:** profile cards, horizontal navigation, media objects, toolbars, and rows of buttons.

---

# 6. A Flexbox Navigation Bar

Flexbox is also useful when you want a logo on the left and navigation links on the right.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Flexbox Navbar</title>
  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: Arial, sans-serif;
    }

    .navbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 20px;
      padding: 16px 24px;
      background: #172554;
      color: white;
    }

    .logo {
      font-size: 22px;
      font-weight: bold;
    }

    .links {
      display: flex;
      flex-wrap: wrap;
      gap: 18px;
    }

    .links a {
      color: white;
      text-decoration: none;
    }
  </style>
</head>
<body>
  <nav class="navbar">
    <div class="logo">MyCollege</div>

    <div class="links">
      <a href="#">Home</a>
      <a href="#">Courses</a>
      <a href="#">Students</a>
      <a href="#">Contact</a>
    </div>
  </nav>
</body>
</html>
```

### Why Flexbox?

- `justify-content: space-between` pushes the logo and links apart.
- `align-items: center` vertically aligns them.
- `gap` controls spacing between links.
- `flex-wrap: wrap` lets links wrap when necessary, although a more complete mobile navigation may need a different design.

---

# 7. CSS Grid

CSS Grid is a layout system designed for two-dimensional layouts: rows and columns.

Enable Grid with:

```css
.container {
  display: grid;
}
```

## Important Grid properties

| Property | What it does |
|---|---|
| `display: grid` | Enables Grid |
| `grid-template-columns` | Defines columns |
| `grid-template-rows` | Defines rows |
| `gap` | Adds space between grid items |
| `column-gap` | Controls horizontal gaps |
| `row-gap` | Controls vertical gaps |
| `fr` | Represents a fraction of the available grid space |
| `repeat()` | Repeats a track definition |
| `minmax()` | Defines a minimum and maximum track size |
| `grid-column` | Controls an item's column placement or span |
| `grid-row` | Controls an item's row placement or span |

## 7.1 Two equal columns

```css
.container {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
}
```

This creates two equal-width columns.

The following is equivalent for two equal flexible columns:

```css
grid-template-columns: 1fr 1fr;
```

### What does `1fr` mean?

`fr` means a fraction of the available space in the grid container after fixed sizes and relevant spacing are accounted for.

For example:

```css
grid-template-columns: 1fr 1fr;
```

Both columns receive equal flexible space.

```css
grid-template-columns: 2fr 1fr;
```

The first column gets twice the flexible share of the second column, assuming no other sizing constraints change the result.

## 7.2 Three columns

```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
```

## 7.3 Four columns

```css
.container {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
}
```

## 7.4 Fixed and flexible columns

```css
.container {
  display: grid;
  grid-template-columns: 200px 1fr;
  gap: 20px;
}
```

This creates a 200-pixel column and a second column that uses the remaining available space, subject to grid sizing rules.

## 7.5 `minmax()`

```css
.container {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 16px;
}
```

`minmax(0, 1fr)` allows each track to shrink to zero if necessary rather than retaining an automatic minimum based on content. This can help prevent long content from forcing columns wider than expected. You may still need `overflow-wrap: anywhere` for long unbroken text.

---

# 8. Create Four Student Cards With Grid

Save as `cards-grid.html`.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Student Cards With Grid</title>
  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      padding: 24px;
      font-family: Arial, sans-serif;
      background: #f4f6f8;
    }

    .container {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 20px;
      max-width: 800px;
      margin: auto;
    }

    .card {
      padding: 20px;
      background: white;
      border: 1px solid #ddd;
      border-radius: 12px;
      box-shadow: 0 3px 8px #ddd;
    }

    .card button {
      padding: 10px 14px;
      border: none;
      border-radius: 5px;
      background: #15803d;
      color: white;
      cursor: pointer;
    }

    @media (max-width: 500px) {
      .container {
        grid-template-columns: 1fr;
      }
    }
  </style>
</head>
<body>
  <h1>Our Students</h1>

  <div class="container">
    <div class="card">
      <h2>Rahul</h2>
      <p>Frontend Developer</p>
      <button>View Profile</button>
    </div>

    <div class="card">
      <h2>Priya</h2>
      <p>Backend Developer</p>
      <button>View Profile</button>
    </div>

    <div class="card">
      <h2>Aman</h2>
      <p>UI Designer</p>
      <button>View Profile</button>
    </div>

    <div class="card">
      <h2>Neha</h2>
      <p>Full Stack Developer</p>
      <button>View Profile</button>
    </div>
  </div>
</body>
</html>
```

## What happens?

- `display: grid` enables Grid.
- `repeat(2, minmax(0, 1fr))` creates two equal flexible columns.
- `gap: 20px` creates spacing between cards.
- The cards automatically fill rows as needed.
- The media query changes the layout to one column when the viewport is 500 pixels wide or narrower.

**Use case:** course listings, product galleries, photo collections, student cards, and dashboards.

---

# 9. Responsive Grid Without Choosing a Fixed Number of Columns

You can make a card gallery adapt to the available width using `auto-fit` and `minmax()`.

```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 20px;
}
```

How it works:

- `minmax(220px, 1fr)` means each column aims to be at least 220 pixels wide and can grow to share available space.
- `auto-fit` fits as many columns as can fit in the available width and collapses unused tracks.
- As the container gets narrower, fewer columns fit.
- As it gets wider, more columns can fit.

This is often a useful starting point for responsive card galleries without writing a separate media query for every column count.

Remember: a very narrow container can still create overflow if its width is smaller than the minimum track size. Choose a suitable minimum or use a media query if needed.

---

# 10. Use Flexbox and Grid Together

In many real projects, you do not need to choose only one.

- Use **Grid** to arrange multiple cards on the page.
- Use **Flexbox** to arrange the image, title, description, and button inside each card.

Example:

```html
<div class="container">
  <article class="card">
    <img src="https://placehold.co/100x100" alt="Rahul">
    <div class="details">
      <h2>Rahul Sharma</h2>
      <p>Full Stack Developer</p>
      <button>View Profile</button>
    </div>
  </article>

  <article class="card">
    <img src="https://placehold.co/100x100" alt="Priya">
    <div class="details">
      <h2>Priya Verma</h2>
      <p>Frontend Developer</p>
      <button>View Profile</button>
    </div>
  </article>

  <article class="card">
    <img src="https://placehold.co/100x100" alt="Aman">
    <div class="details">
      <h2>Aman Singh</h2>
      <p>Backend Developer</p>
      <button>View Profile</button>
    </div>
  </article>

  <article class="card">
    <img src="https://placehold.co/100x100" alt="Neha">
    <div class="details">
      <h2>Neha Gupta</h2>
      <p>UI Designer</p>
      <button>View Profile</button>
    </div>
  </article>
</div>
```

```css
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  padding: 24px;
  font-family: Arial, sans-serif;
  background: #f4f6f8;
}

.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 20px;
}

.card {
  display: flex;
  align-items: center;
  gap: 16px;
  min-width: 0;
  padding: 16px;
  background: white;
  border: 1px solid #ddd;
  border-radius: 12px;
}

.card img {
  flex: 0 0 80px;
  width: 80px;
  height: 80px;
  object-fit: cover;
  border-radius: 8px;
}

.details {
  min-width: 0;
}

.details h2 {
  margin-top: 0;
}

.details p {
  overflow-wrap: anywhere;
}

button {
  padding: 9px 12px;
  border: none;
  border-radius: 5px;
  background: #2563eb;
  color: white;
  cursor: pointer;
}
```

### Why is this approach useful?

The outer Grid controls how many cards fit in each row. The Flexbox inside each card aligns the photo and the details. Each layout system handles the problem it is best suited to solve.

---

# 11. Flexbox vs Grid

| Feature | Flexbox | CSS Grid |
|---|---|---|
| Main purpose | One-dimensional layout | Two-dimensional layout |
| Main arrangement | Row or column | Rows and columns |
| Best for | Aligning and distributing items | Building structured page layouts |
| Typical example | Navbar or card internals | Card gallery or dashboard |
| Spacing | `gap` | `gap`, `row-gap`, `column-gap` |
| Responsive design | Yes | Yes |
| Can items wrap? | Yes, with `flex-wrap` | Grid creates additional rows as needed |
| Can span tracks? | Not in the same track-based way as Grid | Yes, with `grid-column` and `grid-row` |

## Simple rule to remember

- **Flexbox:** How should these items be aligned in this row or column?
- **Grid:** How should these items be arranged across rows and columns?

Neither tool is universally better. Pick the one that makes the intended layout simplest.

---

# 12. Common Beginner Mistakes

### Mistake 1: Applying `justify-content` without enabling Flexbox or Grid

```css
.container {
  justify-content: center;
}
```

By itself, this will not create a Flexbox layout.

Use:

```css
.container {
  display: flex;
  justify-content: center;
}
```

or enable Grid if that is the intended layout.

### Mistake 2: Confusing the two axes in Flexbox

For `flex-direction: row`:

- Main axis is horizontal.
- Cross axis is vertical.
- `justify-content` works along the main axis.
- `align-items` works along the cross axis.

For `flex-direction: column`, the axes switch.

### Mistake 3: Forgetting the direct-child rule

`display: flex` affects the element's direct children, not every descendant automatically.

```html
<div class="container">
  <div class="card">
    <h2>Rahul</h2>
    <p>Developer</p>
  </div>
</div>
```

If `.container` uses Flexbox, its direct flex item is `.card`. The heading and paragraph remain in normal flow inside `.card` unless another layout is applied there.

### Mistake 4: Using fixed widths everywhere

Fixed widths can cause overflow on smaller screens. Consider flexible sizing, `max-width`, `minmax()`, `auto-fit`, and media queries where appropriate.

### Mistake 5: Forgetting `box-sizing`

A useful baseline is:

```css
* {
  box-sizing: border-box;
}
```

With `border-box`, declared width and height include padding and borders, which often makes card sizing easier to reason about.

### Mistake 6: Using Grid for everything

Grid can arrange many layouts, but Flexbox may be simpler for a navbar, a row of buttons, or image-and-text alignment. Choose based on the layout requirement, not merely because the property is available.

---

# 13. Practice Tasks

Try each task before looking at the solutions.

## Beginner tasks

- [ ] **Task 1:** Create a basic student card using normal CSS flow, without Flexbox or Grid.
- [ ] **Task 2:** Use Flexbox to position the image on the left and student details on the right.
- [ ] **Task 3:** Center three buttons horizontally using Flexbox.
- [ ] **Task 4:** Create four student cards in two equal Grid columns.
- [ ] **Task 5:** Add `gap: 20px` between cards.

## Intermediate tasks

- [ ] **Task 6:** Make the Grid layout use one column on screens 500 pixels wide or narrower.
- [ ] **Task 7:** Create a responsive card gallery using `repeat(auto-fit, minmax(220px, 1fr))`.
- [ ] **Task 8:** Build a navbar using Flexbox with the logo on the left and links on the right.
- [ ] **Task 9:** Build a four-card layout with Grid and arrange each card's contents with Flexbox.
- [ ] **Task 10:** Experiment with `justify-content`, `align-items`, `flex-direction`, and `flex-wrap`. Record how each changes the layout.

## Critical-thinking questions

1. Can you create a card without Flexbox or Grid? Explain how.
2. Why might Flexbox be a better choice than Grid for a navigation bar?
3. Why is Grid useful for a gallery containing many cards?
4. What is the difference between `justify-content` and `align-items` when `flex-direction: row`?
5. What changes when `flex-direction` becomes `column`?
6. How does `1fr` differ from a fixed `200px` grid column?
7. Why might `auto-fit` and `minmax()` be useful in responsive layouts?
8. When would combining Grid and Flexbox make sense?

---

# 14. Sample Solutions for Practice Tasks

## Solution: Three centered buttons

```html
<div class="buttons">
  <button>Home</button>
  <button>Courses</button>
  <button>Contact</button>
</div>
```

```css
.buttons {
  display: flex;
  justify-content: center;
  gap: 12px;
}
```

## Solution: Two-column Grid

```css
.container {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
}
```

## Solution: Responsive Grid

```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 20px;
}
```

## Solution: Navbar

```css
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 20px;
}
```

## Solution: Grid outside, Flexbox inside

```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 20px;
}

.card {
  display: flex;
  align-items: center;
  gap: 16px;
}
```

---

# 15. Quick Revision

- Normal document flow is the browser's default arrangement of content.
- Flexbox arranges and aligns items along a main axis.
- Grid arranges items using rows and columns.
- `display: flex` enables Flexbox.
- `display: grid` enables Grid.
- `justify-content` distributes items along the main axis in Flexbox.
- `align-items` aligns items along the cross axis in Flexbox.
- `gap` creates spacing between items in both Flexbox and Grid.
- `grid-template-columns` defines Grid columns.
- `repeat(2, 1fr)` creates two equal flexible columns.
- `repeat(auto-fit, minmax(220px, 1fr))` is a useful responsive card-gallery pattern.
- Media queries can change layouts at chosen viewport widths.
- A common real-world pattern is **Grid for the card gallery and Flexbox inside each card**.

## Final takeaway

You do not need Flexbox or Grid just to create a card. You use them to make layouts easier to align, organize, adapt, and maintain as a website becomes more complex.
