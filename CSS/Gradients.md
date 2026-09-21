## Gradients

Gradients are CSS-generated images (not colors). You apply them anywhere an image works (e.g.,

background-image

,

mask-image

,

border-image

).

### 1) Linear Gradients

Syntax

background-image: linear-gradient([angle | to side-or-corner], color-stop, color-stop, ...);

​

Angle:

45deg

,

180deg

(0deg points up;

to right

≡

90deg

).

Directional keywords:

to top|right|bottom|left

and combos like

to top right

.

Color stops: optional positions (

%

,

px

) to control transitions.

Basic examples

/* Top → bottom (default) */ .box { background: linear-gradient(#4f46e5, #22d3ee); } /* Left → right */ .box { background: linear-gradient(to right, #4f46e5, #22d3ee); } /* Custom angle and stops */ .box { background: linear-gradient(135deg, #4f46e5 0%, #22d3ee 50%, #10b981 100%); }

​

Striped backgrounds (repeating)

.box { background: repeating-linear-gradient( 90deg, #111 0 10px, #333 10px 20px ); }

​

Gradient borders (with

border-image

)

.btn { border: 4px solid transparent; border-image: linear-gradient(90deg, #f59e0b, #ef4444) 1; }

​

Gradient text (because gradients are images, not colors)

.title { background: linear-gradient(90deg, #4f46e5, #22d3ee); -webkit-background-clip: text; background-clip: text; color: transparent; }

​

Overlay on images

.card { background: linear-gradient(180deg, rgba(0,0,0,.6), rgba(0,0,0,0)), url(hero.jpg) center/cover no-repeat; color: white; }

​

### 2) Radial Gradients

Syntax

background-image: radial-gradient([shape size at position], color-stops...);

​

Shape:

circle

|

ellipse

(default depends on box ratio).

Size:

closest-side

,

farthest-side

,

closest-corner

,

farthest-corner

(how far it expands).

Position:

at center

(default) or

at 30% 60%

,

at top left

, etc.

Examples

/* Soft spotlight from center */ .panel { background: radial-gradient(circle at center, #ffffff 0%, #e5e7eb 40%, #d1d5db 100%); } /* Off-center glow */ .badge { background: radial-gradient(circle at 30% 35%, #22d3ee, #4f46e5 60%, #0ea5e9 100%); } /* Repeating polka dots */ .wrap { background: repeating-radial-gradient(circle at center, #111 0 6px, #111 0 12px, #fff 12px 24px); }

​

Tips

Use alpha colors to blend (

rgba()

/

hsl(... / alpha)

).

Layer multiple gradients for complex effects (first listed is on top).

## ![🌫️](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Shadows

### 1) Text Shadows (

text-shadow

)

Syntax

text-shadow: offset-x offset-y blur-radius color;

​

Blur is optional; no spread parameter for text.

Examples

/* Subtle lift */ h1 { text-shadow: 0 1px 2px rgba(0,0,0,.25); } /* Neon glow using multiple shadows */ .glow { color: #fff; text-shadow: 0 0 6px #22d3ee, 0 0 18px #22d3ee, 0 0 36px #06b6d4; }

​

Use cases

Gentle readability boost on busy backgrounds.

Glow effects and outlined looks (use multiple shadows with different offsets/colors).

### 2) Box Shadows (

box-shadow

)

Syntax

box-shadow: [inset] offset-x offset-y blur-radius spread-radius color;

​

inset

makes the shadow inside the box.

Multiple shadows are comma-separated (topmost last).

Examples

/* Card elevation */ .card { box-shadow: 0 6px 14px rgba(0,0,0,.12), 0 2px 6px rgba(0,0,0,.08); } /* Focus ring without layout shift */ .input:focus { outline: none; box-shadow: 0 0 0 3px rgba(99,102,241,.45); } /* Inset for inner depth */ .panel { box-shadow: inset 0 2px 6px rgba(0,0,0,.15); } /* Neumorphism */ .soft { background: #e8ecf1; box-shadow: 10px 10px 20px #c3c8ce, -10px -10px 20px #fff; }

​

Tips

Use smaller blur with small spread for crisp rings (

0 0 0 4px

).

Prefer semi-transparent colors to blend with varied backgrounds.

## ☐ Outlines vs Borders

### Definitions

Border: Part of the box model. It sits between padding and margin, affects layout, supports per-side control, and follows

border-radius

.

Outline: A non-rectangular highlight that does not take space and does not affect layout. It sits outside the border (may not follow the radius) and cannot be set per side (no

outline-top

etc.). Great for focus visibility.

### Properties & Shorthands

/* Border */ .box { border: 2px solid #111; /* width style color */ border-top: 0; /* per-side control */ border-radius: 12px; } /* Outline */ .link { outline: 2px dashed #2563eb; /* width style color */ outline-offset: 4px; /* gap from the element’s edge */ }

​

### When to use

Border: visual boundaries, separators, rounded boxes, containers.

Outline: focus states & accessibility (keyboard navigation), quick dev debugging.

Accessible focus example

button:focus-visible { outline: 3px solid #22c55e; outline-offset: 3px; } button:focus { outline: none; } /* keep default outline unless you supply a visible alternative */

​

Debug trick

/* See all boxes without shifting layout */ * { outline: 1px solid rgba(0,0,0,.08); }

​

Gradient “borders” without affecting layout

.box { position: relative; } .box::before { content: ""; position: absolute; inset: -3px; z-index: -1; border-radius: 12px; background: linear-gradient(90deg, #f59e0b, #ef4444); } /* The pseudo-element emulates a border/outline glow */