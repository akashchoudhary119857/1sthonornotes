## 1 — Color systems & `color` property

**Property**: `color` — sets foreground (text) color.

**Common value formats**:

- **Named**: `red`, `blue`, `rebeccapurple`
- RGB (Red, Green, Blue)
    - Think of **light mixing**. You set how much red, green, and blue light to use.
    - **Range:** `0–255` per channel (or `%`).
    - **CSS syntax:**
        - `rgb(255, 0, 0)` (red)
        - Modern: `rgb(255 0 0)` or percentages `rgb(100% 0% 0%)`
- HEX (Hexadecimal RGB)
    - Same RGB numbers, but written in **base-16** as **hex pairs**: `#RRGGBB`.
    - Shorthand exists: `#RGB` (expands to `#RRGGBB`).
    - **Examples**
        - Red: `#ff0000` (= `rgb(255,0,0)`)
        - White: `#ffffff` (= `rgb(255,255,255)`)
        - Shorthand gray: `#ccc` → `#cccccc` (= `rgb(204,204,204)`)

**How to read:** `#1e90ff` → `1e`(30), `90`(144), `ff`(255) ⇒ `rgb(30,144,255)`.

**Good for:** compact, widely used in design systems and branding.

- HSL (Hue, Saturation, Lightness)
    - More **human-friendly** color model.
    - **Hue**: color angle **0–360°** on a wheel (0=red, 120=green, 240=blue)
    - **Saturation**: **0–100%** (gray → vivid)
    - **Lightness**: **0–100%** (black → normal → white)
    - **CSS syntax**
        - `hsl(0, 100%, 50%)` (pure red)
        - Modern: `hsl(0deg 100% 50%)`

**Good for:** tweaking **tints/shades** and **vibrancy** without guessing numbers.

---

### How they’re related

All three describe **the same color**:

- `rgb(255, 0, 0)` ≡ `#ff0000` ≡ `hsl(0, 100%, 50%)`
- They’re just **different coordinate systems** for the same color space (sRGB).

Choose based on task:

- **HEX** for compact tokens.
- **RGB** for channel-based tweaks or from image pickers.
- **HSL** for easy “make it lighter/darker/more vivid.”

### Alpha (transparency)

Alpha controls **opacity** (how see-through the color is).

- **Range:** `0` (fully transparent) → `1` (fully opaque) or `0%–100%`.
- Doesn’t change the color itself—just how it **blends with the background**.

**Ways to use alpha:**

- **RGBA:** `rgba(255, 0, 0, 0.5)` or modern `rgb(255 0 0 / 0.5)`
- **HSLA:** `hsla(0, 100%, 50%, 0.5)` or modern `hsl(0 100% 50% / 0.5)`
- **8-digit HEX:** `#RRGGBBAA` (and shorthand `#RGBA`)
    - 50% red: `#ff000080` (because 0.5×255 ≈ 128 = `80` in hex)
    - 20% black overlay: `#00000033` (`33` hex = 51 ≈ 20%)

**Examples (same semi-transparent red):**

- `rgb(255 0 0 / 0.5)`
- `hsl(0 100% 50% / 0.5)`
- `#ff000080`

---

# Practical examples

```css
/* Solid colors */
.button        { background: #1e90ff; }               /* HEX */
.alert         { background: rgb(255, 69, 0); }       /* RGB */
.tag           { background: hsl(140 70% 40%); }      /* HSL */

/* Semi-transparent overlays */
.overlay       { background: rgb(0 0 0 / 0.4); }      /* 40% black */
.tint-red      { background: #ff000080; }             /* 50% red */
.glass         { background: hsl(0 0% 100% / 0.25); } /* 25% white */

/* Using HSL to make variants easily */
.primary       { background: hsl(220 90% 56%); }      /* base */
.primary-hover { background: hsl(220 90% 50%); }      /* darker */
.primary-weak  { background: hsl(220 90% 95%); }      /* pale tint */

```

---

## Quick cheat sheet

- **Pure red:** `rgb(255,0,0)` = `#ff0000` = `hsl(0,100%,50%)`
- **Pure green:** `rgb(0,255,0)` = `#00ff00` = `hsl(120,100%,50%)`
- **Pure blue:** `rgb(0,0,255)` = `#0000ff` = `hsl(240,100%,50%)`
- **Gray:** any `hsl(*, 0%, L%)` (saturation 0% makes it gray)

If you want, I can whip up a tiny HTML demo that shows the **same color in RGB/HEX/HSL** and lets you slide **alpha, saturation, and lightness** to see the effect live.

---

## 2 — Backgrounds (full property set & shorthand)

### Individual background properties

- `background-color`: color behind content.
- `background-image`: `url(...)`, `linear-gradient(...)`, `radial-gradient(...)`, `conic-gradient(...)`.
- `background-position`: position of background (e.g., `center`, `left top`, `50% 75%`).
- `background-size`: `auto`, `cover`, `contain`, `<width> <height>` (e.g., `100% 200px`).
- `background-repeat`: `repeat`, `repeat-x`, `repeat-y`, `no-repeat`, `round`, `space`.
- `background-attachment`: `scroll`, `fixed`, `local`.
- `background-origin`: `padding-box`, `border-box`, `content-box`.
- `background-clip`: `border-box`, `padding-box`, `content-box`.
- `background-blend-mode`: `multiply`, `screen`, `overlay`, etc. (how multiple backgrounds blend).

### Shorthand

```css
/* color image position/size repeat origin clip attachment */
background: #222 url("img.jpg") center/cover no-repeat padding-box border-box fixed;

```

### Multiple backgrounds

- Separate layers with commas; first is topmost.

```css
header {
  background-image: linear-gradient(to right, rgba(0,0,0,0.6), rgba(0,0,0,0)), url("hero.jpg");
  background-size: cover, auto;
  background-position: center, center;
}

```

### Gradients

- `linear-gradient(direction, color-stop1, color-stop2, ...)`
    
    ```css
    background-image: linear-gradient(90deg, #ff7a18, #af002d 60%, #319197);
    
    ```
    
- `radial-gradient()` and `conic-gradient()` exist too.
    
- Gradients act like images — can be used in `background-image`.
    

---

## 3 — Border system

### Border basics

- `border`: shorthand for `border-width border-style border-color`.
- Subproperties:
    - `border-width` (e.g., `1px`, `thin`, `medium`, `thick`)
    - `border-style` (`none`, `hidden`, `dotted`, `dashed`, `solid`, `double`, `groove`, `ridge`, `inset`, `outset`)
    - `border-color` (any color value)
- Side-specific:
    - `border-top`, `border-right`, `border-bottom`, `border-left`
    - `border-top-width`, `border-top-style`, `border-top-color`

### Border radius

- `border-radius`: corners rounding. Values:
    - Single: `border-radius: 8px;` (all corners)
    - Four values: `border-radius: 2px 4px 6px 8px;` (top-left, top-right, bottom-right, bottom-left)
    - Elliptical: `border-radius: 50% / 10%` (X radius / Y radius)
- Examples:

```css
img { border-radius: 50%; } /* circle for square images */
.box { border-radius: 10px 10px 0 0; }

```

### Border image

- `border-image-source`, `border-image-slice`, `border-image-width`, `border-image-outset`, `border-image-repeat`
- Complex; used when using image-based borders.

### Outline

- `outline` (like border but does not take up layout space; often used for focus)
- `outline-offset`: distance from edge
- Example:

```css
button:focus { outline: 3px solid #5b9; outline-offset: 2px; }

```

---

## 4 — Shadows

- `box-shadow`: `offsetX offsetY blurRadius spreadRadius color [inset]`
    - Examples:
        - `box-shadow: 0 2px 6px rgba(0,0,0,0.2);`
        - Multiple: `box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);`
        - `inset` for inner shadow.
- `text-shadow`: `h-shadow v-shadow blur color` e.g. `text-shadow: 1px 1px 2px rgba(0,0,0,0.5);`

---

## 5 — Practical example: Card

```html
<div class="card">
  <h3>Title</h3>
  <p>Summary</p>
</div>

```

```css
.card {
  background-image: linear-gradient(180deg, #ffffffcc, #f4f7fb);
  border: 1px solid rgba(0,0,0,0.06);
  border-radius: 12px;
  padding: 20px;
  box-shadow: 0 6px 18px rgba(0,0,0,0.08);
}

```

---

## 6 — Accessibility & contrast

- Ensure sufficient contrast between text and background (WCAG AA/AAA).
- Avoid relying solely on `opacity` for readability (affects children).
- Prefer explicit colors with alpha (rgba/hsla) for backgrounds that should be semi-transparent, instead of `opacity`.

---

## 7 — Exercises

1. Create a hero section with background image that covers and stays centered.
    
    ```css
    .hero {
      background: url(hero.jpg) center/cover no-repeat;
    }
    
    ```
    
2. Make a rounded button with subtle shadow: