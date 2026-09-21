# Comprehensive HTML & CSS Study Notes: From Fundamentals to Practical Implementation

---

## Module 1: Introduction to HTML

---

### Topic 1: What Is HTML?

#### Introduction
HTML stands for **HyperText Markup Language**. It is the standard foundational language used to build and organize content on the World Wide Web. HTML is not a programming language; it is a **markup language**. A markup language uses tags to wrap around plain text to define its structural meaning and purpose for a web browser (such as Google Chrome, Mozilla Firefox, or Microsoft Edge).

*   **HyperText:** Refers to text that contains links to other texts or pages, allowing users to navigate non-linearly across the web.
*   **Markup:** Refers to special keywords (tags) used to annotate and structure plain text.
*   **Language:** Refers to the set of syntax rules used by web browsers to interpret the document.

#### Real-Life Analogy
Think of building a webpage like constructing a human body:
*   **HTML (Structure/Skeleton):** Provides the bones, ribcage, and basic architectural framework. It specifies where the head, arms, and legs are positioned.
*   **CSS (Appearance/Clothing & Features):** Adds clothing, skin tone, eye color, height, and hairstyle. It defines how the body looks.
*   **JavaScript (Behavior/Movement):** Adds muscles, nerve endings, and brain logic. It allows the body to walk, talk, jump, and respond to environmental stimuli.

```
+-------------------------------------------------------------+
|                      THE WEB TRINITY                        |
+------------------------------+------------------------------+
| HTML                         | Structure / Skeleton         |
| CSS                          | Presentation / Appearance    |
| JavaScript                   | Behavior / Functionality     |
+------------------------------+------------------------------+
```

#### Use Cases
HTML is used across every single website on the internet, including:
1.  **E-commerce Sites (Amazon, Flipkart):** Formatting product titles, pricing details, product descriptions, and image placements.
2.  **Social Media Platforms (Twitter, LinkedIn):** Structuring user profiles, post feeds, comment sections, and navigation bars.
3.  **Educational Portals & Colleges:** Structuring lecture notes, syllabus tables, admission forms, and video lectures.

#### Why Is It Required?
Without HTML, a browser cannot distinguish between a main title, a paragraph, an image, or a clickable button. Plain text without HTML would be displayed as a continuous, unformatted block of text without structure, hierarchy, or interactive hyperlinks.

#### How It Works
1.  The developer writes text wrapped in HTML tags (e.g., `<p>Hello World</p>`).
2.  The file is saved with an `.html` extension (e.g., `index.html`).
3.  When opened in a web browser, the browser reads the markup tags, strips them away, and renders only the enclosed text formatted according to the tag rules.

#### Syntax
```html
<tagname>Enclosed Content Goes Here</tagname>
```
*   `<tagname>`: Opening tag (signals the start of an element).
*   `Enclosed Content`: The text or visual element being structured.
*   `</tagname>`: Closing tag (contains a forward slash `/` signaling the end of an element).

#### Implementation
```html
<!DOCTYPE html>
<html>
  <body>
    <h1>Welcome to Web Development</h1>
    <p>This is a paragraph structured using HTML.</p>
  </body>
</html>
```

#### CSS Integration
```html
<!-- Inline CSS Example -->
<h1 style="color: navy; font-family: Arial, sans-serif;">Welcome to Web Development</h1>
```

#### Output Explanation
The browser displays a large, bold heading reading "Welcome to Web Development" in navy blue, followed by a regular paragraph of text below it. The raw HTML tags (`<h1>`, `<p>`) are hidden from the visual display.

#### Common Mistakes
*   **Mistake:** Calling HTML a "programming language."
*   **Correction:** HTML has no logic, conditional loops (like `if` or `for`), variables, or algorithmic operations. It is strictly a **markup** language for structuring content.
*   **Mistake:** Forgetting the forward slash (`/`) in the closing tag.
*   **Correction:** `<p>Paragraph Text<p>` causes nesting errors. Always close paired tags: `<p>Paragraph Text</p>`.

#### Practical Application
```html
<!-- Mini Profile Card Structure -->
<h2>John Doe</h2>
<p>Computer Science Student | Web Development Enthusiast</p>
```

#### Summary
*   HTML stands for HyperText Markup Language.
*   It forms the skeleton/structure of all web pages.
*   It works alongside CSS (styling) and JavaScript (behavior).
*   It uses opening (`<tag>`) and closing (`</tag>`) syntax to structure content.

---

### Topic 2: History and Evolution of HTML

#### Introduction
HTML has evolved from a basic text-document format used by scientists into a modern web application standard capable of rendering video, audio, complex graphics, and responsive layouts.

#### Brief Timeline
*   **1991 (HTML 1.0):** Created by Tim Berners-Lee at CERN to help researchers share academic papers.
*   **1995 (HTML 2.0):** Standardized basic form controls and table concepts.
*   **1997 (HTML 3.2 / HTML 4.01):** Added inline styling options, frame elements, and enhanced table capabilities.
*   **2014 (HTML5):** Introduced by the W3C (World Wide Web Consortium) and WHATWG (Web Hypertext Application Technology Working Group). HTML5 modernized the web by introducing native multimedia tags (`<video>`, `<audio>`), modern graphic canvases, and semantic structural tags (`<header>`, `<nav>`, `<article>`, `<footer>`).

#### HTML5 and Its Importance
Modern web standards rely entirely on **HTML5**. HTML5 eliminated the need for third-party browser plugins (such as Adobe Flash) to play music or video, integrated native mobile-device optimizations, and introduced strict web accessibility standards.

#### Key Enhancements in HTML5
| Feature Category | Old Approach (HTML4) | Modern Approach (HTML5) |
| :--- | :--- | :--- |
| **Media** | Third-party Flash plugins (`<object>`) | Native tags: `<video>`, `<audio>` |
| **Document Structure** | Generic `<div id="header">` tags | Semantic tags: `<header>`, `<nav>`, `<main>`, `<footer>` |
| **Form Inputs** | Generic `<input type="text">` | Semantic inputs: `type="email"`, `type="date"`, `type="number"` |
| **Doctype** | Extremely long, complex DTD string | Simple, clean `<!DOCTYPE html>` |

#### Summary
*   HTML was created by Tim Berners-Lee in 1991.
*   HTML5 is the current, modern standard for web development.
*   HTML5 introduced semantic tags, native multimedia support, and improved mobile compatibility.

---

### Topic 3: Basic HTML Boilerplate

#### Introduction
An HTML boilerplate is the standard template of required code that every HTML file must contain to ensure web browsers parse and render the document correctly across different operating systems and devices.

#### Complete Boilerplate Code
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document Title</title>
  </head>
  <body>
    <!-- Webpage content goes here -->
  </body>
</html>
```

#### Line-by-Line Breakdown

```
+-------------------------------------------------------------------------+
|                               <!DOCTYPE html>                           |
|  +-------------------------------------------------------------------+  |
|  |                            <html lang="en">                       |  |
|  |  +-------------------------------------------------------------+  |  |
|  |  |                         <head>                              |  |  |
|  |  |  - <meta charset="UTF-8">                                   |  |  |
|  |  |  - <meta name="viewport" content="...">                     |  |  |
|  |  |  - <title>Document Title</title>                            |  |  |
|  |  +-------------------------------------------------------------+  |  |
|  |  +-------------------------------------------------------------+  |  |
|  |  |                         <body>                              |  |  |
|  |  |  - Visible content rendered on screen                       |  |  |
|  |  +-------------------------------------------------------------+  |  |
|  +-------------------------------------------------------------------+  |
+-------------------------------------------------------------------------+
```

##### 1. `<!DOCTYPE html>`
*   **Purpose:** Informs the web browser that the document is written in modern **HTML5**.
*   **Requirement:** It must be the very first line of code in the file.
*   **Omission Result:** If omitted, the browser enters "Quirks Mode," rendering the page using outdated rendering rules, which can break CSS layouts.
*   **Browser Visibility:** Invisible.

##### 2. `<html lang="en">`
*   **Purpose:** The root element wrapping all content on the page. The `lang="en"` attribute specifies that the primary language of the content is English.
*   **Requirement:** Required for accessibility tools (screen readers) and search engines (SEO).
*   **Omission Result:** Translation software may struggle to identify the correct language.
*   **Browser Visibility:** Invisible directly, but encloses the entire document.

##### 3. `<head>`
*   **Purpose:** Contains **metadata** (data about data)—information intended for the browser, search engines, and external links rather than the user.
*   **Requirement:** Essential for character encoding, page titles, styling links, and script references.
*   **Omission Result:** Search engines cannot index the site properly, stylesheets fail to load, and tab titles are broken.
*   **Browser Visibility:** Invisible on the main page canvas.

##### 4. `<meta charset="UTF-8">`
*   **Purpose:** Sets the character encoding standard to UTF-8, which includes almost all written characters, emojis, and symbols from all world languages.
*   **Requirement:** Essential to ensure foreign characters and symbols render correctly.
*   **Omission Result:** Text like accents or emojis may appear as garbled characters (e.g., `Ã©` instead of `é`).
*   **Browser Visibility:** Invisible.

##### 5. `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
*   **Purpose:** Configures the viewport to scale the webpage's width to match the screen width of mobile devices, laptops, and tablets automatically.
*   **Requirement:** Mandatory for responsive web design.
*   **Omission Result:** Mobile devices will render the web page at a desktop scale, forcing users to pinch and zoom horizontally.
*   **Browser Visibility:** Invisible.

##### 6. `<title>`
*   **Purpose:** Sets the text displayed on the browser's tab, search engine results, and bookmark bar.
*   **Requirement:** Mandatory for user experience and SEO.
*   **Omission Result:** The tab displays the raw file path or `Untitled`.
*   **Browser Visibility:** Visible only in the browser tab bar at the top, not on the page canvas.

##### 7. `<body>`
*   **Purpose:** Contains all visible elements (headings, paragraphs, images, tables, links, videos) rendered on the main web page canvas.
*   **Requirement:** Mandatory.
*   **Omission Result:** Nothing appears on the user's screen.
*   **Browser Visibility:** Fully visible.

#### Summary
*   The boilerplate is the standard template required by every HTML page.
*   `<!DOCTYPE html>` enables HTML5 parsing mode.
*   `<head>` contains metadata, title, and assets; `<body>` contains all visible content.

---

### Topic 4: HTML Document Architecture

#### Introduction
An HTML document is structured as a hierarchical **tree structure** (often referred to as the DOM Tree). Understanding this hierarchy is essential for organizing elements, writing CSS, and writing JavaScript.

#### Structural Tree Diagram
```
                     +------------------+
                     |     Document     |
                     +--------+---------+
                              |
                     +--------v---------+
                     |   <html> (Root)  |
                     +----+--------+----+
                          |        |
        +-----------------+        +-----------------+
        |                                            |
+-------v--------+                          +--------v-------+
|     <head>     |                          |     <body>     |
+-------+--------+                          +--------+-------+
        |                                            |
+-------v--------+                          +--------v-------+
|    <title>     |                          |   <h1> (Head)  |
+----------------+                          +--------+-------+
                                                     |
                                            +--------v-------+
                                            |   <p> (Para)   |
                                            +----------------+
```

#### Hierarchy Terminology
*   **Root Element:** The top-level element containing all others (`<html>`).
*   **Parent Element:** An element containing other nested elements. In the diagram above, `<body>` is the parent of `<h1>`.
*   **Child Element:** An element located directly inside another. `<h1>` is a child of `<body>`.
*   **Sibling Elements:** Elements that share the same direct parent. `<h1>` and `<p>` are siblings under `<body>`.
*   **Nested Elements:** Elements placed inside other elements (e.g., placing `<strong>` inside `<p>`).

#### Browser Interpretation
When a web browser reads an HTML file, it scans the code top-to-bottom, line-by-line, and builds an internal tree node representation of the document structure.

#### Summary
*   HTML pages follow a parent-child hierarchical tree model.
*   The `<html>` element is the root element.
*   Elements sharing the same parent are called siblings.

---

### Topic 5: How HTML Works

#### Introduction
Understanding how raw HTML code written on your computer transforms into a fully functioning visual web page helps in debugging, optimizing performance, and building responsive web applications.

#### Step-by-Step Execution Workflow
```
[Developer Code] -> [Saved .html] -> [Browser Load] -> [Parsing] -> [DOM Construction] -> [CSSOM & Render Tree] -> [Layout & Paint] -> [Visual Page]
```

1.  **Code Creation:** A developer writes text formatted with HTML tags in an editor (VS Code, Notepad).
2.  **File Storage:** The file is saved with an `.html` file extension using standard ASCII or UTF-8 character encoding.
3.  **File Loading:**
    *   *Direct File Loading:* Double-clicking a local file opens it via the file system path (`file:///C:/projects/index.html`).
    *   *Server/URL Loading:* Entering a website URL (`https://example.com`) sends an HTTP/HTTPS request to a remote server, which responds by sending back the `.html` file over the network.
4.  **Parsing:** The browser's **Rendering Engine** (e.g., Blink in Chrome/Edge, Gecko in Firefox, WebKit in Safari) reads the raw text bytes and converts them into characters, tokens, and elements.
5.  **DOM Construction:** The rendering engine converts the tags into node structures, building the **Document Object Model (DOM)**.
6.  **CSSOM & Render Tree:** The browser parses CSS to construct the CSS Object Model (CSSOM). It combines the DOM and CSSOM to create the **Render Tree** (calculating what is visible).
7.  **Layout & Painting:** The browser calculates exact geometry/positions for every element (Layout) and draws the pixels onto the screen (Painting).

#### Source Code vs. The DOM
*   **HTML Source Code:** The static text written inside the `.html` file saved on your hard drive.
*   **The DOM (Document Object Model):** The live, dynamic, in-memory object tree constructed by the browser. JavaScript interacts with and modifies the DOM in real-time, changing what is rendered without altering the original saved source code file.

#### Summary
*   Browsers parse HTML source code line-by-line to construct the DOM.
*   The rendering engine handles DOM creation, CSS parsing, layout, and painting.
*   Source code is static; the DOM is dynamic and editable via JavaScript.

---

## Module 2: HTML Tags, Elements, Attributes, and Properties

---

### Topic 6: Types of HTML Tags

#### Introduction
HTML tags are categorized based on their structural behavior, display modes, and semantic meaning.

#### 1. Paired (Container) Tags vs. Void (Empty) Elements
*   **Paired / Container Tags:** Require both an opening tag (`<tag>`) and a closing tag (`</tag>`). They enclose content or other child tags inside them.
    *   *Examples:* `<h1>Heading</h1>`, `<p>Text</p>`, `<div>Container</div>`.
*   **Void / Empty Elements:** Do not enclose content and **must not** have a closing tag. They insert self-contained items onto the page.
    *   *Examples:* `<br>` (line break), `<hr>` (horizontal rule), `<img>` (image), `<input>` (form field), `<meta>` (metadata).
    *   *Note:* Writing `<br></br>` is invalid syntax in HTML5.

#### 2. Block-Level vs. Inline Elements
*   **Block-Level Elements:**
    *   Always start on a new line.
    *   By default, take up the full available width of their parent container (100% width).
    *   Can contain both other block-level elements and inline elements.
    *   *Examples:* `<div>`, `<h1>`-`<h6>`, `<p>`, `<ul>`, `<ol>`, `<li>`, `<table>`, `<form>`.
*   **Inline Elements:**
    *   Do **not** start on a new line; they sit side-by-side with surrounding content.
    *   Only take up as much width as their inner content requires.
    *   Should generally contain only other inline elements or plain text.
    *   *Examples:* `<span>`, `<a>`, `<strong>`, `<em>`, `<img>`, `<label>`.

```
Block-Level Behavior:
+-------------------------------------------------------------------------+
| Block Element (Takes 100% full width, forces next element down)          |
+-------------------------------------------------------------------------+
| Block Element 2                                                         |
+-------------------------------------------------------------------------+

Inline Behavior:
+-----------------+ +-----------------+ +-----------------+
| Inline Item 1   | | Inline Item 2   | | Inline Item 3   |
+-----------------+ +-----------------+ +-----------------+
```

#### 3. Semantic vs. Non-Semantic Elements
*   **Semantic Elements:** Clearly describe the meaning and purpose of their content to the browser, search engines, and screen readers.
    *   *Examples:* `<header>`, `<nav>`, `<article>`, `<section>`, `<aside>`, `<footer>`, `<table>`.
*   **Non-Semantic Elements:** Act as generic containers with no intrinsic meaning about their content. They are used purely for styling or grouping layout blocks.
    *   *Examples:* `<div>` (generic block container), `<span>` (generic inline container).

#### CSS Override Clarification
Block and inline behaviors describe an element's **default display settings**. These behaviors can be altered at any time using CSS properties:
```css
/* Converts a block paragraph to display inline */
p {
  display: inline;
}

/* Converts an inline link to display as a full-width block */
a {
  display: block;
}
```

#### Summary
*   Container tags have matching opening and closing tags; void tags are self-closing without inner text.
*   Block elements start on new lines and span 100% width; inline elements stay on the same line and fit content width.
*   Semantic tags describe meaning (`<nav>`); non-semantic tags are generic containers (`<div>`).

---

### Topic 7: HTML Tags vs Elements vs Attributes vs DOM Properties

#### Introduction
Beginners often confuse tags, elements, attributes, and DOM properties. Understanding these distinctions is critical for modern web development.

#### Defining Terms with a Human Analogy

```
+-------------------------------------------------------------------------+
|                              HUMAN ANALOGY                              |
+------------------+------------------------------------------------------+
| HTML Element     | A person (e.g., "John Doe")                          |
| HTML Attributes  | Birth Certificate details (Fixed initial state)      |
| DOM Properties   | Current live status (Can change dynamically)          |
+------------------+------------------------------------------------------+
```

*   **HTML Tag:** The raw syntax markers in code (`<input>`).
*   **HTML Element:** The complete structure from opening tag to closing tag, including all content inside (`<input type="text" id="username">`).
*   **HTML Attribute:** Initial settings or metadata written inside the opening tag in the source code (`type="text"`, `value="Default"`).
*   **DOM Property:** The live, dynamic variables representing that element inside the browser memory accessible via JavaScript (`element.value`).

#### Real-World Form Example (Attributes vs. DOM Properties)
Consider this input element in source code:
```html
<input type="text" id="studentName" value="Alice" />
```

When this code loads, the browser sets both the HTML attribute `value` and the DOM property `.value` to `"Alice"`.

**What happens when a user types "Bob" into the input box?**
1.  **HTML Attribute (`getAttribute('value')`):** Remains `"Alice"` (reflects the initial code state).
2.  **DOM Property (`element.value`):** Changes to `"Bob"` (reflects the real-time user input state).

```javascript
// Demonstrating the difference via JavaScript
const inputElement = document.getElementById("studentName");

console.log(inputElement.getAttribute("value")); // Outputs: "Alice" (Attribute)
console.log(inputElement.value); // Outputs: "Bob"   (DOM Property)
```

#### Comparison Matrix: Attributes vs. DOM Properties
| Feature | HTML Attribute | DOM Property |
| :--- | :--- | :--- |
| **Location** | Written in the HTML source code | Stored in browser memory DOM objects |
| **Time of Origin** | Initialized when page is parsed | Dynamic during application runtime |
| **Data Type** | Always a String | Can be Boolean, Object, Array, String, etc. |
| **Examples** | `class="card"`, `id="btn"`, `disabled` | `.className`, `.id`, `.disabled` |

#### Summary
*   A tag is the code syntax marker; an element is the complete rendered object.
*   Attributes define the initial configuration written in code.
*   DOM properties hold the live, dynamic state stored in memory.

---

## Module 3: CSS Fundamentals and HTML Integration

---

### Topic 8: Introduction to CSS

#### Introduction
**CSS** stands for **Cascading Style Sheets**. While HTML provides the raw architectural structure of a webpage, CSS defines its visual presentation, layout, color palette, typography, spacing, and animations.

#### Separation of Concerns Principle
Modern web development follows the **Separation of Concerns** principle:
*   **Structure:** Handled solely by HTML.
*   **Presentation:** Handled solely by CSS.

Mixing visual presentation directly inside HTML using deprecated presentation attributes (like `<body bgcolor="red">` or `<font color="blue">`) leads to redundant code, difficult maintenance, and poor accessibility.

#### CSS Rule Syntax
A CSS rule consists of a **Selector** and a **Declaration Block**:

```
 Selector          Declaration Block
  +---+   +---------------------------------+
  |h1 |   { color: navy; font-size: 24px; }
  +---+   +---------------------------------+
             |     |     |       |
             +--+--+     +---+---+
                |            |
             Property      Value
```

*   **Selector:** Points to the HTML element(s) you want to style (e.g., `h1`).
*   **Property:** The visual feature you want to modify (e.g., `color`, `font-size`).
*   **Value:** The configuration assigned to the property (e.g., `navy`, `24px`).
*   **Declaration:** A property and value pair ending with a semicolon `;`.

#### Summary
*   CSS controls visual presentation, separating styling from HTML content.
*   A CSS rule is composed of a selector, properties, and values.

---

### Topic 9: Types of CSS

#### Introduction
CSS can be attached to an HTML document using three distinct methods: Inline CSS, Internal CSS, and External CSS.

---

#### A. Inline CSS

##### Meaning & Syntax
Inline CSS styles an element directly inside its opening tag using the `style` attribute.

##### Implementation
```html
<h1 style="color: blue; text-align: center;">Welcome to College Portal</h1>
<p style="font-size: 18px; line-height: 1.5;">This paragraph is styled using Inline CSS.</p>
```

##### Advantages & Disadvantages
*   **Advantages:** Useful for rapid testing or applying one-off styles. High specificity overrides global stylesheets.
*   **Disadvantages:** Mixes presentation with structure, duplicates code, and is difficult to maintain across multiple pages.

---

#### B. Internal CSS

##### Meaning & Syntax
Internal CSS is written within a `<style>` block placed inside the `<head>` section of a single HTML document.

##### Implementation
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Internal CSS Example</title>
    <style>
      body {
        background-color: #f0f4f8;
        font-family: Arial, sans-serif;
      }
      h1 {
        color: #1a365d;
        text-align: center;
      }
      p {
        color: #4a5568;
        font-size: 16px;
      }
    </style>
  </head>
  <body>
    <h1>Internal CSS Heading</h1>
    <p>This page uses styles defined inside the document head.</p>
  </body>
</html>
```

##### Advantages & Disadvantages
*   **Advantages:** Keeps styling separate from body tags; styles apply to all matching elements on that single page.
*   **Disadvantages:** Cannot be reused across multiple pages, increasing overall file size on large websites.

---

#### C. External CSS

##### Meaning & Syntax
External CSS keeps all style declarations in a separate file with a `.css` extension (e.g., `style.css`). This file is linked to the HTML document using the `<link>` tag placed in the `<head>` section.

##### Implementation

1.  **Create Stylesheet (`style.css`):**
```css
/* style.css */
body {
  margin: 0;
  padding: 0;
  font-family: Segoe UI, sans-serif;
}

.main-heading {
  color: #2b6cb0;
  padding: 20px;
}
```

2.  **Link Stylesheet in HTML (`index.html`):**
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>External CSS Example</title>
    <!-- External CSS Link -->
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <h1 class="main-heading">External CSS Applied</h1>
  </body>
</html>
```

##### `<link>` Tag Attributes Explained:
*   `rel="stylesheet"`: Specifies the relationship between the HTML file and the target file.
*   `href="style.css"`: Specifies the path to the CSS file.

---

#### Direct Comparison Table

| Feature | Inline CSS | Internal CSS | External CSS |
| :--- | :--- | :--- | :--- |
| **Location** | Inside HTML element tags | Inside `<style>` in `<head>` | Separate `.css` file |
| **Scope** | Single element | Single page | Entire website (Multiple pages) |
| **Maintainability** | Poor | Moderate | Excellent |
| **Reusability** | None | Low | High |
| **Performance** | Increases HTML file size | Increases page load time | Cached by browser for faster load |
| **Best For** | Quick tests / dynamic overrides | Single-page unique layouts | Production websites |

#### Summary
*   Inline CSS uses the `style` attribute on individual elements.
*   Internal CSS uses the `<style>` tag inside the `<head>` section.
*   External CSS uses a dedicated `.css` file linked via `<link rel="stylesheet" href="...">`.
*   External CSS is the industry standard for scalable, clean code.

---

### Topic 10: CSS Selectors and Mapping CSS to HTML

#### Introduction
CSS Selectors allow developers to target specific HTML elements to apply styles.

#### 1. Element (Tag) Selector
Targets all HTML elements matching the specified tag name.
*   **CSS:**
    ```css
    p {
      color: #333333;
    }
    ```
*   **HTML Affected:** All `<p>` elements on the page.

#### 2. Class Selector
Targets elements containing a specific `class` attribute. Classes are reusable across multiple elements on a page. Represented by a dot (`.`).
*   **CSS:**
    ```css
    .highlight {
      background-color: #fef08a;
      font-weight: bold;
    }
    ```
*   **HTML:** `<p class="highlight">Important note here.</p>`

#### 3. ID Selector
Targets a single, unique element containing a specific `id` attribute. An ID **must be unique** on a webpage. Represented by a hash (`#`).
*   **CSS:**
    ```css
    #main-header {
      background-color: #1e293b;
      color: #ffffff;
    }
    ```
*   **HTML:** `<header id="main-header">Header Content</header>`

#### 4. Group Selector
Applies the same CSS declaration block to multiple selectors simultaneously, separated by commas.
*   **CSS:**
    ```css
    h1, h2, h3 {
      font-family: Georgia, serif;
      color: #0f172a;
    }
    ```
*   **HTML Affected:** All `<h1>`, `<h2>`, and `<h3>` elements.

#### 5. Descendant Selector
Targets elements located inside a specific parent structure. Indicated by a space between selectors.
*   **CSS:**
    ```css
    .nav-menu a {
      color: white;
      text-decoration: none;
    }
    ```
*   **HTML:**
    ```html
    <div class="nav-menu">
      <a href="#">Home</a> <!-- Styled -->
    </div>
    <p><a href="#">Read More</a></p> <!-- NOT Styled -->
    ```

#### 6. Attribute Selector
Targets elements based on the presence or value of an HTML attribute.
*   **CSS:**
    ```css
    input[type="text"] {
      border: 2px solid #94a3b8;
    }
    ```
*   **HTML:** `<input type="text" />` (Styled); `<input type="checkbox" />` (Not styled).

#### Class vs. ID: Key Differences

```
Class (.): Reusable, applies to MANY elements on a page.
ID    (#): Unique, applies to ONE element per page.
```

| Feature | Class Selector (`.`) | ID Selector (`#`) |
| :--- | :--- | :--- |
| **Syntax Marker** | Period / Dot (`.className`) | Hash / Pound (`#idName`) |
| **Uniqueness** | Reusable across multiple elements | Must be unique to one element per page |
| **Use Case** | Styling reusable components (buttons, cards) | Specific layout blocks, JS anchor targets |
| **Specificity** | Lower specificity | Higher specificity |

#### Summary
*   Selectors map CSS styling rules directly to target HTML tags.
*   Use classes (`.`) for styles shared by multiple elements.
*   Use IDs (`#`) for single, unique page elements.

---

### Topic 11: CSS Cascade, Specificity, and Inheritance

#### Introduction
When multiple CSS rules target the exact same HTML element, the browser uses three primary mechanisms to resolve conflicts: **Cascade**, **Specificity**, and **Inheritance**.

#### 1. The Cascade
The "Cascade" is the algorithm browsers use to resolve conflicting rules based on origin and order. When two rules have equal specificity, the rule defined **later in the stylesheet (Source Order)** overrides earlier rules.

```css
/* Paragraph text will be RED because it appears later in source order */
p {
  color: blue;
}
p {
  color: red;
}
```

#### 2. Specificity Calculation
Specificity determines which CSS rule takes precedence when multiple selectors target the same element. Specificity is calculated using a four-category score system:

```
  Inline Styles    ID Selectors    Classes / Attr    Elements / Pseudo
      (1,               0,              0,                0)
```

1.  **Inline Styles (`style=""`):** Score: **1,0,0,0** (Highest specificity)
2.  **ID Selectors (`#id`):** Score: **0,1,0,0**
3.  **Classes, Attributes, Pseudo-classes (`.class`, `[type]`, `:hover`):** Score: **0,0,1,0**
4.  **Elements and Pseudo-elements (`p`, `div`, `::before`):** Score: **0,0,0,1**

##### Specificity Example Scenario:
If an element has both a class and an ID styled in CSS:
```css
#header-title { color: gold; } /* Specificity: 0,1,0,0 (WINNER) */
.title        { color: blue; } /* Specificity: 0,0,1,0 */
h1            { color: red;  } /* Specificity: 0,0,0,1 */
```
The text will render **gold** because the ID selector `#header-title` has higher specificity than the class or element selectors.

#### 3. Inheritance
Certain CSS properties applied to a parent element are automatically passed down (inherited) by its child elements.
*   **Inherited Properties:** Text/font properties (`color`, `font-family`, `font-size`, `line-height`, `text-align`).
*   **Non-Inherited Properties:** Layout/box model properties (`margin`, `padding`, `border`, `width`, `height`, `background`).

#### Common Misconception Clarification
*   *Myth:* "Inline CSS always overrides every other CSS declaration."
*   *Fact:* An external CSS rule using the `!important` flag (e.g., `color: red !important;`) overrides inline styles. However, overuse of `!important` is bad practice and should generally be avoided.

#### Summary
*   **Cascade:** Last rule defined wins if specificity is tied.
*   **Specificity Order:** Inline styles > IDs > Classes > Elements.
*   **Inheritance:** Font and text styles flow down from parent to child automatically.

---

## Module 4: HTML Text Formatting Elements

---

### Topic 12: Heading Tags: `<h1>` to `<h6>`

#### Introduction
HTML provides six levels of section headings, ranging from `<h1>` (highest priority) down to `<h6>` (lowest priority). Headings structure the text hierarchy of a document.

#### Syntax & Hierarchy
```html
<h1>Main Document Heading (Level 1)</h1>
<h2>Major Section Heading (Level 2)</h2>
<h3>Sub-section Heading (Level 3)</h3>
<h4>Sub-sub-section Heading (Level 4)</h4>
<h5>Minor Heading (Level 5)</h5>
<h6>Lowest Level Heading (Level 6)</h6>
```

#### Semantic Importance & SEO Rules
1.  **`<h1>` Rule:** Each webpage should generally contain **only one `<h1>` tag**, representing the primary topic of the page (equivalent to a book title).
2.  **Hierarchy Flow:** Never skip heading levels (e.g., do not jump directly from `<h1>` down to `<h3>` without an intermediate `<h2>`).
3.  **SEO & Accessibility:** Search engines (Google) use headings to index document structure. Screen readers rely on headings to navigate content for visually impaired users.

```
CORRECT HIERARCHY             INCORRECT HIERARCHY
<h1>College Portal</h1>       <h1>College Portal</h1>
  └── <h2>Computer Science</h2> └── <h3>B.Tech Course</h3> (Skipped H2!)
      └── <h3>B.Tech Course</h3>
```

#### Common Beginner Mistake
*   **Mistake:** Selecting a heading tag simply to make text bigger or bolder.
*   **Correction:** Use CSS (`font-size`, `font-weight`) to alter text size. Use heading tags strictly to represent structural hierarchy.

#### CSS Integration
```css
h1 {
  font-size: 2.5rem;
  color: #0f172a;
  border-bottom: 2px solid #e2e8f0;
}
h2 {
  font-size: 1.8rem;
  color: #1e293b;
}
```

#### Summary
*   `<h1>` to `<h6>` represent semantic heading levels in descending order.
*   Use only one `<h1>` per webpage for optimal SEO.
*   Do not select heading tags purely for text styling; use CSS instead.

---

### Topic 13: Paragraph Tag: `<p>`

#### Introduction
The `<p>` tag formats blocks of standard body text. Browsers automatically add vertical space (top and bottom margins) around `<p>` elements to separate paragraphs visually.

#### Handling Whitespaces & Line Breaks
Browsers perform **Whitespace Collapse** when reading HTML. They compress multiple consecutive spaces, tabs, or line breaks into a single space character.

```html
<!-- What you write in code: -->
<p>
   This text has      multiple    spaces 
   and line breaks.
</p>

<!-- What the browser displays: -->
This text has multiple spaces and line breaks.
```
To force an explicit line break inside a paragraph without starting a new paragraph, use the void tag `<br>`.

#### Implementation
```html
<p>
  Welcome to our university portal. We offer world-class technical education.<br />
  Applications for the upcoming semester are now open.
</p>
```

#### CSS Styling
```css
p {
  font-size: 16px;
  line-height: 1.6; /* Improves readability by spacing out text lines */
  color: #334155;
  margin-bottom: 16px;
}
```

#### Summary
*   `<p>` wraps standard text content into separated paragraphs.
*   Browsers collapse multiple internal spaces into a single space.
*   Use `<br>` to insert manual line breaks inside a paragraph.

---

### Topic 14: Preformatted Text: `<pre>`

#### Introduction
The `<pre>` (Preformatted Text) element displays text exactly as written in the HTML source code, preserving all spaces, tabs, and line breaks without whitespace collapse.

#### Differences: `<p>` vs. `<pre>`

| Feature | Paragraph Tag (`<p>`) | Preformatted Tag (`<pre>`) |
| :--- | :--- | :--- |
| **Whitespace Handling** | Collapses multiple spaces into one space | Preserves all spaces, tabs, and formatting |
| **Line Breaks** | Ignores line breaks in code | Preserves code line breaks strictly |
| **Default Font** | Standard proportional font (e.g., Times / Arial) | Monospaced font (e.g., Courier) |
| **Best Used For** | Articles, descriptions, standard prose | Code snippets, ascii art, tabular raw logs |

#### Combining `<pre>` with `<code>`
For displaying programming code on a webpage, nest a `<code>` tag inside a `<pre>` block:

```html
<pre>
<code>
function calculateTotal(price, tax) {
    return price + (price * tax);
}
</code>
</pre>
```

#### CSS Integration
```css
pre {
  background-color: #1e293b;
  color: #f8fafc;
  padding: 15px;
  border-radius: 6px;
  overflow-x: auto; /* Adds horizontal scrollbar if code exceeds container width */
  font-family: "Courier New", Courier, monospace;
}
```

#### Summary
*   `<pre>` preserves all spaces, line breaks, and formatting from the source code.
*   It defaults to a monospaced font family.
*   Useful for showing source code when paired with `<code>`.

---

## Module 5: Anchor Tag and Hyperlinks

---

### Topic 15: Anchor Tag: `<a>`

#### Introduction
Hyperlinks are what connect web pages across the world wide web. The HTML Anchor element `<a>` creates clickable links targeting other pages, section locations, email addresses, or downloadable files.

#### Key Attributes
*   `href` (Hypertext Reference): Specifies the destination target URL or path. Without `href`, the `<a>` tag loses its hyperlink functionality.
*   `target`: Controls where the linked document will open.
    *   `target="_self"` (Default): Opens the link in the same window/tab.
    *   `target="_blank"`: Opens the link in a new browser tab.
*   `rel`: Defines the relationship between the current document and the target document.
    *   *Security Requirement:* Always use `rel="noopener noreferrer"` alongside `target="_blank"` to prevent security vulnerabilities (tabnabbing).
*   `download`: Instructs the browser to download the linked file directly rather than navigating to it.

#### Target Types & Examples

```html
<!-- 1. Absolute URL (External Website) -->
<a href="https://www.google.com" target="_blank" rel="noopener noreferrer">Search Google</a>

<!-- 2. Relative URL (Internal Webpage) -->
<a href="about.html">About Us</a>

<!-- 3. In-Page Anchor Link (Jumps to an ID on the same page) -->
<a href="#contact-section">Jump to Contact</a>

<!-- 4. Email Link -->
<a href="mailto:support@college.edu">Email Admissions</a>

<!-- 5. Telephone Link -->
<a href="tel:+15550199">Call Support</a>

<!-- 6. Download Link -->
<a href="syllabus.pdf" download>Download Syllabus PDF</a>
```

#### Styling Anchor Tags with CSS Pseudo-Classes
Anchor tags can be styled based on user interaction states using CSS pseudo-classes:

```css
/* Base link style */
a {
  color: #2563eb;
  text-decoration: underline;
}

/* Hover state (Mouse over link) */
a:hover {
  color: #1d4ed8;
  text-decoration: none;
}

/* Visited state (User has previously clicked this link) */
a:visited {
  color: #7c3aed;
}

/* Active state (Moment mouse button is held down) */
a:active {
  color: #dc2626;
}

/* Custom Button Link Style */
.btn-link {
  display: inline-block;
  padding: 10px 20px;
  background-color: #2563eb;
  color: white;
  border-radius: 4px;
  text-decoration: none;
}
```

#### Anchor Link vs. `<button>` Element
*   **Anchor (`<a>`):** Used for **navigation**—taking the user to a new location or page.
*   **Button (`<button>`):** Used for **actions**—submitting forms, triggering JavaScript functions, opening popups/dialogs without changing pages.

#### Summary
*   The `<a>` tag creates hyperlinks using the required `href` attribute.
*   Use `target="_blank"` with `rel="noopener noreferrer"` to safely open links in new tabs.
*   Use `<a>` for navigation and `<button>` for in-page user actions.

---

## Module 6: HTML Lists

---

### Topic 16: Introduction to Lists

#### Introduction
Lists organize related pieces of information in a clear, sequential, or structured format. HTML provides three distinct types of lists:
1.  **Ordered List (`<ol>`):** Sequenced items where order matters (numbered).
2.  **Unordered List (`<ul>`):** Unsequenced items where order does not matter (bulleted).
3.  **Description List (`<dl>`):** Name-value / term-definition pairs.

---

### A. Ordered List: `<ol>`

#### Purpose & Attributes
Used when the sequence of items is important (e.g., step-by-step tutorials, top 10 rankings). Individual items are wrapped in `<li>` (List Item) tags.

##### Key Attributes:
*   `type`: Changes the marker numbering style.
    *   `type="1"`: Numbers (1, 2, 3) - Default
    *   `type="A"`: Uppercase Letters (A, B, C)
    *   `type="a"`: Lowercase Letters (a, b, c)
    *   `type="I"`: Uppercase Roman Numerals (I, II, III)
    *   `type="i"`: Lowercase Roman Numerals (i, ii, iii)
*   `start`: Specifies the starting numerical value for the list.
*   `reversed`: Reverses the numbering order (e.g., 3, 2, 1).

#### Implementation
```html
<h4>Steps to Enroll in Course</h4>
<ol type="A" start="1">
  <li>Register an account on the student portal.</li>
  <li>Select your preferred course modules.</li>
  <li>Pay the tuition fee online.</li>
</ol>
```

#### HTML Attribute vs. CSS List Styling
While the HTML `type` attribute changes numbering styles, CSS is preferred for visual styling:
```css
ol {
  list-style-type: upper-roman; /* Changes numbering to I, II, III via CSS */
}
```

---

### B. Unordered List: `<ul>`

#### Purpose & Bullet Options
Used when items do not require a specific sequence (e.g., shopping lists, feature bullets, navigation menus).

##### CSS `list-style-type` Values:
*   `disc`: Solid dark circle (Default)
*   `circle`: Hollow circle
*   `square`: Solid square
*   `none`: Removes all visible markers (commonly used for navigation bars)

#### Implementation
```html
<ul style="list-style-type: square;">
  <li>HTML5 Structure</li>
  <li>CSS3 Styling</li>
  <li>JavaScript Logic</li>
</ul>
```

---

### C. Description List: `<dl>`

#### Purpose & Structure
Displays terms alongside their corresponding definitions or descriptions.
*   `<dl>`: Description List wrapper container.
*   `<dt>`: Description Term (the word or title being defined).
*   `<dd>`: Description Details (the explanation or definition).

#### Implementation
```html
<dl>
  <dt>HTML</dt>
  <dd>HyperText Markup Language used for structuring web pages.</dd>
  <dt>CSS</dt>
  <dd>Cascading Style Sheets used for styling document layouts.</dd>
</dl>
```

---

### Topic 17: Nested Lists

#### Introduction
A nested list is a list placed inside an item (`<li>`) of another list. This is used to display hierarchical data such as course curriculums, site menus, or multi-level outlines.

#### Structural Rule
**Important Syntax Rule:** A sub-list (`<ul>` or `<ol>`) must be placed **inside an individual `<li>` tag**, not directly inside the parent `<ol>` or `<ul>`.

#### Correct Nesting Implementation
```html
<h2>Computer Science Curriculum</h2>
<ul>
  <li>
    Semester 1
    <ol type="i">
      <li>Mathematics I</li>
      <li>Computer Fundamentals</li>
    </ol>
  </li>
  <li>
    Semester 2
    <ol type="i">
      <li>Data Structures</li>
      <li>Web Development Essentials</li>
    </ol>
  </li>
</ul>
```

#### Output Representation
```
• Semester 1
   i. Mathematics I
  ii. Computer Fundamentals
• Semester 2
   i. Data Structures
  ii. Web Development Essentials
```

#### Summary
*   `<ol>` creates numbered lists; `<ul>` creates bulleted lists; `<dl>` creates term-definition pairs.
*   Control numbering/bullets using the CSS property `list-style-type`.
*   Nested sub-lists must always be placed inside `<li>` elements.

---

## Module 7: HTML Tables

---

### Topic 18: Introduction to Tables

#### Introduction
HTML tables display structured **tabular data**—data organized logically into rows and columns (e.g., student grade sheets, timetables, pricing matrices).

#### Crucial Layout Rule
**NEVER use HTML tables to build page layouts.** Using tables for general page layout creates poor responsiveness on mobile devices, broken accessibility for screen readers, and bloated code. Page layouts must be built using CSS Flexbox or Grid.

---

### Topic 19: Table Structure

#### Table Components
Modern semantic tables use specific tags to divide data into distinct structural zones:

*   `<table>`: Root wrapper element for tabular data.
*   `<caption>`: Sets an accessible title for the table.
*   `<thead>`: Wraps the table header rows containing column labels.
*   `<tbody>`: Wraps the core content data rows.
*   `<tfoot>`: Wraps summary rows (e.g., totals, averages) at the bottom.
*   `<tr>`: Table Row container.
*   `<th>`: Table Header cell (Displays text **bold** and **centered** by default).
*   `<td>`: Table Data cell (Displays text **regular weight** and **left-aligned** by default).
*   `scope`: An attribute on `<th>` (`scope="col"` or `scope="row"`) that tells screen readers whether the header applies to an entire column or row.

#### Complete Semantic Table Example
```html
<table>
  <caption>Student Academic Performance</caption>
  <thead>
    <tr>
      <th scope="col">Roll No</th>
      <th scope="col">Student Name</th>
      <th scope="col">Marks</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>101</td>
      <td>Alice Johnson</td>
      <td>88</td>
    </tr>
    <tr>
      <td>102</td>
      <td>Bob Smith</td>
      <td>92</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td colspan="2">Average Marks</td>
      <td>90</td>
    </tr>
  </tfoot>
</table>
```

---

### Topic 20: Table Attributes and Cell Spanning

#### Spanning Rows and Columns
Cell spanning allows a single table cell to expand across multiple columns or rows.

*   `colspan="N"`: Expands a cell horizontally across `N` columns.
*   `rowspan="N"`: Expands a cell vertically across `N` rows.

#### Code Example (Cell Spanning)
```html
<table border="1">
  <tr>
    <th>Student</th>
    <th colspan="2">Contact Information</th> <!-- Spans 2 columns -->
  </tr>
  <tr>
    <td>John</td>
    <td>Email: john@test.com</td>
    <td>Phone: 555-0199</td>
  </tr>
  <tr>
    <td rowspan="2">Alice</td> <!-- Spans 2 rows -->
    <td colspan="2">Email: alice@test.com</td>
  </tr>
  <tr>
    <td colspan="2">Phone: 555-0144</td>
  </tr>
</table>
```

---

### Topic 21: Styling Tables with CSS

#### Essential Table CSS Properties
*   `border-collapse: collapse;`: Merges double table borders into a clean single line.
*   `padding`: Adds breathing room inside table cells.
*   `:nth-child(even)`: Applies alternating background colors to rows (Zebra Striping).

#### Clean CSS Implementation
```css
table {
  width: 100%;
  border-collapse: collapse; /* Essential for clean borders */
  margin-top: 20px;
}

th, td {
  border: 1px solid #cbd5e1;
  padding: 12px;
  text-align: left;
}

th {
  background-color: #1e293b;
  color: white;
}

/* Zebra Striping */
tbody tr:nth-child(even) {
  background-color: #f8fafc;
}

/* Hover Effect */
tbody tr:hover {
  background-color: #f1f5f9;
}
```

---

### Topic 22: Nested Tables

#### Introduction
A nested table is a full HTML `<table>` placed inside a `<td>` cell of an outer table.

#### Usage Warning
Nested tables increase document complexity and make reading content difficult for assistive technologies. Use nested tables sparingly and only when data requires multi-dimensional sub-tables.

#### Code Example
```html
<table border="1">
  <tr>
    <th>Student Name</th>
    <th>Subject Marks</th>
  </tr>
  <tr>
    <td>Alex</td>
    <td>
      <!-- Nested Table Inside TD -->
      <table border="1">
        <tr><th>Math</th><td>95</td></tr>
        <tr><th>Science</th><td>89</td></tr>
      </table>
    </td>
  </tr>
</table>
```

#### Summary
*   Use tables exclusively for tabular data; never for general page layouts.
*   Structure tables using semantic tags: `<caption>`, `<thead>`, `<tbody>`, `<tfoot>`, `<tr>`, `<th>`, and `<td>`.
*   Use `colspan` and `rowspan` to merge cells across columns or rows.
*   Always apply `border-collapse: collapse;` in CSS for clean table borders.

---

## Module 8: The `<div>` Element and Layout

---

### Topic 23: Introduction to `<div>`

#### Introduction
The `<div>` (Division) element is a non-semantic, block-level **generic container**. It carries no inherent structural meaning or default visual style. It is used to group related HTML elements together so they can be styled as a single unit using CSS or manipulated using JavaScript.

#### Human Analogy
Think of a `<div>` as a **cardboard box**:
*   The box itself has no specific identity.
*   You place related items (a group of toys, or books) inside the box.
*   You can label the box with a marker (assigning a `class` or `id`) to organize, style, or move all items inside it together.

```html
<div class="profile-card">
  <h2>Sarah Jenkins</h2>
  <p>Software Engineer</p>
</div>
```

---

### Topic 24: Creating Layouts with `<div>` vs. Semantic Structural Tags

Before HTML5, web layouts were built using nested `<div>` tags with `id` attributes (e.g., `<div id="header">`). Modern HTML replaces these generic containers with clear **Semantic Layout Tags**:

```
+-------------------------------------------------------------------------+
|                                <header>                                 |
+-------------------------------------------------------------------------+
|                                  <nav>                                  |
+-------------------------------------------------------------------------+
|                       |                                                 |
|       <aside>         |                     <main>                      |
|      (Sidebar)        |                 (Main Content)                  |
|                       |                                                 |
+-----------------------+-------------------------------------------------+
|                                <footer>                                 |
+-------------------------------------------------------------------------+
```

*   `<header>`: Introductions, branding, titles, and site logos.
*   `<nav>`: Main navigation menu link groups.
*   `<main>`: Primary, unique content of the page.
*   `<aside>`: Secondary content, sidebars, or related links.
*   `<footer>`: Copyright declarations, legal terms, and contact links.

---

### Topic 25: Aligning Divs Using CSS Layout Methods

---

#### A. Text Alignment (`text-align`)
*   **Property:** `text-align: center | left | right | justify;`
*   **Behavior:** Align inline content (text, inline images, links) inside a block parent container.
*   **Note:** It does **not** align block-level `<div>` elements themselves, only the inline content inside them.

---

#### B. Float Layout (Legacy Method)
*   **Property:** `float: left;` or `float: right;`
*   **Behavior:** Removes the element from normal page flow, pushing it to the left or right edge of its parent container. Surrounding text flows around it.
*   **Clearing Floats:** Following elements must apply `clear: both;` to avoid sliding beneath floating elements.

##### Float Code Example:
```html
<style>
  .column-left {
    float: left;
    width: 48%;
    background: #e2e8f0;
  }
  .column-right {
    float: right;
    width: 48%;
    background: #cbd5e1;
  }
  .clearfix {
    clear: both; /* Prevents container collapse */
  }
</style>

<div class="column-left">Left Column</div>
<div class="column-right">Right Column</div>
<div class="clearfix"></div>
```

---

#### C. Flexbox Layout (Modern 1D Layout System)
Flexbox is designed for 1-dimensional layouts (arranging elements in either a single row or a single column).

##### Essential Flexbox Properties:
*   `display: flex;`: Enables flex context on the parent container.
*   `flex-direction: row | column;`: Defines main layout axis.
*   `justify-content: flex-start | center | space-between | space-around;`: Aligns items along the main horizontal axis.
*   `align-items: stretch | center | flex-start | flex-end;`: Aligns items along the cross vertical axis.
*   `gap: 20px;`: Sets consistent spacing between child elements.

##### Flexbox Code Example:
```css
.card-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 16px;
}
```

---

#### D. CSS Grid Layout (Modern 2D Layout System)
Grid is designed for complex 2-dimensional layouts (managing both rows and columns simultaneously).

##### Essential Grid Properties:
*   `display: grid;`: Turns parent into a grid container.
*   `grid-template-columns`: Defines column widths (e.g., `repeat(3, 1fr)` creates 3 equal columns).
*   `gap`: Sets spacing between grid rows and columns.

##### CSS Grid Code Example:
```css
.dashboard-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
```

#### Summary
*   `<div>` is a generic container used to group elements for styling or layout.
*   Prefer semantic structural tags (`<header>`, `<nav>`, `<main>`, `<footer>`) over generic divs for layout regions.
*   Use Flexbox for single-row or single-column layouts; use CSS Grid for complex 2D layouts.

---

## Module 9: Block, Inline, and Inline-Block Elements

---

### Topic 26: Block-Level Elements

#### Characteristics
*   Starts on a brand-new line by default.
*   Spans the full width of its parent container (100% width).
*   Respects all box model properties: `width`, `height`, `margin`, and `padding`.
*   *Examples:* `<div>`, `<p>`, `<h1>`-`<h6>`, `<ul>`, `<ol>`, `<li>`, `<table>`, `<header>`, `<footer>`.

---

### Topic 27: Inline Elements

#### Characteristics
*   Does **not** start on a new line; sits directly alongside adjacent inline elements.
*   Only occupies the width required by its inner content.
*   Ignores custom `width` and `height` properties.
*   Accepts horizontal padding/margins (`margin-left`, `margin-right`), but vertical margins (`margin-top`, `margin-bottom`) are ignored or do not push adjacent elements away.
*   *Examples:* `<span>`, `<a>`, `<strong>`, `<em>`, `<code>`, `<label>`.

---

### Topic 28: Inline-Block Elements

#### Characteristics
*    Combines the multi-element flow of inline tags with the box model styling of block elements.
*   Sits side-by-side on the same line with other elements (like inline tags).
*   Respects explicit `width`, `height`, `margin`, and `padding` dimensions (like block tags).
*   *Examples:* `<button>`, `<input>`, `<img>`, or any element styled with `display: inline-block;`.

```
DISPLAY TYPE COMPARISON:

1. display: block
+-------------------------------------------------------------------------+
| [Block Element] - Forces new line, takes 100% full container width       |
+-------------------------------------------------------------------------+

2. display: inline
[Inline 1] [Inline 2] (Ignores width/height styles, sits on same line)

3. display: inline-block
+-------------------+ +-------------------+
| [Inline-Block 1]  | | [Inline-Block 2]  |  (Sits on same line,
| Width: 150px      | | Width: 150px      |   respects custom width/height)
+-------------------+ +-------------------+
```

---

### Topic 29: Master Display Comparison Matrix

| Property / Feature | Block (`display: block`) | Inline (`display: inline`) | Inline-Block (`display: inline-block`) |
| :--- | :--- | :--- | :--- |
| **Starts on New Line?** | Yes | No | No |
| **Default Width** | 100% of parent container | Fits content size | Fits content size |
| **Accepts `width` & `height`?** | Yes | No (Ignored) | Yes |
| **Accepts Vertical Margins?** | Yes | No | Yes |
| **Accepts Horizontal Margins?**| Yes | Yes | Yes |
| **Common Use Cases** | Structural sections, cards | Text highlights, links | Buttons, badges, form controls |

#### Demonstrative Code Example
```html
<style>
  .box-block {
    display: block;
    width: 200px;
    height: 40px;
    background-color: #fca5a5;
    margin: 5px 0;
  }
  .box-inline {
    display: inline;
    width: 200px; /* Ignored! */
    height: 40px; /* Ignored! */
    background-color: #86efac;
    padding: 5px;
  }
  .box-inlineblock {
    display: inline-block;
    width: 150px;
    height: 40px;
    background-color: #93c5fd;
    margin: 5px;
  }
</style>

<div class="box-block">Block Box 1</div>
<div class="box-block">Block Box 2</div>

<span class="box-inline">Inline Span 1</span>
<span class="box-inline">Inline Span 2</span>

<div class="box-inlineblock">Inline-Block 1</div>
<div class="box-inlineblock">Inline-Block 2</div>
```

#### Summary
*   Block elements stack vertically and span 100% width.
*   Inline elements flow horizontally and ignore width/height dimensions.
*   Inline-block elements flow horizontally while respecting custom width, height, and margins.

---

## Module 10: Practice and Assessment

---

### A. Conceptual Questions

1. What is the full form of HTML, and why is it categorized as a markup language rather than a programming language?
2. Explain the purpose of the `<!DOCTYPE html>` declaration placed at the top of HTML documents.
3. What is character encoding? Why is `<meta charset="UTF-8">` recommended for modern web pages?
4. Describe the primary functional difference between the `<head>` and `<body>` sections of an HTML document.
5. Explain the concept of the Document Object Model (DOM) and how it differs from static HTML source code.
6. What are void (empty) elements in HTML? List four examples of void tags.
7. Compare block-level elements and inline elements based on line placement and width behavior.
8. What is the difference between an HTML attribute and a DOM property? Illustrate using an `<input>` text box example.
9. Define the three methods used to apply CSS to an HTML document. Which method is best for production environments and why?
10. Explain the CSS specificity hierarchy order among inline styles, class selectors, ID selectors, and element selectors.
11. Why is it recommended to use only one `<h1>` tag per webpage? What are the SEO and accessibility implications?
12. How does a browser handle multiple contiguous spaces and line breaks inside standard paragraph `<p>` tags?
13. Explain the difference between `<p>` and `<pre>` elements in terms of whitespace preservation and visual display.
14. What is the security risk associated with using `target="_blank"` on anchor links, and how does `rel="noopener noreferrer"` mitigate it?
15. Differentiate between an anchor link (`<a>`) and a button (`<button>`) in terms of their semantic purpose.
16. Compare the three types of HTML lists (`<ol>`, `<ul>`, `<dl>`) and provide a valid use case for each.
17. Describe the correct structural method for creating nested lists in HTML.
18. Explain why using HTML tables for primary webpage layouts is considered bad practice.
19. What are the roles of `colspan` and `rowspan` attributes in HTML tables?
20. Explain the structural and visual differences between `display: inline`, `display: block`, and `display: inline-block`.

---

### B. Practical Coding Tasks

1. **Boilerplate Creation:** Write a valid HTML5 document containing meta character set tags, a viewable title reading "My First Web Page", and a visible heading in the body.
2. **Text Structure Assignment:** Create a web page displaying a main heading, two sub-headings, and three paragraphs styled with a line-height of 1.6 and custom font sizing.
3. **Preformatted Code Snippet:** Display a C++ or JavaScript code block on a webpage preserved with original indentation using `<pre>` and `<code>` tags.
4. **External Navigation Bar:** Create an HTML unordered list containing links to three pages (`index.html`, `about.html`, `contact.html`). Style the list horizontally without bullets using CSS.
5. **In-Page Jump Links:** Build a long single-page HTML file with a navigation header linking to three distinct section IDs (`#about`, `#services`, `#contact`) located further down the page.
6. **Multi-Type List:** Construct an ordered list showing the top 3 priorities for a student. Inside priority item #1, nest an unordered list detailing sub-tasks.
7. **Description Glossary:** Build a description list (`<dl>`) containing terms and definitions for Web Development, API, Server, and Database.
8. **Student Marksheet Table:** Construct a fully styled semantic table (`<table>`, `<thead>`, `<tbody>`, `<tfoot>`) displaying marks for 3 students across 3 subjects with total average values in the footer.
9. **Merged Table Cells:** Create a table timetable layout using `colspan` to merge a single row cell across 3 columns representing a "Lunch Break".
10. **Custom Styled Buttons:** Create three `<a>` elements styled using `display: inline-block`, padding, rounded corners, and background colors to look like buttons.
11. **CSS Specificity Test:** Write an HTML heading with an `id` and a `class`. Write internal CSS targeting the heading via element, class, and ID selectors with conflicting colors to observe which style wins.
12. **Card Layout Container:** Build a profile card using a `<div>` wrapper containing an image placeholder, an `<h3>` name, a `<p>` biography, and an anchor link formatted as a button.
13. **Flexbox Layout Task:** Align three summary stat cards horizontally side-by-side with equal spacing between them using Flexbox (`display: flex`).
14. **Responsive Table Wrapper:** Wrap a multi-column data table inside a container `<div>` configured with CSS `overflow-x: auto` to allow horizontal scrolling on small screen sizes.
15. **Display Property Comparison:** Create three `<div>` elements styled with identical widths and heights, but set their CSS display properties to `block`, `inline`, and `inline-block` respectively to observe screen flow differences.

---

### C. Debugging Exercises

#### 1. Fix the Invalid Nesting and Closing Error
*   **Incorrect Code:**
    ```html
    <p>Welcome to the portal <div>Information box content</p></div>
    ```
*   **Correction & Explanation:**
    ```html
    <div>
      <p>Welcome to the portal</p>
      <div>Information box content</div>
    </div>
    ```
    *Explanation:* A block-level `<div>` cannot be nested inside a `<p>` element, and opening/closing tags must not overlap incorrectly.

#### 2. Fix the Invalid Void Element Tag
*   **Incorrect Code:**
    ```html
    <img src="logo.png" alt="Company Logo"></img>
    ```
*   **Correction & Explanation:**
    ```html
    <img src="logo.png" alt="Company Logo" />
    ```
    *Explanation:* `<img>` is a void (empty) element and must not have a closing `</img>` tag.

#### 3. Fix the Link Security and Target Bug
*   **Incorrect Code:**
    ```html
    <a href="https://example.com" target="blank">Visit External Site</a>
    ```
*   **Correction & Explanation:**
    ```html
    <a href="https://example.com" target="_blank" rel="noopener noreferrer">Visit External Site</a>
    ```
    *Explanation:* Missing the underscore in `_blank` (causes it to open in a frame named "blank") and missing `rel="noopener noreferrer"` security attributes.

#### 4. Fix Broken Nested List Syntax
*   **Incorrect Code:**
    ```html
    <ul>
      <li>Frontend Technologies</li>
      <ul>
        <li>HTML</li>
        <li>CSS</li>
      </ul>
    </ul>
    ```
*   **Correction & Explanation:**
    ```html
    <ul>
      <li>
        Frontend Technologies
        <ul>
          <li>HTML</li>
          <li>CSS</li>
        </ul>
      </li>
    </ul>
    ```
    *Explanation:* The nested `<ul>` must be placed *inside* the parent `<li>` tag, rather than directly inside another `<ul>`.

#### 5. Fix Broken Table Row Structure
*   **Incorrect Code:**
    ```html
    <table>
      <tr>
        <td>Name</td>
        <td>Age</td>
      </tr>
      <td>Alice</td>
      <td>22</td>
    </table>
    ```
*   **Correction & Explanation:**
    ```html
    <table>
      <tr>
        <td>Name</td>
        <td>Age</td>
      </tr>
      <tr>
        <td>Alice</td>
        <td>22</td>
      </tr>
    </table>
    ```
    *Explanation:* Data cells (`<td>`) must always be wrapped inside Table Row (`<tr>`) elements.

---

### D. Output Prediction Questions

#### Question 1
```html
<p>Hello       World!
This is   a test.</p>
```
*   **Predicted Output:**
    `Hello World! This is a test.`
*   **Explanation:** The browser collapses all multiple spaces, tabs, and newlines inside `<p>` tags into a single space.

---

#### Question 2
```html
<style>
  .text-box { color: blue; }
  #main-text { color: red; }
  p { color: green; }
</style>
<p id="main-text" class="text-box" style="color: orange;">Sample Text</p>
```
*   **Predicted Output:** The text renders in **orange**.
*   **Explanation:** The inline style attribute (`style="color: orange;"`) has the highest specificity score (1,0,0,0), overriding the ID selector (0,1,0,0), class selector (0,0,1,0), and element selector (0,0,0,1).

---

#### Question 3
```html
<span style="width: 200px; height: 100px; background-color: yellow;">Inline Test</span>
```
*   **Predicted Output:** A yellow background box sized **only around the text width/height**, ignoring the `200px` width and `100px` height inline styles.
*   **Explanation:** Non-replaced inline elements (`<span>`) ignore CSS `width` and `height` properties.

---

### E. Interview Questions and Answers

##### Q1: What is the primary difference between HTML semantic tags and non-semantic tags?
*   **Answer:** Semantic tags (e.g., `<header>`, `<article>`, `<nav>`) clearly describe the operational purpose and meaning of their enclosed content to browsers, search engines, and assistive screen readers. Non-semantic tags (e.g., `<div>`, `<span>`) serve strictly as generic visual containers with zero inherent semantic meaning.

##### Q2: Why is the `alt` attribute mandatory on `<img>` tags?
*   **Answer:** The `alt` (alternate text) attribute provides a text fallback displayed if the image fails to load due to broken paths or network errors. Crucially, screen readers read `alt` text aloud to visually impaired users, ensuring web accessibility compliance (WCAG).

##### Q3: What is CSS Specificity and how is it calculated?
*   **Answer:** Specificity is the scoring system browsers use to determine which CSS styling rule overrides others when multiple rules target the same element. It is calculated based on four categories: Inline Styles (1,0,0,0) > ID Selectors (0,1,0,0) > Class/Attribute Selectors (0,0,1,0) > Element Selectors (0,0,0,1).

##### Q4: Explain the difference between `display: none` and `visibility: hidden` in CSS.
*   **Answer:** `display: none` completely removes the element from the document visual rendering tree, causing the page layout to collapse and re-flow as if the element does not exist. `visibility: hidden` hides the element visually, but the element continues to occupy its original layout space on the screen canvas.

##### Q5: What is the difference between relative and absolute positioning in CSS?
*   **Answer:** `position: relative` offsets an element relative to its normal natural layout position without affecting surrounding elements. `position: absolute` removes the element completely from normal page flow, positioning it relative to its nearest ancestor element configured with `position: relative` (or the initial document viewport if no relative ancestor exists).

---

### F. Quick Revision Sheet

#### Key Structural Tags
*   `<!DOCTYPE html>`: Declares modern HTML5 document type.
*   `<html>`: Root element wrapping all document nodes.
*   `<head>`: Encloses metadata, titles, styles, and asset links.
*   `<body>`: Contains all visible page content canvas elements.
*   `<header>`, `<nav>`, `<main>`, `<aside>`, `<footer>`: HTML5 semantic structural layout tags.

#### Essential Text Formatting Syntax
*   `<h1>` to `<h6>`: Headings (Level 1 highest to Level 6 lowest).
*   `<p>`: Paragraph text container (collapses internal whitespace).
*   `<pre>`: Preformatted text container (preserves spaces and breaks).
*   `<strong>`: Semantic bold text (emphasizes importance).
*   `<em>`: Semantic italicized text (emphasizes tone).

#### Hyperlinks & Attributes
*   `<a href="URL">`: Link tag. `href` attribute is mandatory.
*   `target="_blank"`: Opens link in a new tab.
*   `rel="noopener noreferrer"`: Security requirement for new tab links.

#### Essential Display Properties
*   `display: block;`: New line, 100% width, respects width/height dimensions.
*   `display: inline;`: Same line, content width only, ignores custom width/height.
*   `display: inline-block;`: Same line, respects custom width/height dimensions.
