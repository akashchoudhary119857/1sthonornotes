# CSS Media Queries : Responsive Web Design

## 1. What is a Media Query?

A CSS Media Query is a technique used to apply different CSS styles depending on the device's screen size, orientation, or other characteristics.

It helps us make a website look good on mobile phones, tablets, laptops, and desktops without creating a separate website for every device.

Example: A heading may appear in `36px` on a laptop but reduce to `24px` on a mobile phone.

[The Tallow Chandlers’ Company](https://images.openai.com/static-rsc-4/Xdoxux_KQJiPcIDQA0O-MzL5RMo-wBlsTJ3pchxzVw6DbRJn5O1yjnVdnI7HOSMFuJgBEY2vvtx1mPX38HylAN6u8JcZ_hTtEYnLCR4a1RQA20INjlhElUd-55lxyVYVOT3WTcmvCqX7NlATrBw1us6WZpX_YyfuEoqXG6KivXI?purpose=inline)

Mobile

Single column

[National Travel Bendigo Web Design | Creative Revoltion](https://images.openai.com/static-rsc-4/-OwRKmPqPXhuvHE2LkIuX5KJIczDx5vXily5U112tRawU9wgND-UDos-pOT7B-tJowNo6w1h5tjo4PdI5691sGI-4Z1Swcyvhk1PmHTr7n1CxrKBdLHFf1NA612nRtKPi9glFX7Oce1X_q86GXV8w8oIzhnzv4YzLmJS0ck4v7s?purpose=inline)

Tablet

Flexible layout

[VMX Digital | Tecnología que transforma procesos](https://images.openai.com/static-rsc-4/Lhk-oJhUHVB3dTWSs4uqW7gt4Ianjian41sGEtMc5yCDCz8i0Rc_AY83XuxoOagjfalKKMtMnmin2K3WqBDr6e1B3eRGx0r4dpd9DpYOAA1Ye76N1vocw6kgzOsOQ4PAQIuT-K_DvgUSRi-Ksr3h63u3msgTw467vN7CW7t0veE?purpose=inline)

Desktop

More columns

## 2. Why are Media Queries necessary?

Imagine designing a website on a laptop with a width of `1440px`. The same website opens on a phone with a width of approximately `390px`.

Without responsive styling, the layout might have:

- Text that is too large or difficult to read.
    
- Cards that are squeezed together or overflow the screen.
    
- Navigation links that do not fit in one row.
    
- Images that exceed their containers.
    
- Unnecessary horizontal scrolling.
    

Media queries allow us to change the design according to the available screen space.

### Real-world use cases

|Situation|What a media query can do|
|---|---|
|Mobile navigation|Hide desktop links or display a mobile menu|
|Product cards|Change four columns into one or two|
|Headings|Reduce font size on smaller screens|
|Sidebar|Move it below the main content|
|Images|Adjust spacing and layout around images|
|Landscape/portrait|Apply different styles based on orientation|
|Printing|Hide navigation and style content for printed pages|

## 3. How does a media query work?

A media query checks whether a specified condition is true. If it is true, the CSS inside the query is applied.

Browser checks screen width

Is the viewport width 600px or less?

Yes

Apply mobile CSS

No

Use other matching styles

### Basic syntax

```
@media (max-width: 600px) {
  /* CSS rules for viewport widths of 600px or less */
}
```

Explanation:

- `@media` — starts a media query.
    
- `max-width: 600px` — the condition is true when the viewport width is at most `600px`.
    
- `{ ... }` — contains the styles applied when the condition matches.
    

Important: A media query normally goes inside the CSS stylesheet, not directly inside an HTML element. HTML provides the content; CSS controls its appearance.

## 4. How to implement Media Queries with HTML and CSS

A media query works with HTML and CSS. HTML defines the elements, and CSS changes their layout or styling when the screen meets a condition.

### Step 1: Create an HTML file

Always include the viewport meta tag inside the `<head>` section.

```
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

Why is this necessary?

- `width=device-width` makes the viewport width correspond to the device's CSS-pixel width.
    
- `initial-scale=1.0` sets the initial zoom level to 100%.
    

Without the viewport meta tag, mobile browsers may use a wider virtual layout viewport, making responsive breakpoints behave unexpectedly.

### Step 2: Write normal CSS

These styles are applied by default.

```
h1 {
  font-size: 36px;
  color: royalblue;
}
```

### Step 3: Add a media query

```
@media (max-width: 600px) {
  h1 {
    font-size: 24px;
    color: crimson;
  }
}
```

Result:

- On a viewport wider than `600px`, the heading is normally `36px` and royal blue.
    
- At `600px` or less, the heading becomes `24px` and crimson.
    

## 5. Important media query conditions

|Condition|Meaning|
|---|---|
|`max-width: 600px`|Viewport width is 600px or less|
|`min-width: 768px`|Viewport width is 768px or more|
|`orientation: portrait`|Viewport height is greater than or equal to its width|
|`orientation: landscape`|Viewport width is greater than its height|
|`hover: hover`|Primary input mechanism can hover|
|`prefers-color-scheme: dark`|User prefers a dark color scheme|

### Common breakpoint examples

Breakpoints are widths at which the layout changes. They are not fixed rules for specific devices; choose them based on when your content needs a change.

```
/* Small screens */
@media (max-width: 600px) { }

/* Tablets and wider */
@media (min-width: 768px) { }

/* Large screens */
@media (min-width: 1024px) { }
```

There is no single universal breakpoint standard. Test your design at different widths and select breakpoints where the layout starts to look cramped or unbalanced.

## 6. Four simple examples for beginners

### Example 1: Change heading size on mobile

```
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    h1 {
      font-size: 40px;
    }

    @media (max-width: 600px) {
      h1 {
        font-size: 24px;
      }
    }
  </style>
</head>
<body>
  <h1>Learn CSS Media Queries</h1>
</body>
</html>
```

Concept: Change the font size when the viewport becomes smaller.

### Example 2: Change background color on mobile

```
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      background-color: lightblue;
    }

    @media (max-width: 600px) {
      body {
        background-color: lightyellow;
      }
    }
  </style>
</head>
<body>
  <h1>Responsive Background</h1>
  <p>Resize the browser to see the change.</p>
</body>
</html>
```

Concept: Apply different styles based on screen width.

### Example 3: Hide an element on small screens

```
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    .message {
      background: lightgreen;
      padding: 20px;
    }

    @media (max-width: 600px) {
      .message {
        display: none;
      }
    }
  </style>
</head>
<body>
  <h1>My Website</h1>
  <div class="message">Welcome to the desktop version!</div>
  <p>This paragraph remains visible.</p>
</body>
</html>
```

Concept: Hide content that is not necessary on smaller screens. Note that `display: none` removes the element from the layout, but does not delete it from the HTML.

### Example 4: Change navigation direction

```
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    nav {
      display: flex;
      gap: 20px;
      padding: 15px;
      background: #ddd;
    }

    @media (max-width: 600px) {
      nav {
        flex-direction: column;
        gap: 8px;
      }
    }
  </style>
</head>
<body>
  <nav>
    <a href="#">Home</a>
    <a href="#">About</a>
    <a href="#">Courses</a>
    <a href="#">Contact</a>
  </nav>
</body>
</html>
```

Concept: Display navigation links in a row on wider screens and a column on smaller screens.

Notice that this example uses Flexbox and a media query together. Flexbox controls the arrangement; the media query decides when to change that arrangement.

## 7. Medium-level example: Responsive card layout

Problem: Display three course cards in one row on desktop, two columns on tablets, and one column on mobile.

```

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Responsive Course Cards</title>

  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      padding: 20px;
      font-family: Arial, sans-serif;
      background: #f4f6f8;
    }

    h1 {
      text-align: center;
    }

    .courses {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 20px;
      max-width: 1000px;
      margin: 30px auto;
    }

    .card {
      padding: 25px;
      background: white;
      border-radius: 10px;
      box-shadow: 0 2px 8px #0002;
    }

    .card h2 {
      color: royalblue;
    }

    /* Tablet */
    @media (max-width: 800px) {
      .courses {
        grid-template-columns: repeat(2, 1fr);
      }
    }

    /* Mobile */
    @media (max-width: 500px) {
      .courses {
        grid-template-columns: 1fr;
      }

      body {
        padding: 12px;
      }

      h1 {
        font-size: 25px;
      }
    }
  </style>
</head>
<body>
  <h1>Our Courses</h1>

  <main class="courses">
    <article class="card">
      <h2>HTML & CSS</h2>
      <p>Learn website structure and styling.</p>
    </article>

    <article class="card">
      <h2>JavaScript</h2>
      <p>Learn programming for interactive websites.</p>
    </article>

    <article class="card">
      <h2>React</h2>
      <p>Learn to build reusable UI components.</p>
    </article>
  </main>
</body>
</html>
```

### How the layout changes

Desktop

Above 800px

HTML

JS

React

Tablet

501px–800px

HTML

JS

React

Mobile

500px or less

HTML

JS

React

The grid provides the columns. The media queries change the number of columns at specific viewport widths.

## 8. Hard-level example: Responsive dashboard

Problem: Create a dashboard with a sidebar, a header, and four information cards. On desktop, the sidebar stays beside the content. On mobile, the sidebar becomes a horizontal navigation row, the cards become one column, and the header stacks vertically.

```

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Responsive Dashboard</title>

  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: Arial, sans-serif;
      color: #222;
    }

    .dashboard {
      display: grid;
      grid-template-columns: 220px minmax(0, 1fr);
      min-height: 100vh;
    }

    .sidebar {
      background: #18243a;
      color: white;
      padding: 24px 16px;
    }

    .sidebar nav {
      display: flex;
      flex-direction: column;
      gap: 12px;
    }

    .sidebar a {
      color: white;
      text-decoration: none;
      padding: 10px;
      border-radius: 5px;
    }

    .sidebar a:hover {
      background: #34445f;
    }

    .content {
      min-width: 0;
      padding: 24px;
      background: #f4f6fa;
    }

    .header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 16px;
      margin-bottom: 24px;
    }

    .header h1 {
      margin: 0;
    }

    .cards {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 20px;
    }

    .card {
      min-width: 0;
      padding: 24px;
      background: white;
      border-radius: 12px;
      overflow-wrap: anywhere;
      box-shadow: 0 2px 8px #0001;
    }

    .card p {
      line-height: 1.6;
    }

    /* Medium screens */
    @media (max-width: 900px) {
      .dashboard {
        grid-template-columns: 170px minmax(0, 1fr);
      }

      .content {
        padding: 18px;
      }

      .cards {
        gap: 12px;
      }
    }

    /* Small screens */
    @media (max-width: 600px) {
      .dashboard {
        grid-template-columns: 1fr;
      }

      .sidebar {
        padding: 12px;
      }

      .sidebar nav {
        flex-direction: row;
        flex-wrap: wrap;
      }

      .content {
        padding: 14px;
      }

      .header {
        align-items: flex-start;
        flex-direction: column;
      }

      .cards {
        grid-template-columns: 1fr;
      }

      .card {
        padding: 18px;
      }
    }
  </style>
</head>
<body>
  <div class="dashboard">

    <aside class="sidebar">
      <h2>My Dashboard</h2>
      <nav>
        <a href="#">Overview</a>
        <a href="#">Students</a>
        <a href="#">Courses</a>
        <a href="#">Reports</a>
      </nav>
    </aside>

    <main class="content">
      <header class="header">
        <h1>Dashboard Overview</h1>
        <p>Welcome, Instructor!</p>
      </header>

      <section class="cards">
        <article class="card">
          <h2>Students</h2>
          <p>Total registered students: 250</p>
        </article>

        <article class="card">
          <h2>Courses</h2>
          <p>Active courses: 12</p>
        </article>

        <article class="card">
          <h2>Assignments</h2>
          <p>Pending submissions: 35</p>
        </article>

        <article class="card">
          <h2>Attendance</h2>
          <p>Overall attendance: 89%</p>
        </article>
      </section>
    </main>

  </div>
</body>
</html>
```

### Why this is a harder example

- It uses CSS Grid for the overall dashboard structure.
    
- It uses Flexbox for the header and sidebar navigation.
    
- It uses multiple breakpoints to adapt to different widths.
    
- `minmax(0, 1fr)` helps prevent grid columns from overflowing due to their contents.
    
- `flex-wrap: wrap` lets navigation links move onto another line if necessary.
    
- The layout changes its structure instead of merely shrinking the text.
    

Try resizing the browser to `1200px`, `800px`, and `390px` to observe the differences.

## 9. Media Queries vs Flexbox vs Grid

This is one of the most important concepts for students to understand.

Media queries, Flexbox, and Grid are not competitors. They solve different problems and are often used together.

|Feature|Media Queries|Flexbox|CSS Grid|
|---|---|---|---|
|Main purpose|Apply styles when a condition matches|Arrange items in one dimension|Arrange items in rows and columns|
|Works based on|Viewport/device conditions or media features|Available space and item properties|Available space and grid definitions|
|Changes layout at breakpoints|Yes|Not by itself, unless combined with responsive rules|Not by itself, unless combined with responsive rules|
|Best use case|Different styles for mobile and desktop|Navigation bars, buttons, aligned items|Dashboards, galleries, card layouts|
|Can work together?|Yes|Yes|Yes|

### Understand with a simple example

Flexbox alone:

```
.container {
  display: flex;
  gap: 10px;
}
```

This arranges items in a row by default. But the row may become cramped on a small screen.

Flexbox with a media query:

```
.container {
  display: flex;
  gap: 10px;
}

@media (max-width: 600px) {
  .container {
    flex-direction: column;
  }
}
```

Now the container switches to a column when the viewport width is 600px or less.

Grid with a media query:

```
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
}

@media (max-width: 600px) {
  .container {
    grid-template-columns: 1fr;
  }
}
```

Now the grid changes from three columns to one column.

Teaching takeaway: Flexbox and Grid control how items are arranged. Media queries control when particular CSS rules should apply.

### Do we always need media queries?

No. Some layouts can adapt naturally without them.

For example, this Grid layout automatically fits as many columns as the available width permits:

```
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 16px;
}
```

This is useful when you want cards to wrap naturally without specifying exact breakpoints. You can still add media queries when you need more specific changes, such as changing font sizes, hiding elements, or rearranging the navigation.

## 10. Advantages of Media Queries

1. Responsive design: One website adapts to different screen sizes.
    
2. Improved readability: Text and spacing can be adjusted for smaller screens.
    
3. Better user experience: Content remains usable on phones, tablets, and desktops.
    
4. Flexible layouts: Elements can change position, direction, size, or visibility.
    
5. Maintainability: Responsive rules can be managed within the same stylesheet.
    
6. Device and accessibility preferences: Styles can respond to orientation, color-scheme preferences, and other supported media features.
    
7. Reduced unnecessary scrolling: Responsive layouts can help prevent content from extending beyond the viewport.
    

## 11. Common mistakes students should avoid

### Mistake 1: Forgetting the viewport meta tag

```
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

Include it in the HTML `<head>` section.

### Mistake 2: Using `min-width` when `max-width` is intended

```
@media (max-width: 600px) {
  /* Applies at 600px and below */
}
```

```
@media (min-width: 600px) {
  /* Applies at 600px and above */
}
```

Remember the difference between `min` and `max`.

### Mistake 3: Forgetting the `@media` syntax

Incorrect:

```
media (max-width: 600px) {
  h1 { font-size: 20px; }
}
```

Correct:

```
@media (max-width: 600px) {
  h1 { font-size: 20px; }
}
```

### Mistake 4: Choosing breakpoints based only on device names

Do not assume that every tablet has the same width or every phone uses the same viewport. Select breakpoints based on how your content behaves.

### Mistake 5: Writing conflicting CSS rules

```
h1 {
  font-size: 36px;
}

@media (max-width: 600px) {
  h1 {
    font-size: 24px;
  }
}
```

This works because the media query matches on small screens and its rule appears later with the same selector specificity. Other CSS rules, specificity, and source order can affect which declaration wins.

## 12. Best practices

- Start with a mobile-first design when it suits the project.
    
- Use flexible widths, percentages, `rem`, `minmax()`, Flexbox, and Grid where appropriate.
    
- Add media queries only where the content needs a change.
    
- Test on real devices or browser developer tools.
    
- Avoid excessive breakpoints that make the stylesheet difficult to maintain.
    
- Check for horizontal overflow and ensure text remains readable.
    
- Use semantic HTML elements and keep content accessible.
    

### Mobile-first approach

In mobile-first design, write the base styles for smaller screens first, then add styles for wider screens.

```
/* Base styles: mobile */
.container {
  display: grid;
  grid-template-columns: 1fr;
}

/* Wider screens */
@media (min-width: 768px) {
  .container {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* Large screens */
@media (min-width: 1024px) {
  .container {
    grid-template-columns: repeat(3, 1fr);
  }
}
```

This is the reverse of starting with a desktop layout and overriding it for mobile. Both approaches are valid, but mobile-first often makes it easier to build a simple layout and enhance it for larger screens.

## 13. Quick revision questions

1. What is the main purpose of a CSS media query?

To create HTML elements

To apply CSS based on conditions

To execute JavaScript

To store website data

2. What does max-width: 600px mean?

Only screens wider than 600px

Screens exactly 600px wide

Viewports 600px wide or less

The page must be 600px tall

3. Which HTML tag helps the page use the device's viewport width correctly?

meta viewport

media

responsive

screen

4. Which technology arranges elements in a one-dimensional layout?

Media Queries

Flexbox

HTML

JavaScript

5. Can Grid and media queries be used together?

No

Only on desktops

Yes

Only with JavaScript



## Final summary

- Media queries apply styles when screen or other media conditions match.
    
- Flexbox arranges items along a primary axis.
    
- Grid arranges items in rows and columns.
    
- Responsive design often combines all three.
    
- Breakpoints should be selected according to the content, not only the device type.
    
- The viewport meta tag helps ensure responsive layouts behave as intended on mobile browsers.
    

The most important concept for students to remember is that a media query does not create a responsive layout on its own. It allows CSS rules to change when a 



 2 10 13 26 28 30 31 41 45 50 
@media (max-width:600px){

.parent{
 flex-direction:column;
 align-item: center
}
.box{
width:90%
}

}