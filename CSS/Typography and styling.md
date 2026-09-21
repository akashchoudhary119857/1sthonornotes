Typography is all about how text looks and behaves on the web.

It includes fonts, sizes, weights, spacing, alignment, and decoration.

### 1. Font Family

Defines which font is used.

p { font-family: "Roboto", "Helvetica Neue", Arial, sans-serif; }

​

![🔹](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Rules:

Always provide fallback fonts (browser picks the next if first isn’t available).

Fonts are grouped into 5 generic families:

serif → Times New Roman (with strokes)

sans-serif → Arial, Roboto (clean edges)

monospace → Courier (equal-width characters)

cursive → Brush Script

fantasy → Decorative fonts

### 2. Font Size

Controls text size.

#### Units:

Absolute:

px

→

font-size: 16px;

Relative:

em

→ relative to parent element’s font-size

rem

→ relative to root (

html

) font-size

%

→ relative to parent’s size

vw/vh

→ relative to viewport

clamp()

→ responsive safe scaling

p { font-size: clamp(1rem, 2.5vw, 1.5rem); }

​

![✅](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Good practice: Use

rem

or clamp() for accessibility.

### 3. Font Weight

Defines thickness of letters.

p { font-weight: 400; /* normal */ font-weight: 700; /* bold */ }

​

![🔹](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Keywords:

normal

,

bold

,

lighter

,

bolder

![🔹](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Numeric values:

100

(thin) →

900

(extra bold)

### 4. Font Style

Defines italicization.

p { font-style: italic; }

​

Values:

normal

italic

oblique

(slanted but not true italic)

### 5. Text Transform

Changes capitalization.

h1 { text-transform: uppercase; /* ALL CAPS */ }

​

Values:

uppercase

lowercase

capitalize

none

### 6. Text Decoration

Adds/removes decoration lines.

a { text-decoration: underline dotted red; }

​

Values:

none

underline

overline

line-through

dotted

,

dashed

,

wavy

(style)

### 7. Text Align

Aligns text horizontally inside a container.

p { text-align: center; }

​

Values:

left

right

center

justify

(spreads text evenly across line)

### 8. Text Indent

First-line indentation.

p { text-indent: 2em; }

​

### 9. Letter Spacing

Space between characters.

p { letter-spacing: 2px; }

​

### 10. Word Spacing

Space between words.

p { word-spacing: 1rem; }

​

### 11. Line Height

Vertical spacing between lines.

p { line-height: 1.6; /* 1.6 × font-size */ }

​

![✅](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Best practice:

1.5–1.8

for readability.

### 12. White Space

Controls text wrapping.

p { white-space: nowrap; /* Prevents wrapping */ }

​

Values:

normal

(default)

nowrap

pre

(respects spaces & line breaks)

pre-wrap

pre-line

### 13. Text Overflow

What happens when text doesn’t fit.

p { white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }

​

![✅](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Shows

...

when overflowing.

### 14. Word Break & Hyphens

Control how long words wrap.

p { word-break: break-word; /* Breaks long words */ hyphens: auto; /* Adds hyphenation */ }

​

### 15. Shorthand: Font

You can define multiple properties in one.

p { font: italic small-caps bold 16px/1.5 "Roboto", sans-serif; }

​

Format:

font: [style] [variant] [weight] [size]/[line-height] [family];

​

### 16. Advanced: Web Fonts

Using Google Fonts:

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap" rel="stylesheet">

​

body { font-family: "Poppins", sans-serif; }

​

### ![🎯](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Example Bringing It All Together

<h1>Elegant Typography Example</h1> <p class="styled"> This paragraph shows how CSS typography works beautifully on the web. </p>

​

h1 { font-family: "Merriweather", serif; font-size: clamp(1.5rem, 3vw, 2.5rem); font-weight: 700; text-align: center; letter-spacing: 1px; text-transform: capitalize; } .styled { font-family: "Open Sans", sans-serif; font-size: 1rem; line-height: 1.7; color: #333; text-align: justify; word-spacing: 0.2rem; }