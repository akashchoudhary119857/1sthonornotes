## 1. **Typography in Bootstrap**

Typography is all about **how text looks** on a webpage: font, size, color, alignment, and weight. Bootstrap provides ready-to-use classes so you don’t have to write custom CSS.

---

### 🔹 1.1 Headings

Bootstrap allows you to style text like HTML headings (`h1`–`h6`) with **classes**:

```html
<p class="h1">Heading 1</p>
<p class="h2">Heading 2</p>
<p class="h3">Heading 3</p>
<p class="h4">Heading 4</p>
<p class="h5">Heading 5</p>
<p class="h6">Heading 6</p>

```

✅ Works even on a `<p>` or `<div>` element.

Useful when you want **heading styles** but don’t want to break semantic HTML.

---

### 🔹 1.2 Display Headings

**Bigger, bolder headings** for hero sections.

```html
<h1 class="display-1">Display 1</h1>
<h1 class="display-2">Display 2</h1>
<h1 class="display-3">Display 3</h1>
<h1 class="display-4">Display 4</h1>
<h1 class="display-5">Display 5</h1>
<h1 class="display-6">Display 6</h1>

```

✅ Great for **landing pages, banners, and highlights**.

---

### 🔹 1.3 Lead Text

Makes paragraphs **stand out**.

```html
<p class="lead">This is an important intro paragraph.</p>

```

---

### 🔹 1.4 Text Alignment

- `.text-start` → Left align
- `.text-center` → Center align
- `.text-end` → Right align

```html
<p class="text-start">Left aligned</p>
<p class="text-center">Centered text</p>
<p class="text-end">Right aligned</p>

```

---

### 🔹 1.5 Font Weight & Style

- `.fw-bold` → Bold
- `.fw-normal` → Normal
- `.fw-light` → Light
- `.fst-italic` → Italic

```html
<p class="fw-bold">Bold Text</p>
<p class="fw-light">Light Text</p>
<p class="fst-italic">Italic Text</p>

```

---

### 🔹 1.6 Text Transform

- `.text-uppercase` → ALL CAPS
- `.text-lowercase` → lowercase
- `.text-capitalize` → Capitalize Each Word

```html
<p class="text-uppercase">uppercase text</p>
<p class="text-lowercase">LOWERCASE</p>
<p class="text-capitalize">capitalize each word</p>

```

---

### 📝 Practice Task – Typography

- Make a hero section with a **`display-2` heading**.
- Add a **lead paragraph** below it.
- Style another line with **bold italic uppercase**.

---

## 2. **Colors in Bootstrap**

Bootstrap comes with a **color system** for both **text** and **backgrounds**.

---

### 🔹 2.1 Text Colors

```html
<p class="text-primary">Primary text</p>
<p class="text-secondary">Secondary text</p>
<p class="text-success">Success text</p>
<p class="text-danger">Danger text</p>
<p class="text-warning">Warning text</p>
<p class="text-info">Info text</p>
<p class="text-dark">Dark text</p>
<p class="text-muted">Muted (faded) text</p>

```

---

### 🔹 2.2 Background Colors

```html
<div class="bg-primary text-white p-3">Primary Background</div>
<div class="bg-success text-white p-3">Success Background</div>
<div class="bg-danger text-white p-3">Danger Background</div>
<div class="bg-warning text-dark p-3">Warning Background</div>
<div class="bg-light text-dark p-3">Light Background</div>

```

✅ Use `text-*` with `bg-*` for best contrast.

---

### 🔹 2.3 Subtle Colors (Bootstrap 5+)

Lighter variations for soft backgrounds:

```html
<div class="bg-primary-subtle text-primary p-3">Primary Subtle</div>
<div class="bg-danger-subtle text-danger p-3">Danger Subtle</div>

```

---

### 📝 Practice Task – Colors

- Create a **warning box** with `bg-warning` and dark text.
- Make a **success banner** using `bg-success-subtle`.

---

## 3. **Buttons**

Bootstrap buttons are made using `.btn` + **color classes**.

---

### 🔹 3.1 Basic Buttons

```html
<button class="btn btn-primary">Primary</button>
<button class="btn btn-secondary">Secondary</button>
<button class="btn btn-success">Success</button>
<button class="btn btn-danger">Danger</button>
<button class="btn btn-warning">Warning</button>
<button class="btn btn-info">Info</button>
<button class="btn btn-dark">Dark</button>
<button class="btn btn-light">Light</button>

```

---

### 🔹 3.2 Outline Buttons

No background, just border.

```html
<button class="btn btn-outline-primary">Outline Primary</button>
<button class="btn btn-outline-danger">Outline Danger</button>

```

---

### 🔹 3.3 Sizes

```html
<button class="btn btn-success btn-lg">Large Button</button>
<button class="btn btn-warning btn-sm">Small Button</button>

```

---

### 🔹 3.4 Full Width

```html
<button class="btn btn-info w-100">Full Width Button</button>

```

---

### 🔹 3.5 States

```html
<button class="btn btn-primary active">Active</button>
<button class="btn btn-secondary disabled">Disabled</button>

```

---

### 📝 Practice Task – Buttons

- Create a **row of 4 buttons**: Primary, Outline, Danger, and Success.
- Add a **large full-width “Login” button**.

---

## 4. **Cards**

Cards are **content containers** with optional images, headers, footers, and links.

---

### 🔹 4.1 Basic Card

```html
<div class="card" style="width: 18rem;">
  <div class="card-body">
    <h5 class="card-title">Card Title</h5>
    <p class="card-text">Some quick example text.</p>
    <a href="#" class="btn btn-primary">Go Somewhere</a>
  </div>
</div>

```

---

### 🔹 4.2 Card with Image

```html
<div class="card" style="width: 18rem;">
  <img src="<https://via.placeholder.com/150>" class="card-img-top" alt="...">
  <div class="card-body">
    <h5 class="card-title">Card with Image</h5>
    <p class="card-text">This card has an image at the top.</p>
  </div>
</div>

```

---

### 🔹 4.3 Card with Header & Footer

```html
<div class="card text-center">
  <div class="card-header">Featured</div>
  <div class="card-body">
    <h5 class="card-title">Special Title</h5>
    <p class="card-text">Some quick example text.</p>
    <a href="#" class="btn btn-success">Learn More</a>
  </div>
  <div class="card-footer text-muted">2 days ago</div>
</div>

```

---

### 🔹 4.4 Card Groups (Multiple Cards)

```html
<div class="card-group">
  <div class="card">
    <div class="card-body">Card 1</div>
  </div>
  <div class="card">
    <div class="card-body">Card 2</div>
  </div>
  <div class="card">
    <div class="card-body">Card 3</div>
  </div>
</div>

```

---

### 📝 Practice Task – Cards

- Create a **profile card** with image, name, description, and follow button.
- Make a **row of 3 cards** for services.
- Add a **footer** with “Last Updated: Today”.

---

## 5. **Spacing (Margins & Padding)**

Spacing is controlled by `m-*` (margin) and `p-*` (padding).

---

### 🔹 5.1 Margin Classes

- `m-0` → No margin
- `m-1` → Small margin
- `m-2` to `m-5` → Bigger margins

**Direction-based margins**:

- `mt-*` → Margin top
- `mb-*` → Margin bottom
- `ms-*` → Margin start (left in LTR)
- `me-*` → Margin end (right in LTR)

```html
<div class="m-3 bg-light border">Margin All</div>
<div class="mt-5 bg-warning">Big Top Margin</div>
<div class="ms-4 bg-success">Left Margin</div>

```

---

### 🔹 5.2 Padding Classes

- `p-0` to `p-5` → Padding all sides
- `pt-*` → Padding top
- `pb-*` → Padding bottom
- `ps-*` → Padding start (left)
- `pe-*` → Padding end (right)

```html
<div class="p-4 bg-info">Padding All Sides</div>
<div class="pt-3 bg-danger">Top Padding</div>

```

---

### 🔹 5.3 Auto Margin

Centers content:

```html
<div class="mx-auto bg-primary text-white w-50 p-3">Centered Box</div>

```

---

### 📝 Practice Task – Spacing

- Create a box with **`p-5` padding** and `m-3` margin.
- Center a card using `mx-auto`.
- Add two buttons with `me-2` spacing.

---

# ✅ Final Summary

- **Typography** → headings, display, lead, weight, transform.
- **Colors** → text & background colors, subtle variations.
- **Buttons** → styles (`btn-*`), outline, sizes, states.
- **Cards** → versatile containers (with image, header, footer, groups).
- **Spacing** → margin (`m-*`) & padding (`p-*`) classes.