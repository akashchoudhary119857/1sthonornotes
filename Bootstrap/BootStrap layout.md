## Short summary (what you’ll master)

After this seating you should be able to:

- Explain how Bootstrap’s grid works (12 columns, breakpoints).
- Use `.container`, `.row`, `.col-*`, `.col-auto`, `.col` and responsive variants.
- Control gutters, spacing, alignment, ordering and nesting.
- Build responsive layouts: sidebar/content, card grids, forms.
- Debug common issues (overflow, content not wrapping, unequal heights).
- Know when to use Bootstrap grid vs plain CSS Grid / Flexbox.

---

## 1) How Bootstrap layout works — conceptually (THE WHY)

- **Bootstrap Grid = a flexbox-based 12-column system.** Each `.row` is a flex container. `.col-*` are flex items.
- The **grid simplifies responsive layouts** by providing classes that change how many of the 12 columns a cell occupies at different breakpoints.
- Bootstrap is **mobile-first**: classes without breakpoints apply to all sizes, while `col-md-6` applies from `md` and up.
- **Gutters** = spacing between columns implemented via row negative margins + column padding.

---

## 2) Containers — the outer wrapper

### Types

- `.container` → fixed widths at breakpoints (centered).
- `.container-fluid` → always `100%` width.
- `.container-{breakpoint}` (e.g. `.container-md`) → fluid until that breakpoint, then fixed.

### Fixed widths (Bootstrap 5 typical values)

(container max-widths at each breakpoint)

- `sm` → 540px
- `md` → 720px
- `lg` → 960px
- `xl` → 1140px
- `xxl` → 1320px

```html
<div class="container"> <!-- content centered with max-width -->
  ...
</div>

<div class="container-fluid"> <!-- full width -->
  ...
</div>

```

**Why choose which?**

- Use `.container` for centered page content (most sites).
- Use `.container-fluid` for edge-to-edge components (hero backgrounds, footer bars).
- Use `.container-md` when you want fluid on small screens and constrained on larger.

---

## 3) Row & Columns — the 12-column core

### Basic structure

```html
<div class="container">
  <div class="row">
    <div class="col">A</div>
    <div class="col">B</div>
    <div class="col">C</div>
  </div>
</div>

```

- `.row` creates a horizontal group and sets up gutters.
- `.col` auto-sizes to divide available space equally.

### Column sizing

- `.col` → auto-equal columns
- `.col-#` → fixed fraction of 12 (e.g. `.col-4` = 4/12 = 33.33%)
- `.col-sm-#, .col-md-#, .col-lg-#` → responsive at breakpoints

```html
<div class="row">
  <div class="col-4">4 of 12</div>
  <div class="col-8">8 of 12</div>
</div>

```

### Auto-layout columns (flex behavior)

- `col` (no number) behaves like `flex: 1 0 0%`.
- Mix `.col` with `.col-4`: numbered columns get their width, `.col` share remaining space.

```html
<div class="row">
  <div class="col-3">fixed</div>
  <div class="col">flex 1</div>
  <div class="col">flex 2</div>
</div>

```

### `.col-auto`

- Width fits content (width determined by content)

```html
<div class="row">
  <div class="col-auto">I fit my content</div>
  <div class="col">I take leftover space</div>
</div>

```

---

## 4) Responsive breakpoints — quick reference

|Prefix|Breakpoint|Meaning|
|---|---|---|
|none / `col-`|XS: <576px|base (mobile)|
|`sm`|≥576px|small devices|
|`md`|≥768px|tablets|
|`lg`|≥992px|small desktops|
|`xl`|≥1200px|large desktops|
|`xxl`|≥1400px|very large screens|

**Example**

```html
<div class="col-12 col-md-6 col-lg-4">Responsive</div>

```

- mobile: full width
- md+: half width
- lg+: one-third width

---

## 5) Gutters (spacing between columns)

- Implemented by `-bs-gutter-x` and `-bs-gutter-y` variables.
- Classes: `g-#` sets both row and column gap (`g-0` … `g-5`).
- `gx-#` controls horizontal gutter, `gy-#` controls vertical gutter.

```html
<div class="row g-3">
  <div class="col">... </div>
  <div class="col">... </div>
</div>

<div class="row gx-0"> <!-- no horizontal spacing -->
  ...
</div>

```

**To remove all gutters:** `.g-0` or `.row gx-0 gy-0`

**Why gutters matter:** Bootstrap uses negative margins on `.row` and equal horizontal padding on `.col` to create gutters. Removing gutters eliminates that padding.

---

## 6) Nesting rows & columns

- To nest columns you must put `.row` inside a `.col` and then `.col` children within that row.

```html
<div class="row">
  <div class="col-8">
    <div class="row">
      <div class="col-6">Nested 1</div>
      <div class="col-6">Nested 2</div>
    </div>
  </div>
  <div class="col-4">Side</div>
</div>

```

**Important:** Nested `.row` will produce its own gutters — plan accordingly.

---

## 7) Quick helpers for multi-column layout

### `row-cols-*`

- Auto-splits row into equal columns without explicitly counting `col`

```html
<div class="row row-cols-1 row-cols-md-3 g-3">
  <div class="col">card 1</div>
  <div class="col">card 2</div>
  <div class="col">card 3</div>
  <div class="col">card 4</div>
</div>

```

- Mobile: 1 column, md+: 3 columns (cards flow accordingly).

---

## 8) Alignment & vertical behavior

### Horizontal alignment (main axis)

- `.justify-content-start|center|end|between|around|evenly` — placed on `.row` (flex container)

```html
<div class="row justify-content-center">
  <div class="col-4">centered</div>
</div>

```

### Vertical alignment (cross axis)

- `.align-items-start|center|end|baseline|stretch` — placed on `.row`

```html
<div class="row align-items-center" style="height:200px">
  <div class="col">I am centered vertically</div>
</div>

```

### Individual column alignment

- `.align-self-start|center|end|stretch` on `.col` overrides parent.

**Equal height columns**

- `.row` defaults to `align-items: stretch` so columns stretch to same height. If you put content with `min-height` or nested flex you can make inner elements equal height:

```html
<div class="row align-items-stretch">
  <div class="col">
    <div class="card h-100"> <!-- h-100 fills height -->
      <div class="card-body">...</div>
    </div>
  </div>
</div>

```

- Use `.h-100` on the `.card` and `align-items-stretch` for equal card heights.

---

## 9) Ordering & offsets

### Order (change visual order without changing DOM)

- Classes: `.order-0` … `.order-5` and `.order-first`, `.order-last`.
- Responsive variants: `.order-md-1`, etc.

```html
<div class="row">
  <div class="col order-md-2">Second on md+</div>
  <div class="col order-md-1">First on md+</div>
</div>

```

**Note (accessibility):** changing visual order can confuse keyboard/screen reader users. If reordering for layout, ensure DOM order remains logical for reading/keyboard navigation.

### Offsets (shift columns to the right)

- `.offset-1` … `.offset-11` and responsive `.offset-md-3`

```html
<div class="row">
  <div class="col-md-4 offset-md-2">starts at column 3</div>
</div>

```

---

## 10) Useful utilities that interact with grid

- **Display**: `.d-flex`, `.d-block`, `.d-none`, `.d-md-flex` (responsive)
- **Spacing**: `m-*, p-*` (margins/padding). `mx-auto` centers horizontally.
- **Sizing**: `.w-100`, `.h-100`
- **Text**: `.text-center`, `.text-md-right`, `.lead`, `.small`
- **Borders / bg**: `.border`, `.bg-light`, `.rounded`
- **Flex helpers**: `.flex-row`, `.flex-column`, `.flex-wrap`, `.gap-*`

Example horizontal layout using flex + grid:

```html
<header class="d-flex justify-content-between align-items-center p-3">
  <div class="brand">Logo</div>
  <nav class="d-none d-md-block">menu</nav>
</header>

```

---

## 11) Images, media & forms in the grid

### Images

- `.img-fluid` → `max-width:100%; height:auto;` responsive images.

```html
<img src="..." class="img-fluid rounded" alt="...">

```

### Responsive forms

- Use `.row` + `.col-md-*` to make inputs multi-column at larger widths:

```html
<form>
  <div class="row g-3">
    <div class="col-12 col-md-6">
      <label class="form-label">First name</label>
      <input class="form-control" type="text">
    </div>
    <div class="col-12 col-md-6">
      <label class="form-label">Last name</label>
      <input class="form-control" type="text">
    </div>
  </div>
</form>

```

- For horizontal form labels: use `.row` + `.col-form-label` on `<label>` with `.col-sm-2`, `.col-sm-10`.

---

## 12) Example: Hero + 3-Column features (full code)

Copy-paste and test:

```html
<!doctype html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Bootstrap Grid — Example</title>
  <link href="<https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css>" rel="stylesheet">
</head>
<body>

<!-- Container -->
<div class="container my-5">
  <!-- Hero row -->
  <div class="row align-items-center">
    <div class="col-12 col-md-7">
      <h1 class="display-5">Product name</h1>
      <p class="lead">Short description goes here. Catch attention.</p>
      <p><a class="btn btn-primary btn-lg" href="#">Get started</a></p>
    </div>
    <div class="col-12 col-md-5 text-center">
      <img src="<https://via.placeholder.com/360x240>" class="img-fluid rounded" alt="hero">
    </div>
  </div>

  <!-- Features (3 cols on md+, stacked on xs) -->
  <div class="row text-center mt-5">
    <div class="col-12 col-md-4 mb-3">
      <div class="p-4 bg-light rounded h-100">Feature A</div>
    </div>
    <div class="col-12 col-md-4 mb-3">
      <div class="p-4 bg-light rounded h-100">Feature B</div>
    </div>
    <div class="col-12 col-md-4 mb-3">
      <div class="p-4 bg-light rounded h-100">Feature C</div>
    </div>
  </div>
</div>

<script src="<https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js>"></script>
</body>
</html>

```

**Notes**

- `col-12 col-md-7` ensures hero text full width on mobile and 7/12 on md+.
- `.h-100` inside the feature box makes boxes equal height when parent row stretches.

---

## 13) Common pitfalls & fixes

### 1. Columns overflow and horizontal scrollbar

**Cause:** wide element (image/table) inside column, or gutters mis-specified.

**Fixes:**

- Add `.img-fluid` for images.
- Use `overflow-auto` for wide content.
- Use `g-0` or correct container padding if gutters cause scroll.

### 2. Content won’t shrink inside column (long words)

**Cause:** flex items default `min-width:auto` (content forces min size).

**Fix:**

```css
.col { min-width: 0; } /* or apply to specific flex child */

```

Also use `word-break: break-word` or `overflow-wrap: anywhere`.

### 3. Nested row gutters too wide

**Cause:** nested `.row` adds gutter padding over existing column padding.

**Fix:** Accept nested gutters or use `.g-0` on inner row, or adjust styling.

### 4. Vertical centering not working

**Cause:** `.row` is not tall enough or `align-items-*` not set.

**Fix:** Use `.align-items-center` on `.row` and ensure row has a height (or use `py-5`).

### 5. Visual order differs from DOM order (accessibility)

**Problem:** using `.order-*` changes visual order but keyboard/tab order follows DOM.

**Advice:** Keep DOM order logical; only use `.order-*` for minor layout changes, not content flow.

---

## 14) Debugging tips & quick utilities

- Temporarily add borders/backgrounds to see grid:

```css
.row * { outline: 1px dashed rgba(0,0,0,.1); } /* only for debugging */

```

- Or in markup:

```html
<div class="col bg-info bg-opacity-10 border">...</div>

```

- Use browser devtools responsive simulator (toggle device toolbar) and test breakpoints.

---

## 15) Accessibility & semantic considerations

- Use semantic elements (`<header>`, `<main>`, `<nav>`, `<footer>`) inside grid.
- Keep DOM order meaningful (screen readers, keyboard navigation).
- Use ARIA only where necessary; prefer semantic HTML.
- For forms inside grid, ensure `<label for>` properly references inputs.

---

## 16) When to use Bootstrap grid vs CSS Grid / raw Flexbox

- **Bootstrap grid** = great for standard page layouts, quick responsive columns, and when you want to leverage utility classes.
- **CSS Grid** = better for complex two-dimensional layouts (explicit row/column positioning).
- **Flexbox** = excellent for 1-dimensional layouts (navbars, alignment inside a row).
- You can mix: use CSS Grid for main complex layout blocks and Bootstrap grid for simpler content flows.

---

## 17) Extra reading (blogs, tutorials, docs)

(Use these for deeper conceptual reading and additional patterns)

- **Official Bootstrap docs**
    
    - Grid: [https://getbootstrap.com/docs/5.3/layout/grid/](https://getbootstrap.com/docs/5.3/layout/grid/)
    - Containers: [https://getbootstrap.com/docs/5.3/layout/containers/](https://getbootstrap.com/docs/5.3/layout/containers/)
- **FreeCodeCamp** — Bootstrap Grid Tutorial
    
    [https://www.freecodecamp.org/news/bootstrap-grid-tutorial/](https://www.freecodecamp.org/news/bootstrap-grid-tutorial/)
    
- **CSS-Tricks** — Bootstrap Grid System reference & patterns
    
    [https://css-tricks.com/snippets/css/bootstrap-grid-system/](https://css-tricks.com/snippets/css/bootstrap-grid-system/)
    
- **MDN** — Flexbox guide (to understand underlying flex behavior)
    
    [https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout)
    
- **Smashing Magazine** — articles on responsive design and Bootstrap patterns (search “Smashing Magazine Bootstrap grid”)
    
- **Official Bootstrap blog** — for patterns, utilities, and advanced usage.
    

---

## 18) Short cheat-sheet (most used classes for layout)

- Containers: `.container`, `.container-fluid`, `.container-md`
- Rows/cols: `.row`, `.col`, `.col-4`, `.col-md-6`, `.col-auto`
- Auto-collapsing: `row-cols-1 row-cols-md-3`
- Gutters: `g-0, g-1, g-2, g-3, gx-3, gy-2`
- Offsets: `.offset-md-3`
- Order: `.order-0` … `.order-5`, `.order-md-1`
- Align: `.align-items-center`, `.justify-content-between`
- Utilities: `.d-flex`, `.flex-column`, `.h-100`, `.img-fluid`, `.mx-auto`, `.px-3`, `.py-4`, `.text-center`

---

## 19) Practice exercises (10 quick drills)

1. Make a 4-column grid that becomes 2 columns at `md` and 1 column on mobile.
2. Build a header: left logo, center nav (hidden on xs), right search button (use `.d-none d-md-block`).
3. Create card grid with `row-cols-md-3` and consistent gutters.
4. Make a form with two inputs side-by-side on `md+` and stacked on mobile.
5. Make an image + caption where image is 40% on `lg+` and full width on xs.
6. Use `.offset-md-2` to center a narrow column inside a row.
7. Demo `.col-auto` next to `.col` to see content-fitting behavior.
8. Create vertically centered text inside a fixed-height row with `.align-items-center`.
9. Reorder 3 columns on `md+` so middle column displays first visually.
10. Debug an overflowing column: intentionally insert a long unbroken word and fix it.