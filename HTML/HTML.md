# HTML

##  Introduction to HTML

**HTML (Hypertext Markup Language)** is the standard language used to create and structure web pages. Think of HTML as the **skeleton of a webpage**—it defines the layout and elements, while CSS adds styling (clothes) and JavaScript adds interactivity (brain).

Example:

```html
<!DOCTYPE html>
<html>
<head>
  <title>My First Webpage</title>
</head>
<body>
  <h1>Hello, World!</h1>
  <p>This is my first HTML page.</p>
</body>
</html>

```

- `<!DOCTYPE html>` → Defines the document as HTML5.
- `<html>` → Root element.
- `<head>` → Metadata (title, links, etc.).
- `<body>` → Visible content.

---

##  Basic Structure of an HTML Document

Every HTML document follows this structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document Title</title>
</head>
<body>
  <!-- Page content goes here -->
</body>
</html>

```

### Key Elements:

- `<meta charset="UTF-8">` → Ensures proper text encoding.
- `<meta name="viewport">` → Makes website responsive.
- `<title>` → Displays the title in the browser tab.

---

##  Heading and Paragraph

🔹 Headings in HTML

- **Purpose**: Define titles and subtitles on a webpage.
- **Tags**: `<h1>` to `<h6>`
    - `<h1>` → Highest (most important, largest text)
    - `<h6>` → Lowest (least important, smallest text)
- **SEO Importance**:
    - `<h1>` is usually used for the **main page title** (only one per page is recommended).
    - `<h2>–<h6>` are used for sections, subsections, and hierarchy.

 Example:

```html
<h1>Main Title</h1>
<h2>Section Heading</h2>
<h3>Subsection Heading</h3>

```

 **Notes**:

- Browsers automatically add **top and bottom margin** around headings.
- Headings should be used for **content structure**, not styling (use CSS for styles).

---

### 🔹 Paragraphs in HTML

- **Purpose**: Used to display blocks of text.
- **Tag**: `<p> ... </p>`
- Browsers automatically add **space (margin)** before and after each paragraph.

 Example:

```html
<p>This is the first paragraph.</p>
<p>This is another paragraph of text.</p>

```

 **Notes**:

- Paragraphs automatically **wrap text** inside the tag.
- Extra spaces, tabs, and line breaks inside `<p>` are **ignored by browsers** (HTML collapses whitespace).
- Use `<br>` if you want a **line break** inside a paragraph without starting a new one.

 Example with `<br>`:

```html
<p>This is line one.<br>This is line two.</p>

```

---

### 🔹 Key Differences

|Feature|Headings (`<h1>-<h6>`)|Paragraph (`<p>`)|
|---|---|---|
|Usage|Titles/Subtitles|Text content|
|SEO Value|High (especially `<h1>`)|Low|
|Default Style|Bold, larger font size|Normal text|
|Frequency|One `<h1>` per page recommended|Unlimited|

---

##  HTML Links & Anchors

### 🔹 Anchor Tag (`<a>`)

- **Purpose**: Creates hyperlinks (links to another page, file, email, or section).
- **Syntax**:

```html
<a href="URL">Link Text</a>

```

---

### 🔹 Types of Links

1. **Absolute URL (external website)**

```html
<a href="<https://www.google.com>">Go to Google</a>

```

1. **Relative URL (linking within same project)**

```html
<a href="about.html">About Page</a>

```

1. **Email Link**

```html
<a href="mailto:someone@example.com">Send Email</a>

```

1. **Telephone Link**

```html
<a href="tel:+911234567890">Call Us</a>

```

---

### 🔹 Anchor Tag Attributes

|Attribute|Description|Example|
|---|---|---|
|`href`|Destination URL|`<a href="<https://example.com>">Visit</a>`|
|`target="_blank"`|Opens link in new tab|`<a href="page.html" target="_blank">Open</a>`|
|`title`|Tooltip text on hover|`<a href="home.html" title="Go Home">Home</a>`|
|`download`|Download file instead of opening|`<a href="file.pdf" download>Download PDF</a>`|

---

### 🔹 Internal Page Navigation (Anchors)

- You can jump to specific sections on the same page using **id** and **#**.

 Example:

```html
<a href="#section1">Go to Section 1</a>

<h2 id="section1">Section 1</h2>
<p>This is section 1 content.</p>

```

---

### 🔹 Styling Links (Default Behavior)

- By default:
    - **Unvisited link** → Blue and underlined
    - **Visited link** → Purple
    - **Active link** → Red (when clicked)

 Example (CSS):

```css
a:link { color: blue; }
a:visited { color: purple; }
a:hover { color: green; }
a:active { color: red; }

```

---

 **Quick Demo**

```html
<!DOCTYPE html>
<html>
<head>
  <title>Links Example</title>
</head>
<body>
  <h1>HTML Links & Anchors</h1>

  <!-- Absolute Link -->
  <p><a href="<https://www.google.com>" target="_blank">Visit Google</a></p>

  <!-- Relative Link -->
  <p><a href="about.html">About Us</a></p>

  <!-- Email Link -->
  <p><a href="mailto:info@example.com">Contact Us</a></p>

  <!-- Internal Page Link -->
  <p><a href="#section2">Go to Section 2</a></p>

  <h2 id="section2">Section 2</h2>
  <p>This is section 2 content.</p>
</body>
</html>

```

---

##  HTML Images

### 🔹 Basic Image Tag

- Images are inserted with `<img>` tag (self-closing).
- **Syntax**:

```html
<img src="image.jpg" alt="Description of image">

```

### Attributes:

|Attribute|Description|
|---|---|
|`src`|Path/URL of the image file|
|`alt`|Alternate text (shown if image fails to load; important for SEO & accessibility)|
|`width`|Sets image width (in px or %)|
|`height`|Sets image height (in px or %)|
|`title`|Tooltip when hovering over the image|

 Example:

```html
<img src="cat.jpg" alt="Cute Cat" width="300" height="200" title="My Pet Cat">

```

---

### 🔹 Image Sources

1. **Local Image**

```html
<img src="images/dog.png" alt="Dog">

```

### **Online Image (absolute URL)**

```html
<img src="<https://example.com/pic.jpg>" alt="Remote Picture">

```

---

### 🔹 Image as a Link

You can wrap an image inside an `<a>` tag:

```html
<a href="<https://www.google.com>">
  <img src="google-logo.png" alt="Google Logo" width="150">
</a>

```

---

### 🔹 Responsive Images

- Make images adjust to screen size using CSS.

```css
img {
  max-width: 100%;
  height: auto;
}

```

This ensures the image **scales down** on smaller screens without breaking layout.

---

### 🔹 Image with Caption

Use `<figure>` and `<figcaption>` for semantic captions.

```html
<figure>
  <img src="mountain.jpg" alt="Snowy Mountain" width="400">
  <figcaption>Beautiful Snowy Mountain</figcaption>
</figure>

```

---

### 🔹 Image Formats

- **JPEG (.jpg)** → Best for photos (smaller size, lossy).
- **PNG (.png)** → Transparent backgrounds, sharp edges (logos, icons).
- **GIF (.gif)** → Simple animations.
- **SVG (.svg)** → Scalable vector graphics (icons, logos, illustrations).
- **WebP (.webp)** → Modern format (smaller + better quality).

---

 **Quick Demo Page**

```html
<!DOCTYPE html>
<html>
<head>
  <title>Image Examples</title>
  <style>
    img { border-radius: 10px; }
  </style>
</head>
<body>

  <h2>Basic Image</h2>
  <img src="cat.jpg" alt="Cute Cat" width="250">

  <h2>Image as a Link</h2>
  <a href="<https://www.wikipedia.org>">
    <img src="wiki-logo.png" alt="Wikipedia" width="150">
  </a>

  <h2>Image with Caption</h2>
  <figure>
    <img src="nature.jpg" alt="Nature View" width="300">
    <figcaption>Nature at its best 🌿</figcaption>
  </figure>

</body>
</html>

```

---

##  HTML Lists

HTML provides 3 main types of lists:

1. **Ordered List (`<ol>`)** – Numbered list
2. **Unordered List (`<ul>`)** – Bulleted list
3. **Description List (`<dl>`)** – Term & description list

---

### 🔹 1. Ordered List (`<ol>`)

- Items are **numbered** (1, 2, 3… by default).
- Each item goes inside `<li>`.

 Example:

```html
<ol>
  <li>HTML</li>
  <li>CSS</li>
  <li>JavaScript</li>
</ol>

```

### Attributes:

- `type` → Changes numbering style
    - `1` → Numbers (default)
    - `A` → Uppercase letters
    - `a` → Lowercase letters
    - `I` → Roman numerals (uppercase)
    - `i` → Roman numerals (lowercase)

 Example:

```html
<ol type="A">
  <li>Step One</li>
  <li>Step Two</li>
</ol>

```

- `start` → Sets starting number/letter

```html
<ol start="5">
  <li>Point One</li>
  <li>Point Two</li>
</ol>

```

---

### 🔹 2. Unordered List (`<ul>`)

- Items are marked with **bullets** (• by default).

 Example:

```html
<ul>
  <li>Apples</li>
  <li>Bananas</li>
  <li>Oranges</li>
</ul>

```

### Attribute:

- `type` → Changes bullet style (but now deprecated, better use CSS).
    - `disc` → ● (default)
    - `circle` → ○
    - `square` → ■

 Example (with CSS instead of `type`):

```html
<ul style="list-style-type: square;">
  <li>Red</li>
  <li>Green</li>
  <li>Blue</li>
</ul>

```

---

### 🔹 3. Description List (`<dl>`)

- Used for definitions, terms, FAQs.
- `<dt>` → Definition term
- `<dd>` → Definition description

 Example:

```html
<dl>
  <dt>HTML</dt>
  <dd>Standard language for creating webpages.</dd>

  <dt>CSS</dt>
  <dd>Used for styling and layout.</dd>
</dl>

```

---

### 🔹 Nested Lists

- You can place one list inside another.

 Example:

```html
<ul>
  <li>Frontend
    <ol>
      <li>HTML</li>
      <li>CSS</li>
    </ol>
  </li>
  <li>Backend
    <ul>
      <li>Node.js</li>
      <li>Express</li>
    </ul>
  </li>
</ul>

```

---

### 🔹 Styling Lists with CSS

```css
ul {
  list-style-type: square;
  padding-left: 20px;
}
ol {
  list-style-type: upper-roman;
}

```

---

## HTML Tables

### 🔹 What is a Table?

- A table displays **data in rows and columns**.
- Created using the `<table>` element.

---

### 🔹 Basic Table Structure

|Tag|Purpose|
|---|---|
|`<table>`|Defines the table|
|`<tr>`|Defines a table row|
|`<td>`|Defines a table data cell|
|`<th>`|Defines a table header cell (bold + centered by default)|

 Example:

```html
<table border="1">
  <tr>
    <th>Name</th>
    <th>Age</th>
    <th>City</th>
  </tr>
  <tr>
    <td>Abhishek</td>
    <td>22</td>
    <td>Delhi</td>
  </tr>
  <tr>
    <td>Aditi</td>
    <td>24</td>
    <td>Mumbai</td>
  </tr>
</table>

```

---

### 🔹 Table Attributes

|Attribute|Description|Example|
|---|---|---|
|`border`|Adds border around table|`<table border="1">`|
|`cellpadding`|Space **inside** cell|`<table cellpadding="10">`|
|`cellspacing`|Space **between** cells|`<table cellspacing="5">`|
|`colspan`|Cell spans multiple columns|`<td colspan="2">`|
|`rowspan`|Cell spans multiple rows|`<td rowspan="2">`|

 Example with `colspan` and `rowspan`:

```html
<table border="1">
  <tr>
    <th rowspan="2">Name</th>
    <th colspan="2">Details</th>
  </tr>
  <tr>
    <th>Age</th>
    <th>City</th>
  </tr>
  <tr>
    <td>Ravi</td>
    <td>25</td>
    <td>Bangalore</td>
  </tr>
</table>

```

---

### 🔹 Table Sections

- `<thead>` → Header section
- `<tbody>` → Body section
- `<tfoot>` → Footer section

 Example:

```html
<table border="1">
  <thead>
    <tr>
      <th>Product</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Laptop</td>
      <td>$800</td>
    </tr>
    <tr>
      <td>Phone</td>
      <td>$500</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td>Total</td>
      <td>$1300</td>
    </tr>
  </tfoot>
</table>

```

---

### 🔹 Styling Tables with CSS

```css
table {
  width: 100%;
  border-collapse: collapse; /* removes double borders */
}
th, td {
  border: 1px solid black;
  padding: 8px;
  text-align: center;
}
th {
  background-color: lightgray;
}

```

---

### 8.  Text Formatting

HTML provides tags for text styling:

```html
<b>Bold</b>
<i>Italic</i>
<u>Underline</u>
<mark>Highlighted</mark>
<sup>Superscript</sup>
<sub>Subscript</sub>

```

---

##  HTML Iframes

### 🔹 What is an `<iframe>`?

- `<iframe>` = **Inline Frame**
- Allows you to **embed another webpage** inside your current webpage.
- Used for embedding **videos, maps, ads, docs, or other sites**.

 Basic Syntax:

```html
<iframe src="<https://www.example.com>"></iframe>

```

---

### 🔹 Important Attributes

|Attribute|Description|Example|
|---|---|---|
|`src`|URL of the page to display|`<iframe src="page.html"></iframe>`|
|`width` / `height`|Set size of iframe|`<iframe src="page.html" width="600" height="400"></iframe>`|
|`title`|Accessibility (screen readers)|`<iframe title="Google Map"></iframe>`|
|`name`|Name of the iframe (used as link target)|`<iframe name="myFrame"></iframe>`|
|`frameborder` (deprecated)|0 = no border, 1 = border (use CSS instead)|`<iframe frameborder="0">`|
|`loading="lazy"`|Improves performance (loads iframe only when visible)|`<iframe loading="lazy">`|
|`allowfullscreen`|Allows fullscreen mode (for videos/maps)|`<iframe allowfullscreen></iframe>`|
|`sandbox`|Restricts what iframe content can do (security)|`<iframe sandbox></iframe>`|

---

### 🔹 Example 1: Simple Iframe

```html
<iframe src="<https://www.wikipedia.org>"
        width="600"
        height="400"
        title="Wikipedia"></iframe>

```

---

### 🔹 Example 2: YouTube Video Embed

```html
<iframe width="560" height="315"
  src="<https://www.youtube.com/embed/dQw4w9WgXcQ>"
  title="YouTube video"
  frameborder="0"
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
  allowfullscreen>
</iframe>

```

---

### 🔹 Example 3: Google Maps Embed

```html
<iframesrc="<https://www.google.com/maps/embed?pb=>..."
  width="600"
  height="450"
  style="border:0;"
  allowfullscreen=""
  loading="lazy"
  referrerpolicy="no-referrer-when-downgrade">
</iframe>

```

---

### 🔹 Example 4: Targeting Links to Iframe

You can open a link **inside an iframe** using the `name` attribute.

```html
<a href="page1.html" target="myFrame">Load Page 1</a>
<a href="page2.html" target="myFrame">Load Page 2</a>

<iframe name="myFrame" width="600" height="400"></iframe>

```

---

### 🔹 Security with Iframes

- Iframes can be risky (clickjacking, malicious scripts).
- Use the **`sandbox` attribute** to restrict actions.

 Example:

```html
<iframe src="form.html" sandbox="allow-scripts allow-forms"></iframe>

```

This only allows **scripts and forms**, blocking other actions.

---

##  Semantic HTML

![61a950a4-b5eb-4a12-ac8e-8eb49dade034.png](attachment:b8ade033-b42e-4241-8ac4-c26f59ec3107:61a950a4-b5eb-4a12-ac8e-8eb49dade034.png)

### 🔹 What is Semantic HTML?

- **Semantic HTML** means using HTML tags that have **meaning** (they tell both the browser and developers what the content represents).
- Makes code **more readable, accessible, and SEO-friendly**.

Example:

```html
<!-- Non-Semantic -->
<div id="header"></div>

<!-- Semantic -->
<header></header>

```

---

### 🔹 Why Use Semantic HTML?

1. **Improves readability** → Easier for developers to understand.
2. **SEO benefits** → Search engines understand content structure.
3. **Accessibility** → Screen readers can interpret content better for visually impaired users.
4. **Standard structure** → Defines clear roles for sections of a webpage.

---

### 🔹 Common Semantic Tags

|Tag|Meaning / Usage|
|---|---|
|`<header>`|Represents introductory content (logo, navigation, title).|
|`<nav>`|Contains navigation links (menus, links, navbar).|
|`<main>`|The main content of the document (unique, used once).|
|`<section>`|Defines a thematic grouping of content (chapters, services, etc.).|
|`<article>`|Independent piece of content (blog post, news, forum post).|
|`<aside>`|Secondary content (sidebar, ads, related links).|
|`<footer>`|Footer of a page (copyright, contact info, links).|
|`<figure>`|Wraps images, charts, diagrams.|
|`<figcaption>`|Caption/description for `<figure>`.|
|`<mark>`|Highlights text (like a marker).|
|`<time>`|Represents date/time.|

---

### 🔹 Example of Semantic Layout

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Semantic HTML Example</title>
</head>
<body>

  <header>
    <h1>My Blog</h1>
    <nav>
      <a href="#home">Home</a>
      <a href="#articles">Articles</a>
      <a href="#contact">Contact</a>
    </nav>
  </header>

  <main>
    <article>
      <h2>Understanding Semantic HTML</h2>
      <p>Semantic tags give meaning to content and improve accessibility.</p>
    </article>

    <section>
      <h2>Why Use Semantic HTML?</h2>
      <p>It helps with SEO, accessibility, and code readability.</p>
    </section>

    <aside>
      <h3>Related Links</h3>
      <ul>
        <li><a href="#">HTML Basics</a></li>
        <li><a href="#">CSS Intro</a></li>
      </ul>
    </aside>
  </main>

  <footer>
    <p>&copy; 2025 My Blog | Contact: info@example.com</p>
  </footer>

</body>
</html>

```

---

 **Key Tip**:

Use semantic tags for structure, and use `<div>` or `<span>` only when **no semantic tag fits**.

---

##  HTML Quotations

HTML provides special tags for handling **quotations, citations, and references**.

---

### 🔹 1. Short Quotations – `<q>`

- Used for **inline (short) quotes**.
- Browsers usually add **quotation marks** automatically.

 Example:

```html
<p>She said, <q>HTML makes the web meaningful.</q></p>

```

Output → She said, “HTML makes the web meaningful.”

---

### 🔹 2. Block Quotations – `<blockquote>`

- Used for **longer quotations**, displayed as a **separate block**.
- Can include a `cite` attribute for source.

 Example:

```html
<blockquote cite="<https://www.w3.org/TR/html52/>">
  HTML is the standard markup language for creating Web pages.
</blockquote>

```

---

### 🔹 3. Citation – `<cite>`

- Used for **titles of works** (books, research papers, articles, etc.).
- Usually displayed in _italic_.

 Example:

```html
<p><cite>The Great Gatsby</cite> was written by F. Scott Fitzgerald.</p>

```

---

### 🔹 4. Abbreviations – `<abbr>`

- Used for **abbreviations or acronyms**.
- Provide full form in the `title` attribute (tooltip).

 Example:

```html
<p><abbr title="World Health Organization">WHO</abbr> was founded in 1948.</p>

```

---

### 🔹 5. Address – `<address>`

- Used for **contact information** (author, company, etc.).

 Example:

```html
<address>
  Written by Abhishek Singh.<br>
  Visit us at: www.example.com<br>
  Coimbatore, India
</address>

```

---

### 🔹 6. Bi-Directional Override – `<bdo>`

- Used to **change text direction** (useful for languages like Arabic/Hebrew).

 Example:

```html
<p><bdo dir="rtl">This text is written right-to-left.</bdo></p>

```

---

### 🔹 Quick Demo Page

```html
<!DOCTYPE html>
<html>
<head>
  <title>Quotations Example</title>
</head>
<body>

  <h2>Short Quote</h2>
  <p>Einstein said: <q>Imagination is more important than knowledge.</q></p>

  <h2>Block Quote</h2>
  <blockquote cite="<https://www.goodreads.com/quotes>">
    The only limit to our realization of tomorrow is our doubts of today.
  </blockquote>

  <h2>Citation</h2>
  <p><cite>Romeo and Juliet</cite> was written by William Shakespeare.</p>

  <h2>Abbreviation</h2>
  <p><abbr title="HyperText Markup Language">HTML</abbr> is the foundation of the web.</p>

  <h2>Address</h2>
  <address>
    Contact: abhishek@example.com<br>
    India
  </address>

  <h2>BDO Example</h2>
  <p><bdo dir="rtl">HTML is fun!</bdo></p>

</body>
</html>

```

---

##  Inline Elements vs Block Elements

### 🔹 1. Block-level Elements

- **Start on a new line** (take full width available).
- Always stack **vertically**.
- Can contain **inline or other block elements**.
- Default width = **100% of parent**.

 Examples of **Block Elements**:

```html
<div>, <p>, <h1> to <h6>, <section>, <article>, <header>, <footer>, <table>, <ul>, <ol>, <li>, <form>, <blockquote>

```

 Example:

```html
<p>This is a paragraph.</p>
<h2>This is a heading</h2>
<div>This is a division</div>

```

 Result → Each one starts on a **new line**.

---

### 🔹 2. Inline Elements

- **Do not start on a new line** (flow inside text).
- Only take up as much width as **content requires**.
- Can only contain **text or other inline elements** (not block).

 Examples of **Inline Elements**:

```html
<span>, <a>, <img>, <strong>, <em>, <b>, <i>, <u>, <label>, <input>, <button>

```

 Example:

```html
<p>This is <span style="color:red;">red text</span> inside a paragraph.</p>
<a href="#">Click Me</a>
<strong>Bold text</strong>

```

 Result → Elements stay **inline with text**.

---

### 🔹 3. Key Differences

|Feature|Block Elements|Inline Elements|
|---|---|---|
|Line behavior|Start on a **new line**|Stay **in the same line**|
|Width|Full width (100%)|Only content width|
|Height|Can be set normally|Depends on content (cannot set top/bottom margin easily)|
|Contains|Can contain block + inline|Can only contain inline or text|
|Examples|`<div>, <p>, <h1>, <section>`|`<span>, <a>, <img>, <b>, <i>`|

---

### 🔹 4. Example: Block vs Inline Together

```html
<div style="border:2px solid blue;">I am a Block element</div>
<p style="border:2px solid green;">I am also Block</p>

<span style="border:2px solid red;">I am Inline</span>
<a href="#" style="border:2px solid orange;">I am Inline too</a>

```

###  Result →

- Blue `div` & green `p` go **one below the other**.
- Red `span` & orange `a` stay **side by side**.

---

### 🔹 5. Special Case → `inline-block`

- Acts like **inline** (stays in same line).
- But allows you to **set width & height** like block.

 Example:

```html
<span style="display:inline-block; width:100px; height:50px; background:yellow;">
I am inline-block
</span>

```

##  HTML Forms (Special Emphasis)

Forms are the **heart of user interaction**. They allow users to **send data** (like login details, search queries, feedback, etc.).

### Basic Form Structure

```html
<form action="/submit" method="POST">
  <label for="username">Username:</label>
  <input type="text" id="username" name="username">

  <label for="password">Password:</label>
  <input type="password" id="password" name="password">

  <button type="submit">Login</button>
</form>

```

- `<form>` → Container for inputs.
- `action` → URL where data is sent.
- `method` → GET (visible in URL) or POST (hidden).

Analogy: A **form is like a courier service**. Inputs are the contents of the parcel, `method` decides how it’s sent, and `action` is the destination address.

---

### Input Types

```html
<form>
  <input type="text" placeholder="Enter text">
  <input type="password" placeholder="Password">
  <input type="email" placeholder="Email">
  <input type="number" placeholder="Age">
  <input type="date">
  <input type="color">
  <input type="file">
  <input type="checkbox"> I agree
  <input type="radio" name="gender"> Male
  <input type="radio" name="gender"> Female
  <input type="range" min="1" max="10">
  <input type="url" placeholder="<https://example.com>">
  <input type="tel" placeholder="Phone Number">
  <input type="hidden" value="secret">
  <input type="submit" value="Submit">
</form>

```

---

### Labels & Accessibility

```html
<label for="email">Email:</label>
<input type="email" id="email" name="email">

```

- `for` attribute connects label to input.
- Helps **screen readers** and improves accessibility.

---

### 10.4 Dropdowns & Textarea

```html
<select>
  <option>India</option>
  <option>USA</option>
  <option>UK</option>
</select>

<textarea rows="4" cols="30">Enter your message here...</textarea>

```

---

### Buttons

```html
<button type="button">Click Me</button>
<button type="reset">Reset</button>
<button type="submit">Submit</button>

```

---

### Fieldset & Legend

```html
<fieldset>
  <legend>Personal Info</legend>
  <label>Name:</label>
  <input type="text">
</fieldset>

```

- Groups related form elements.

---

### Form Validation

HTML provides basic **built-in validation**:

```html
<input type="email" required>
<input type="number" min="1" max="100">
<input type="text" pattern="[A-Za-z]+">

```

---

---

##  Entities

HTML entities are used for special characters:

- `&lt;` → <
- `&gt;` → >
- `&amp;` → &
- `&copy;` → ©

---

##  Responsive Layout Basics

With CSS, but HTML provides `<meta viewport>` to help:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">

```

---

##  URI Code in HTML

### 🔹 1. What is a URI?

- **URI** → **Uniform Resource Identifier**
- It identifies a resource on the internet (webpage, image, video, etc.).
- Two main types:
    - **URL** (Uniform Resource Locator) → Location of resource (e.g., `https://google.com`)
    - **URN** (Uniform Resource Name) → Name of resource (rarely used in HTML).

 In simple words → **URL is a type of URI**.

---

### 🔹 2. Usage of URI in HTML

- URIs are mostly used in **links**, **images**, **iframes**, **videos**, and **scripts**.

### Example:

```html
<a href="<https://www.example.com>">Visit Example</a>
<img src="<https://www.example.com/image.png>" alt="Example Image">
<link rel="stylesheet" href="style.css">
<script src="app.js"></script>

```

Here:

- `https://www.example.com` → Absolute URI
- `style.css` → Relative URI

---

### 🔹 3. Absolute vs Relative URI

1. **Absolute URI** → Complete path including protocol, domain, file.
    
    ```html
    <a href="<https://www.google.com/>">Google</a>
    
    ```
    
     Works from anywhere in the world.
    
2. **Relative URI** → Path relative to current file.
    
    ```html
    <a href="/about.html">About Us</a>
    
    ```
    
     Works only inside same website/project.
    

---

### 🔹 4. URI Encoding (Percent Encoding)

- Certain characters (like spaces, `#`, `?`, `&`) are **not allowed directly** in URIs.
- They are replaced with **% codes**.

 Common Examples:

- Space → `%20`
- `?` → `%3F`
- `&` → `%26`
- `#` → `%23`

### Example:

```html
<a href="<https://example.com/search?q=hello%20world>">Search</a>

```

 `%20` replaces space in `hello world`.

---

##  Best Practices

- Always use semantic HTML.
- Use `alt` for images.
- Keep forms accessible.
- Use proper indentation.
- Validate HTML using [W3C Validator](https://validator.w3.org/).