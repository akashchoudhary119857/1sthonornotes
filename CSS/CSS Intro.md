## 1 — What is CSS (short recap)

**CSS (Cascading Style Sheets)** styles the HTML structure. It decides how elements look and how they are laid out.

- **Cascading**: When multiple rules target the same element, the browser decides which one “wins.”
- **Separation of concerns**: Keep **structure** (HTML) separate from **style** (CSS).

Role summary:

- Visual presentation: colors, fonts, spacing, sizing.
- Layout: positioning, flex/grid, responsive rules.
- Interactivity hooks: pseudo-classes for hover/focus/active.

---

## 2 — Ways to include CSS (with pros/cons & exact usage)

1. **Inline**

```html
<p style="color:blue; margin:10px;">Hi</p>

```

- Pros: immediate, overrides other rules (high priority).
- Cons: not reusable, clutters HTML, poor separation of concerns.

1. **Internal (Embedded)**

```html
<head>
  <style>
    p { color: blue; }
  </style>
</head>

```

- Pros: good for single page or demos.
- Cons: not reusable across pages.

1. **External**

```html
<link rel="stylesheet" href="styles.css">

```

- Pros: reusable, cacheable, maintainable — **recommended** for production.
- Extra tips: use `rel="preload"` for performance optimization (advanced).

---

## 3 — CSS syntax & anatomy

```css
selector {           /* selector */
  property: value;   /* declaration */
  property2: value2;
}

```

- **Selector** → target element(s).
- **Declaration block** → between `{}`.
- **Property** → property name (e.g., `color`, `margin`).
- **Value** → property value (e.g., `#ff0000`, `10px`).

Comments: `/* This is a comment */`

---

## 4 — Selectors (comprehensive)

### Basic

- **Type / Element**: `p { }`
- **Class**: `.card { }`
- **ID**: `#main { }`
- **Universal**: `*{ }` (selects all elements) — expensive; use sparingly.

### Attribute selectors

`[attr]` → Selects elements that **have the attribute**

```html
<input type="text" placeholder="Enter name">
<input type="password" placeholder="Enter password">
<input placeholder="No type attribute!">

```

```css
input[type] {
  border: 2px solid green; /* applies only to inputs WITH type attribute */
}

```

✅ The last input won’t get styled since it doesn’t have `type`.

---

`[attr="value"]` → Selects elements with an **exact match**

```html
<a href="<https://google.com>">Google</a>
<a href="<https://github.com>">GitHub</a>

```

```css
a[href="<https://google.com>"] {
  color: red;
}

```

✅ Only the Google link will turn red.

---

`[attr~="value"]` → Selects elements where the attribute contains a **whitespace-separated list**

```html
<p class="card highlight">Card</p>
<p class="card">Normal</p>

```

```css
p[class~="highlight"] {
  background: yellow;
}

```

✅ Only the first `<p>` matches because `"card highlight"` contains `"highlight"` as a **whole word**.

---

`[attr|="value"]` → Matches **exact value** or value followed by a **hyphen (-)**

👉 Mostly used for **language codes**.

```html
<p lang="en">Hello</p>
<p lang="en-US">Howdy</p>
<p lang="fr">Bonjour</p>

```

```css
p[lang|="en"] {
  color: blue;
}

```

✅ Matches `en` and `en-US` but NOT `fr`.

---

### `[attr^="val"]` → Attribute **starts with** value

```html
<a href="<https://example.com/page>">Page</a>
<a href="<https://example.org/home>">Home</a>
<a href="<http://oldsite.com>">Old</a>

```

```css
a[href^="<https://example.com>"] {
  font-weight: bold;
}

```

✅ First link matches because it starts with `https://example.com`.

---

`[attr$="val"]` → Attribute **ends with** value

```html
<img src="image.png">
<img src="photo.jpg">
<img src="icon.svg">

```

```css
img[src$=".png"] {
  border: 2px solid blue;
}

```

✅ Only the `.png` image gets a border.

---

`[attr*="val"]` → Attribute **contains substring**

```html
<a href="<https://example.com/help>">Help</a>
<a href="<https://example.com/contact>">Contact</a>
<a href="<https://example.com/profile>">Profile</a>

```

```css
a[href*="contact"] {
  color: green;
}

```

✅ Only the **contact link** matches because `contact` is inside the `href`.

---

Summary Table

|Selector|Meaning|Example Match|
|---|---|---|
|`[attr]`|Has attribute|`<input type="text">`|
|`[attr="value"]`|Exact match|`href="<https://google.com>"`|
|`[attr~="value"]`|Contains **word** in space list|`class="card highlight"`|
|`[attr|="value"]`|Exact or starts with `value-`|
|`[attr^="val"]`|Starts with|`href="<https://example.com>..."`|
|`[attr$="val"]`|Ends with|`src="file.png"`|
|`[attr*="val"]`|Contains substring|`href="...contact..."`|

### Combinators

- **Descendant** (space): `nav a { }` — any `a` inside `nav`.
- **Child** (`>`): `ul > li { }` — direct children only.
- **Adjacent sibling** (`+`): `h2 + p { }` — `p` immediately after `h2`.
- **General sibling** (`~`): `h2 ~ p { }` — any `p` after `h2` (same parent).
- example:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Combinators Example</title>
  <style>
    /* 1. Descendant (any <a> inside nav) */
    nav a {
      color: blue;
      text-decoration: none;
      font-weight: bold;
    }

    /* 2. Child (only direct <li> of <ul>) */
    ul > li {
      color: green;
    }

    /* 3. Adjacent sibling (first <p> after an <h2>) */
    h2 + p {
      background: yellow;
      padding: 5px;
    }

    /* 4. General sibling (all <p> after an <h2>) */
    h2 ~ p {
      color: purple;
    }
  </style>
</head>
<body>

  <!-- Descendant -->
  <nav>
    <a href="#">Home</a> | <a href="#">About</a> | <a href="#">Contact</a>
  </nav>

  <!-- Child -->
  <ul>
    <li>Direct Child 1</li>
    <li>Direct Child 2</li>
    <li>
      Nested List
      <ul>
        <li>Nested Child (won’t be green)</li>
      </ul>
    </li>
  </ul>

  <!-- Adjacent & General sibling -->
  <h2>Section Title</h2>
  <p>This is the FIRST paragraph after h2 (adjacent sibling → yellow background).</p>
  <p>This is ANOTHER paragraph after h2 (general sibling → purple text).</p>
  <p>Yet another paragraph (also general sibling → purple text).</p>

</body>
</html>

```

### Grouping

- `h1, h2, p { font-family: Arial; }` — apply same rules.

### Pseudo-classes (dynamic states & structural)

- `:hover`, `:active`, `:focus` — user interaction
    
- `:first-child`, `:last-child`, `:nth-child(n)` — structural
    
- `:nth-of-type(n)`, `:not(selector)`, `:empty`, `:checked`, `:disabled`, `:valid`, `:invalid`, `:target`, `:root`, `:lang()`
    
    Example:
    

```css
button:disabled { opacity: 0.6; cursor: not-allowed; }
li:nth-child(odd) { background: #f7f7f7; }
```

### Pseudo-elements (create/target sub-part)

- `::before`, `::after` — insert generated content (requires `content:`)
    
- `::first-line`, `::first-letter`, `::selection`, `::placeholder`
    
    Example:
    

```css
p::first-line { font-weight: bold; }
a::after { content: " →"; }

```

> Note: Modern syntax uses double colon :: but single : works for older pseudo-elements.

---

## 5 — Specificity & Cascade — how CSS decides what wins

Order of decision:

1. Importance (`!important` rules win over normal ones)
2. Origin: user-agent < user < author < inline (browser defaults < user styles < page styles < inline).
3. **Specificity** (if same origin and importance)
4. Source order (later definitions override earlier ones if specificity ties)

**Specificity weights** (conceptual tuple): `(a, b, c, d)`

- `a` = inline styles (1 if inline, else 0)
- `b` = number of ID selectors
- `c` = number of class/attribute/pseudo-class selectors
- `d` = number of element/pseudo-element selectors

Examples:

- `#nav .item a` → (0,1,1,1)
- `.btn` → (0,0,1,0)
- `div` → (0,0,0,1)

_**If same specificity: the rule that appears later in the CSS wins.**_

`!important`:

```css
.btn { color: red !important; }  /* overrides most other declarations */

```

Use sparingly — makes maintenance hard.

---

## 6 — Inheritance

Some CSS properties _inherit_ (they naturally propagate from parent to child), others do not.

**Commonly inherited properties**:

- `color`, `font-family`, `font-size`, `line-height`, `visibility`, `text-align`, `list-style`, `text-indent`

**Non-inherited**:

- `margin`, `padding`, `border`, `width`, `height`, `background`, `display` (these are per-element box properties)

Forced inheritance / resets:

- `inherit` — force inherited value
- `initial` — set to initial value (browser default)
- `unset` — acts like `inherit` where property is inheritable, otherwise like `initial`
- `revert` — revert to user-agent/user style as applicable

Example:

```css
body { color: #333; }
p { color: inherit; }   /* p will use #333 */

```

---

## 7 — CSS Variables (Custom Properties)

Define:

```css
:root {
  --main-color: #0b6;
  --spacing: 1rem;
}
```

Use:

```css
button { background: var(--main-color); padding: calc(var(--spacing) * 1.2); }

```

- Support fallback: `var(--foo, #000)`
- Scope: defined on any selector — `:root` makes global.

---

## 8 — Units (essential ones)

- **Absolute (fixed)**: `px`, `pt`, `cm` (avoid for responsive)
- **Relative**:
    - `em` — relative to font-size of element (compounds)
    - `rem` — relative to root (`html`) font-size (stable)
    - `%` — relative to containing block or property context
    - `vw`, `vh` — viewport width/height (1vw = 1% viewport width)
    - `vmin`, `vmax`
    - `ch` — width of `0` character
    - `ex` — x-height
- **Functions**: `calc()`, `min()`, `max()`, `clamp()` — powerful for responsive sizing.

Example:

```css
h1 { font-size: clamp(1.5rem, 4vw, 3rem); }
```

---

## 9 — Useful Dev Tips

- Always use external stylesheet for real projects.
- Keep selectors simple and readable — deep selectors are brittle.
- Prefer class-based selectors for components (`.card`, `.btn`).
- Reset/normalize CSS at project start (e.g., `{ box-sizing: border-box; }`).
- Use CSS variables for theme/colors/spacing to make changes easy.

---

## 10 — Exercises (practice)

1. Write a selector that targets every `<input>` with `type` starting with `date`.
    - Answer: `input[type^="date"] { }`
2. Which selector is more specific: `.nav a` or `#menu a`?
    - Answer: `#menu a` (ID is higher specificity).
3. Use a pseudo-element to add an icon → `a::after { content: " 🔗"; }`.