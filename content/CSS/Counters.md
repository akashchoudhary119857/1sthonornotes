# CSS Counters : Introduction to Advanced

CSS Counters allow you to create **automatic numbering** using CSS instead of manually writing numbers in HTML.

They are especially useful for:

- Numbered headings
- Chapters and sections
- Ordered lists
- FAQs
- Steps in a process
- Nested numbering
- Documentation websites
- Tutorials and notes
- Automatically numbering cards or items

---

# 1. Basic Idea

Normally, you might write:

```
<h2>1. Introduction</h2>
<h2>2. HTML</h2>
<h2>3. CSS</h2>
<h2>4. JavaScript</h2>
```

With CSS Counters, you can write:

```
<h2>Introduction</h2>
<h2>HTML</h2>
<h2>CSS</h2>
<h2>JavaScript</h2>
```

And CSS automatically generates:

```
1. Introduction
2. HTML
3. CSS
4. JavaScript
```

---

# 2. Three Important CSS Counter Properties

CSS Counters mainly use:

```
counter-reset
counter-increment
counter()
```

There is also:

```
counters()
```

for nested counters.

---

# 3. `counter-reset`

`counter-reset` creates or resets a counter.

```
body {
    counter-reset: section;
}
```

Here:

```
section
```

is the counter name.

Think of it as:

> "Start a counter called `section`."

---

# 4. `counter-increment`

`counter-increment` increases the counter.

```
h2 {
    counter-increment: section;
}
```

Every time an `h2` appears, the counter increases by `1`.

For example:

```
h2 → section = 1
h2 → section = 2
h2 → section = 3
```

---

# 5. `counter()`

The `counter()` function retrieves the current counter value.

Usually, we use it with the `content` property.

```
h2::before {
    content: counter(section) ". ";
}
```

Complete example:

### HTML

```
<h2>Introduction</h2>
<h2>HTML</h2>
<h2>CSS</h2>
<h2>JavaScript</h2>
```

### CSS

```
body {
    counter-reset: section;
}

h2 {
    counter-increment: section;
}

h2::before {
    content: counter(section) ". ";
}
```

Output:

```
1. Introduction
2. HTML
3. CSS
4. JavaScript
```

---

# 6. Understanding the Flow

The browser effectively does this:

```
counter-reset
      ↓
counter-increment
      ↓
counter()
      ↓
display number
```

For example:

```
body {
    counter-reset: section;
}
```

Start:

```
section = 0
```

Then:

```
h2 {
    counter-increment: section;
}
```

First `h2`:

```
section = 1
```

Second `h2`:

```
section = 2
```

Third:

```
section = 3
```

Then:

```
content: counter(section);
```

displays the current value.

---

# 7. Starting Counter From a Different Number

By default, the counter starts at `0`.

You can specify a starting value:

```
body {
    counter-reset: section 10;
}
```

Then:

```
h2 {
    counter-increment: section;
}
```

Output:

```
11. Introduction
12. HTML
13. CSS
```

If you want the first number to be `10`, reset it to `9`:

```
body {
    counter-reset: section 9;
}
```

Output:

```
10. Introduction
11. HTML
12. CSS
```

---

# 8. Increasing by More Than 1

Normally:

```
counter-increment: section;
```

means:

```
+1
```

You can specify another value.

```
counter-increment: section 2;
```

Output:

```
2
4
6
8
```

For example:

```
body {
    counter-reset: section;
}

h2 {
    counter-increment: section 2;
}

h2::before {
    content: counter(section) ". ";
}
```

---

# 9. Counter With Text

You can combine normal text with the counter.

```
h2::before {
    content: "Chapter " counter(section) ": ";
}
```

Output:

```
Chapter 1: Introduction
Chapter 2: HTML
Chapter 3: CSS
```

---

# 10. Counter With Different Number Styles

You can specify the numbering style.

For example:

```
h2::before {
    content: counter(section, upper-roman) ". ";
}
```

Output:

```
I. Introduction
II. HTML
III. CSS
IV. JavaScript
```

### Common styles

```
counter(section, decimal)
```

Output:

```
1
2
3
```

```
counter(section, upper-roman)
```

Output:

```
I
II
III
```

```
counter(section, lower-roman)
```

Output:

```
i
ii
iii
```

```
counter(section, upper-alpha)
```

Output:

```
A
B
C
```

```
counter(section, lower-alpha)
```

Output:

```
a
b
c
```

---

# 11. Practical Example — Course Chapters

### HTML

```
<h2>HTML Basics</h2>
<h2>CSS Basics</h2>
<h2>JavaScript Basics</h2>
<h2>DOM Manipulation</h2>
```

### CSS

```
body {
    counter-reset: chapter;
}

h2 {
    counter-increment: chapter;
}

h2::before {
    content: "Chapter " counter(chapter) " - ";
}
```

Output:

```
Chapter 1 - HTML Basics
Chapter 2 - CSS Basics
Chapter 3 - JavaScript Basics
Chapter 4 - DOM Manipulation
```

---

# 12. Nested Counters

This is where CSS Counters become very powerful.

Suppose you want:

```
1. HTML
   1.1 Introduction
   1.2 Elements
   1.3 Forms

2. CSS
   2.1 Introduction
   2.2 Selectors
   2.3 Flexbox

3. JavaScript
   3.1 Variables
   3.2 Functions
```

You can achieve this using nested counters.

### HTML

```
<h2>HTML</h2>
<h3>Introduction</h3>
<h3>Elements</h3>
<h3>Forms</h3>

<h2>CSS</h2>
<h3>Introduction</h3>
<h3>Selectors</h3>
<h3>Flexbox</h3>

<h2>JavaScript</h2>
<h3>Variables</h3>
<h3>Functions</h3>
```

### CSS

```
body {
    counter-reset: chapter;
}

h2 {
    counter-increment: chapter;
    counter-reset: topic;
}

h2::before {
    content: counter(chapter) ". ";
}

h3 {
    counter-increment: topic;
}

h3::before {
    content: counter(chapter) "." counter(topic) " ";
}
```

Output:

```
1. HTML
1.1 Introduction
1.2 Elements
1.3 Forms

2. CSS
2.1 Introduction
2.2 Selectors
2.3 Flexbox

3. JavaScript
3.1 Variables
3.2 Functions
```

Notice this important line:

```
h2 {
    counter-reset: topic;
}
```

Every new `h2` starts the `topic` counter again.

---

# 13. `counters()` — Advanced Nested Numbering

For complex nested structures, use:

```
counters()
```

Example:

```
body {
    counter-reset: section;
}

h2 {
    counter-increment: section;
    counter-reset: subsection;
}

h3 {
    counter-increment: subsection;
}

h2::before {
    content: counter(section) ". ";
}

h3::before {
    content: counter(section) "." counter(subsection) " ";
}
```

For even deeper structures, `counters()` can automatically combine nested counters.

For example:

```
h4::before {
    content: counters(section, ".") " ";
}
```

This can produce numbering such as:

```
1
1.1
1.1.1
1.1.2
1.2
1.2.1
2
2.1
2.1.1
```

---

# 14. `counters()` vs `counter()`

This is an important difference.

### `counter()`

Returns one counter value:

```
counter(section)
```

Example:

```
2
```

### `counters()`

Combines nested counters:

```
counters(section, ".")
```

Example:

```
2.3.1
```

Think:

```
counter()   → one level
counters()  → multiple levels
```

---

# 15. Counter With Cards

CSS Counters aren't limited to headings.

Suppose you have cards:

### HTML

```
<div class="card">HTML</div>
<div class="card">CSS</div>
<div class="card">JavaScript</div>
<div class="card">React</div>
```

### CSS

```
.container {
    counter-reset: card;
}

.card {
    counter-increment: card;
}

.card::before {
    content: counter(card);
}
```

Output:

```
1 HTML
2 CSS
3 JavaScript
4 React
```

---

# 16. Designing Numbered Cards

You can combine counters with normal CSS.

```
.container {
    counter-reset: card;
    display: grid;
    gap: 20px;
}

.card {
    counter-increment: card;

    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 10px;
}

.card::before {
    content: counter(card);
    
    display: inline-flex;
    align-items: center;
    justify-content: center;

    width: 35px;
    height: 35px;

    border-radius: 50%;
    background: black;
    color: white;

    margin-right: 10px;
}
```

This is useful for:

- Course cards
- Feature cards
- Step cards
- Product cards
- Tutorial sections

---

# 17. Counter With Ordered Steps

A very practical use case is a step-by-step process.

### HTML

```
<div class="steps">
    <div class="step">
        Install VS Code
    </div>

    <div class="step">
        Install Node.js
    </div>

    <div class="step">
        Create a project
    </div>

    <div class="step">
        Run the application
    </div>
</div>
```

### CSS

```
.steps {
    counter-reset: step;
}

.step {
    counter-increment: step;
}

.step::before {
    content: "Step " counter(step) ": ";
    font-weight: bold;
}
```

Output:

```
Step 1: Install VS Code
Step 2: Install Node.js
Step 3: Create a project
Step 4: Run the application
```

---

# 18. Counter With Lists

You can also customize list numbering.

### HTML

```
<ul class="topics">
    <li>HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
</ul>
```

### CSS

```
.topics {
    counter-reset: topic;
    list-style: none;
}

.topics li {
    counter-increment: topic;
}

.topics li::before {
    content: counter(topic) ". ";
    font-weight: bold;
}
```

Output:

```
1. HTML
2. CSS
3. JavaScript
```

---

# 19. FAQ Numbering

Another practical use case is an FAQ page.

### HTML

```
<div class="faq">
    <h3>What is HTML?</h3>
    <p>HTML is used to structure web pages.</p>

    <h3>What is CSS?</h3>
    <p>CSS is used to style web pages.</p>

    <h3>What is JavaScript?</h3>
    <p>JavaScript adds behavior and interactivity.</p>
</div>
```

### CSS

```
.faq {
    counter-reset: question;
}

.faq h3 {
    counter-increment: question;
}

.faq h3::before {
    content: "Q" counter(question) ". ";
}
```

Output:

```
Q1. What is HTML?
Q2. What is CSS?
Q3. What is JavaScript?
```

---

# 20. Important: Counters and `::before`

CSS Counters are commonly displayed using pseudo-elements:

```
::before
```

or:

```
::after
```

Example:

```
h2::before {
    content: counter(section);
}
```

The counter itself doesn't automatically appear on the page.

You need:

```
content: counter(section);
```

---

# 21. Counter With `::after`

You can also put the number after the element.

```
h2::after {
    content: " (" counter(section) ")";
}
```

For example:

```
HTML (1)
CSS (2)
JavaScript (3)
```

---

# 22. Important Real-World Use Case — Documentation

CSS Counters are particularly useful for documentation websites.

For example:

```
1. HTML
   1.1 Introduction
   1.2 Basic Tags
   1.3 Forms

2. CSS
   2.1 Introduction
   2.2 Selectors
   2.3 Box Model
   2.4 Flexbox
   2.5 Position

3. JavaScript
   3.1 Introduction
   3.2 Variables
   3.3 Functions
```

This is useful for **technical notes, tutorials, documentation, manuals and course material** because you don't have to manually maintain the numbering when adding or removing sections.

---

# 23. Counter vs HTML `<ol>`

You may ask:

> Why not simply use `<ol>`?

An ordered list:

```
<ol>
    <li>HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
</ol>
```

is often the better choice when you are actually creating a list.

CSS Counters become useful when you need numbering for elements that **aren't naturally list items**.

For example:

```
<h2>HTML</h2>
<h2>CSS</h2>
<h2>JavaScript</h2>
```

You can automatically number these headings using counters.

---

# 24. Common Mistakes

### Mistake 1 — Forgetting `counter-reset`

Incorrect:

```
h2 {
    counter-increment: section;
}

h2::before {
    content: counter(section);
}
```

Better:

```
body {
    counter-reset: section;
}
```

---

### Mistake 2 — Forgetting `counter-increment`

```
body {
    counter-reset: section;
}

h2::before {
    content: counter(section);
}
```

Every heading may show:

```
0
```

because the counter was never incremented.

Correct:

```
h2 {
    counter-increment: section;
}
```

---

### Mistake 3 — Forgetting `content`

This doesn't display anything:

```
h2::before {
    counter(section);
}
```

Correct:

```
h2::before {
    content: counter(section);
}
```

---

# 25. Complete Practical Example

### HTML

```
<div class="course">

    <h2>HTML</h2>
    <h3>Introduction</h3>
    <h3>Elements</h3>
    <h3>Forms</h3>

    <h2>CSS</h2>
    <h3>Introduction</h3>
    <h3>Selectors</h3>
    <h3>Flexbox</h3>

    <h2>JavaScript</h2>
    <h3>Variables</h3>
    <h3>Functions</h3>

</div>
```

### CSS

```
.course {
    counter-reset: chapter;
}

.course h2 {
    counter-increment: chapter;
    counter-reset: topic;
}

.course h2::before {
    content: counter(chapter) ". ";
}

.course h3 {
    counter-increment: topic;
}

.course h3::before {
    content: counter(chapter) "." counter(topic) " ";
}
```

### Result

```
1. HTML
1.1 Introduction
1.2 Elements
1.3 Forms

2. CSS
2.1 Introduction
2.2 Selectors
2.3 Flexbox

3. JavaScript
3.1 Variables
3.2 Functions
```

---

##  Remember This

The most important pattern to remember is:

```
.container {
    counter-reset: myCounter;
}

.item {
    counter-increment: myCounter;
}

.item::before {
    content: counter(myCounter);
}
```

In simple terms:

```
counter-reset
     ↓
Create / restart counter

counter-increment
     ↓
Increase counter

counter()
     ↓
Read counter value

content
     ↓
Display counter value
```