# Flexbox

- Flexbox is a 1-D layout system (lay out **rows or columns** of items).
    
- You choose a **main axis** (by `flex-direction`); the **cross axis** is perpendicular.
    
- Container properties control **how items are laid out**.
    
    Item properties control **how each item behaves** within that layout.
    

We’ll use the **same base HTML** and add different CSS for each property.

```html
<div class="container">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
</div>

```

Base CSS (for styling only, we’ll modify per example):

```css
.container {
  display: flex;
  border: 2px solid #333;
  margin: 20px;
  height: 200px; /* useful for vertical alignment demos */
}

.item {
  background: lightblue;
  border: 1px solid #333;
  padding: 20px;
  text-align: center;
  font-size: 18px;
}

```

---

## 1. **flex-direction**

📌 Defines **main axis direction** (how items are placed).

- `row` → left → right (**default**)
- `row-reverse` → right → left
- `column` → top → bottom
- `column-reverse` → bottom → top

```css
.container {
  display: flex;
  flex-direction: row; /* try row-reverse, column, column-reverse */
}

```

👉 Use case: Switching layouts (e.g., sidebar left or right).

---

## 2. **flex-wrap**

📌 Controls whether items stay in one line or wrap.

- `nowrap` (default) → all items in one row
- `wrap` → items move to the next line if needed
- `wrap-reverse` → wrap, but in reverse order (last line goes up)

```css
.container {
  display: flex;
  flex-wrap: wrap;
}

.item {
  width: 120px; /* force wrapping */
}

```

👉 Use case: Making responsive layouts (items flow to new rows).

---

## 3. **flex-flow**

📌 Shorthand for `flex-direction` + `flex-wrap`.

```css
.container {
  display: flex;
  flex-flow: row wrap; /* direction + wrap together */
}

```

👉 Cleaner than writing both separately.

---

## 4. **justify-content**

📌 Aligns items **horizontally along the main axis**.

- `flex-start` → left (default)
- `flex-end` → right
- `center` → centered
- `space-between` → equal space, edges touch
- `space-around` → equal space around items
- `space-evenly` → equal space everywhere

```css
.container {
  display: flex;
  justify-content: space-evenly;
}

```

👉 Use case: Centering menus, distributing buttons evenly.

---

## 5. **align-items**

📌 Aligns items **vertically along the cross axis**.

- `stretch` (default) → items fill height
- `flex-start` → top
- `flex-end` → bottom
- `center` → middle
- `baseline` → align text baseline

```css
.container {
  display: flex;
  align-items: center;
}

```

👉 Use case: Vertically centering items inside a navbar or box.

---

## 6. **align-content**

📌 Works **only when wrapping** is enabled.

Controls spacing **between multiple rows/columns**.

- `stretch` (default)
- `flex-start`
- `flex-end`
- `center`
- `space-between`
- `space-around`

```css
.container {
  display: flex;
  flex-wrap: wrap;
  align-content: space-between;
}
.item {
  width: 120px;
}

```

👉 Use case: Controlling how rows of cards are spaced vertically.

---

## 7. **gap**

📌 Adds spacing between items (no need for margins).

```css
.container {
  display: flex;
  gap: 20px; /* horizontal + vertical gap */
}

```

👉 Use case: Clean spacing in grids, toolbars, navigation.

---

## 8. **order (child property)**

📌 Changes **visual order** of items (doesn’t change HTML).

Default = `0`. Higher values move later.

```css
.item:nth-child(2) {
  order: 3;
}
.item:nth-child(3) {
  order: 1;
}

```

👉 Use case: Reordering elements for mobile vs desktop.

---

## 9. **flex-grow (child property)**

📌 Defines how much a flex item **expands** relative to others.

- `0` (default) → won’t grow
- `1` → grows to fill available space

```css
.item:nth-child(2) {
  flex-grow: 1;
}

```

👉 Use case: Make one item (like a search bar) expand while others stay fixed.

---

## 10. **flex-shrink (child property) (homework)**

📌 Defines how much a flex item **shrinks** when space is tight.

```css
.item {
  width: 200px;
}
.item:nth-child(2) {
  flex-shrink: 2; /* shrinks twice as fast */
}

```

👉 Use case: Control which items shrink more in small screens.

---

## 11. **flex-basis (child property)**

📌 Defines the **starting size** of an item before grow/shrink.

```css
.item:nth-child(2) {
  flex-basis: 300px;
}

```

👉 Use case: Setting a “preferred size” for cards.

---

## 12. **flex (shorthand)**

📌 Shorthand for `flex-grow`, `flex-shrink`, `flex-basis`.

```css
.item:nth-child(2) {
  flex: 1 1 200px; /* grow | shrink | basis */
}

```

👉 Cleaner way to write all 3 together.

---

## 13. **align-self (child property)**

📌 Overrides `align-items` for **individual items**.

```css
.container {
  display: flex;
  align-items: center;
}

.item:nth-child(2) {
  align-self: flex-end;
}

```

👉 Use case: Make one button drop to bottom while others stay aligned.

---

## Additional Blog (must read)