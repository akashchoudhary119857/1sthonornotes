We’ll use this basic HTML structure:

<div class="grid-container"> <div class="item">1</div> <div class="item">2</div> <div class="item">3</div> <div class="item">4</div> <div class="item">5</div> <div class="item">6</div> </div> 

​

Default CSS (styling only):

.grid-container { display: grid; border: 2px solid #333; margin: 20px; gap: 10px; /* space between items */ } .item { background: lightblue; border: 1px solid #333; padding: 20px; text-align: center; font-size: 18px; }

​

### 1. display: grid

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Turns an element into a grid container.

.grid-container { display: grid; }

​

![👉](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Children (

.item

) automatically become grid items.

### 2. grid-template-columns

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Defines how many columns and their sizes.

.grid-container { display: grid; grid-template-columns: 100px 100px 100px; /* 3 fixed columns */ }

​

![👉](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) You can use:

px

,

%

,

em

→ fixed sizes

fr

(fractional unit) → flexible space

Example:

grid-template-columns: 1fr 2fr 1fr;

​

![👉](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Middle column gets double the space.

### 3. grid-template-rows

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Defines the rows.

.grid-container { display: grid; grid-template-rows: 100px 200px; }

​

![👉](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) First row = 100px, second = 200px, more items spill into auto rows.

### 4. repeat() function

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Shorthand to avoid writing the same size repeatedly.

grid-template-columns: repeat(3, 1fr);

​

![👉](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Creates 3 equal columns.

### 5. auto-fit & auto-fill

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Makes responsive grids.

grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));

​

minmax(150px, 1fr)

→ each column min 150px, max flexible.

auto-fit

→ fits as many as possible.

![👉](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Perfect for responsive galleries.

### 6. gap

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Adds space between grid items.

.grid-container { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; /* both row + column */ }

​

![👉](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Can also use

row-gap

and

column-gap

.

### 7. grid-column & grid-row

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Controls where each item is placed.

.item:nth-child(1) { grid-column: 1 / 3; /* spans across column 1 and 2 */ } .item:nth-child(2) { grid-row: 1 / 3; /* spans down across 2 rows */ }

​

![👉](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Lets items stretch across multiple cells.

### 8. justify-items

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Aligns items horizontally inside their cells.

Values:

start

,

end

,

center

,

stretch

.grid-container { display: grid; grid-template-columns: repeat(3, 1fr); justify-items: center; }

​

![👉](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Items align inside their own grid space.

### 9. align-items

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Aligns items vertically inside their cells.

.grid-container { display: grid; grid-template-columns: repeat(3, 1fr); align-items: end; }

​

### 10. justify-content

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Aligns the whole grid horizontally inside container.

.grid-container { display: grid; grid-template-columns: 100px 100px; justify-content: center; }

​

![👉](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Useful when grid doesn’t take full width.

### 11. align-content

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Aligns the whole grid vertically inside container.

.grid-container { display: grid; grid-template-rows: 100px 100px; align-content: space-between; }

​

![👉](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Works when grid is shorter than container.

### 12. place-items (shorthand)

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Combines

align-items

+

justify-items

.

.grid-container { place-items: center; }

​

### 13. place-content (shorthand)

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Combines

align-content

+

justify-content

.

.grid-container { place-content: center; }

​

### 14. grid-area (naming)

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) You can name areas and place items into them.

.grid-container { grid-template-areas: "header header" "sidebar main" "footer footer"; grid-template-columns: 150px 1fr; grid-template-rows: auto 1fr auto; } .item:nth-child(1) { grid-area: header; } .item:nth-child(2) { grid-area: sidebar; } .item:nth-child(3) { grid-area: main; } .item:nth-child(4) { grid-area: footer; }

​

![👉](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Creates a full-page layout easily.

### 15. grid-auto-rows & grid-auto-columns

![📌](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) Defines size for rows/columns that are added automatically.

.grid-container { grid-template-columns: 100px 100px; grid-auto-rows: 80px; }

​

![👉](data:image/gif;base64,R0lGODlhAQABAIAAAP///wAAACH5BAEAAAAALAAAAAABAAEAAAICRAEAOw==) All new rows get 80px height.

## Real World Examples:

## 1) Calculator UI (Grid-based)

Goal: Build a compact calculator layout where the display spans the full width and buttons form a neat 4-column grid. This demonstrates

grid-template-columns

,

grid-row(s)

,

gap

, and how to span cells.

#### Why Grid?

A calculator is a natural grid: display row + uniform button rows. Grid makes it trivial to control columns, rows and allow some keys (like

0

or

=

) to span columns.

#### Step-by-step

Create a container and set

display: grid

.

Make 4 columns using

repeat(4, minmax(60px, 1fr))

— flexible & responsive.

Make rows with one tall display row and 5 equal button rows.

Put the display in

grid-column: 1 / -1

so it spans all columns.

Use

.span-2

to make

0

(and optionally

=

) span 2 columns.

Add nice visuals and accessibility attributes.

Small JS demo: handle click → update display → compute using

eval()

(only for demo, note security caveat).

#### Demo (calculator.html)

<!doctype html> <html lang="en"> <head> <meta charset="utf-8" /> <meta name="viewport" content="width=device-width,initial-scale=1" /> <title>Grid Calculator UI (Demo)</title> <style> :root{ --bg:#0f172a; --panel:#0b1220; --accent:#10b981; --muted:#94a3b8; --btn:#1f2937; --btn-op:#ef4444; --gap:10px; } body{ margin:0; min-height:100vh; display:flex; align-items:center; justify-content:center; background: linear-gradient(180deg,#071029,#0b1220); font-family:system-ui,Segoe UI,Roboto,"Helvetica Neue",Arial; color:#e6eef8; } .calculator{ width: min(480px, 96vw); background: linear-gradient(180deg,#07172a,#091827); padding:18px; border-radius:14px; box-shadow: 0 10px 30px rgba(2,6,23,.6); display: grid; grid-template-columns: repeat(4, minmax(60px, 1fr)); /* 4 columns */ grid-template-rows: minmax(72px, auto) repeat(5, 64px); /* 1 display row + 5 button rows */ gap: var(--gap); } /* Display */ .display{ grid-column: 1 / -1; /* full width */ background: linear-gradient(90deg,#0b1220,#07122a); border-radius:10px; padding: 12px 16px; display:flex; align-items:center; justify-content:flex-end; font-size: clamp(1.25rem, 3vw, 2rem); color: #e6eef8; box-shadow: inset 0 -6px 18px rgba(0,0,0,.6); overflow:hidden; word-break: break-all; } /* Buttons */ .btn{ border: none; outline: none; background: var(--btn); color: #e6eef8; font-size: 1.15rem; border-radius:10px; cursor: pointer; box-shadow: 0 4px 8px rgba(2,6,23,.45); transition: transform .08s ease, box-shadow .12s ease; display:flex; align-items:center; justify-content:center; } .btn:active{ transform: translateY(2px); box-shadow: 0 2px 6px rgba(2,6,23,.5); } .btn.op { background: linear-gradient(180deg,#ef4444,#dc2626); } .btn.equal { background: linear-gradient(180deg,#10b981,#059669); } /* Span two columns (e.g., 0) */ .span-2 { grid-column: span 2; } /* small visual tweaks for clarity */ .btn.clear { background: #334155; color: #f8fafc; font-weight:600; } </style> </head> <body> <div class="calculator" role="application" aria-label="Calculator"> <div id="display" class="display" aria-live="polite">0</div> <!-- Row 1 --> <button class="btn clear" data-value="C" aria-label="Clear (C)">C</button> <button class="btn" data-value="(" aria-label="Left Parenthesis">(</button> <button class="btn" data-value=")" aria-label="Right Parenthesis">)</button> <button class="btn op" data-value="/" aria-label="Divide">÷</button> <!-- Row 2 --> <button class="btn" data-value="7">7</button> <button class="btn" data-value="8">8</button> <button class="btn" data-value="9">9</button> <button class="btn op" data-value="*" aria-label="Multiply">×</button> <!-- Row 3 --> <button class="btn" data-value="4">4</button> <button class="btn" data-value="5">5</button> <button class="btn" data-value="6">6</button> <button class="btn op" data-value="-" aria-label="Minus">−</button> <!-- Row 4 --> <button class="btn" data-value="1">1</button> <button class="btn" data-value="2">2</button> <button class="btn" data-value="3">3</button> <button class="btn op" data-value="+" aria-label="Plus">+</button> <!-- Row 5 --> <button class="btn span-2" data-value="0">0</button> <button class="btn" data-value=".">.</button> <button class="btn equal" data-value="=" aria-label="Equals">=</button> </div> </body> </html>

​

## 2) Dashboard Layout (Grid Areas)

Goal: A realistic admin/dashboard layout: header, left sidebar, main content area, right widgets/panel, and footer. Show

grid-template-areas

, responsive reflow, nested grids for cards, and scrollable panels.

#### Why Grid?

Dashboards are a classic 2D layout (rows + columns). Grid areas let us name places and reorganize the layout easily for different screen sizes.

#### Step-by-step

Define a root

.dashboard

grid with 3 columns and 3 rows and a

grid-template-areas

map.

Assign each child element a

grid-area

.

Make the main content use a nested grid to layout cards (

auto-fit

+

minmax

).

Add responsive breakpoint: change to single column on small screens.

Ensure scrollable panels with

overflow:auto

and

min-height:0

to avoid flex/grid scrollbar issues.

#### Demo (dashboard.html)

<!doctype html> <html lang="en"> <head> <meta charset="utf-8"/> <meta name="viewport" content="width=device-width,initial-scale=1"/> <title>Grid Dashboard Layout</title> <style> :root{ --bg:#f3f4f6; --panel:#ffffff; --accent:#0ea5e9; --muted:#64748b; --gap:16px; } *{box-sizing:border-box} body{margin:0;font-family:system-ui,Segoe UI,Roboto,Arial,sans-serif;background:var(--bg);color:#0f172a} /* Outer grid */ .dashboard{ display:grid; grid-template-columns: 220px 1fr 320px; /* sidebar | main | right widgets */ grid-template-rows: 64px 1fr 56px; /* header | content | footer */ grid-template-areas: "header header header" "sidebar main right" "footer footer footer"; gap: var(--gap); padding: 18px; min-height: calc(100vh - 36px); } header { grid-area: header; background:var(--panel); padding:12px 18px; border-radius:10px; display:flex; align-items:center; justify-content:space-between; box-shadow:0 6px 18px rgba(2,6,23,.06) } nav { grid-area: sidebar; background:var(--panel); padding:14px; border-radius:10px; overflow:auto; min-height:0; } main { grid-area: main; background:var(--panel); padding:14px; border-radius:10px; overflow:auto; min-height:0; } aside { grid-area: right; background:var(--panel); padding:14px; border-radius:10px; overflow:auto; min-height:0; } footer { grid-area: footer; background:var(--panel); padding:12px 18px; border-radius:10px; display:flex; align-items:center; justify-content:center } /* Sidebar */ .nav-list { list-style:none; padding:0; margin:0; display:flex; flex-direction:column; gap:8px } .nav-list a { display:block; padding:8px 10px; border-radius:8px; color:var(--muted); text-decoration:none } .nav-list a.active { background:linear-gradient(90deg,#e0f2fe,#bae6fd); color:#0369a1; font-weight:600 } /* Header */ .brand { font-weight:700; font-size:1.05rem } .search { display:flex; gap:8px; align-items:center; } /* Main content nested grid for cards */ .cards { display:grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); /* responsive cards */ gap: 14px; } .card { background: linear-gradient(180deg,#ffffff,#fbfdff); padding:12px; border-radius:10px; box-shadow: 0 6px 18px rgba(13,38,63,.05); } .card h3 { margin:0 0 8px; font-size:1rem } /* Right column widgets */ .widget { margin-bottom:12px; padding:10px; border-radius:8px; background: linear-gradient(180deg,#fff,#fbfcff); box-shadow: 0 6px 18px rgba(5,20,40,.04) } /* Responsive: stack to single column on narrow screens */ @media (max-width: 900px){ .dashboard { grid-template-columns: 1fr; grid-template-areas: "header" "main" "sidebar" "right" "footer"; } .dashboard { padding:12px; } } /* small helpers */ .muted { color:var(--muted); font-size:.95rem } .top-row { display:flex; gap:12px; align-items:center } </style> </head> <body> <div class="dashboard"> <header> <div class="top-row"> <div class="brand">Acme Analytics</div> <div class="muted">• Admin Dashboard</div> </div> <div class="search"> <input type="search" placeholder="Search..." aria-label="Search" style="padding:8px;border-radius:8px;border:1px solid #e6eef8"> <button style="padding:8px 10px;border-radius:8px;border:none;background:var(--accent);color:#fff">Search</button> </div> </header> <nav> <ul class="nav-list"> <li><a href="#" class="active">Overview</a></li> <li><a href="#">Orders</a></li> <li><a href="#">Products</a></li> <li><a href="#">Customers</a></li> <li><a href="#">Reports</a></li> <li><a href="#">Settings</a></li> </ul> </nav> <main> <section class="cards" aria-label="Key metrics"> <div class="card"><h3>Revenue</h3><p class="muted">₹ 120,000</p></div> <div class="card"><h3>Orders</h3><p class="muted">1,430</p></div> <div class="card"><h3>Active Users</h3><p class="muted">3,200</p></div> <div class="card"><h3>Conversion</h3><p class="muted">2.4%</p></div> <div class="card"><h3>New Clients</h3><p class="muted">43</p></div> <div class="card"><h3>Pending</h3><p class="muted">7</p></div> </section> <section style="margin-top:14px"> <div class="card"><h3>Recent Orders</h3><p class="muted">Order table or list would go here (scrollable)</p></div> </section> </main> <aside> <div class="widget"><strong>Server Status</strong><p class="muted">All systems operational</p></div> <div class="widget"><strong>Notifications</strong><p class="muted">3 unread</p></div> <div class="widget"><strong>Quick Links</strong><p class="muted">Shortcuts</p></div> </aside> <footer> <div class="muted">© 2025 Acme • Built with CSS Grid</div> </footer> </div> </body> </html>

​

## 3) Responsive Photo Gallery (auto-fit / minmax + spans)

Goal: A responsive image gallery (grid) that fills available width and adapts to screen size using

auto-fit

/

minmax

. We'll also show how to make some images span more than one column for visual variety.

#### Why Grid?

Grids are perfect for galleries: responsive columns, consistent gaps, and easy column/row spans for featured images.

#### Step-by-step

Set container to

display:grid

.

Use

grid-template-columns: repeat(auto-fit, minmax(180px, 1fr))

— this creates as many columns as fit with a minimum width.

Use

gap

for spacing.

For featured tiles, add

.span-2

or

.span-3

to control

grid-column: span 2

or

grid-row: span 2

.

Use

object-fit: cover

to let images fill cells elegantly.

#### Copy-paste demo (gallery.html)

<!doctype html> <html lang="en"> <head> <meta charset="utf-8"/> <meta name="viewport" content="width=device-width,initial-scale=1"/> <title>Responsive Gallery (CSS Grid)</title> <style> :root{ --gap:12px; --bg:#f8fafc } *{box-sizing:border-box} body{margin:0;background:var(--bg);font-family:system-ui,Arial,sans-serif;padding:18px} h1{margin:0 0 12px} .gallery { display:grid; grid-template-columns: repeat(auto-fit, minmax(180px, 1fr)); /* responsive columns */ gap: var(--gap); align-items: stretch; } .tile { position:relative; overflow:hidden; border-radius:10px; background:linear-gradient(180deg,#fff,#f3f4f6); min-height:140px; display:block; } .tile img { width:100%; height:100%; display:block; object-fit:cover; /* cover ensures image fills tile without distortion */ } /* span classes to create visual variety */ .span-2 { grid-column: span 2; } .span-2-rows { grid-row: span 2; } /* caption overlay */ .caption { position:absolute; left:12px; right:12px; bottom:12px; padding:8px 10px; background:linear-gradient(180deg, rgba(0,0,0,.0), rgba(0,0,0,.45)); color:white; border-radius:8px; font-size:.95rem; } /* Make sure spans don't break on small screens */ @media (max-width:540px){ .span-2, .span-2-rows { grid-column: span 1; grid-row: span 1; } } </style> </head> <body> <h1>Responsive Photo Gallery</h1> <p style="color:#64748b;margin-top:4px">Resize the browser to see columns adapt using <code>auto-fit</code> + <code>minmax()</code>.</p> <div class="gallery" aria-label="Photo gallery"> <a class="tile span-2" href="#"> <img src="https://images.unsplash.com/photo-1558981403-cd1f0d3b3d?auto=format&fit=crop&w=1200&q=60" alt="Mountains"> <div class="caption">Featured — Mountains</div> </a> <a class="tile" href="#"><img src="https://images.unsplash.com/photo-1507525428034-b723cf961d3e?auto=format&fit=crop&w=800&q=60" alt="Beach"><div class="caption">Beach</div></a> <a class="tile" href="#"><img src="https://images.unsplash.com/photo-1499951360447-b19be8fe80f5?auto=format&fit=crop&w=800&q=60" alt="City"><div class="caption">City</div></a> <a class="tile span-2-rows" href="#"><img src="https://images.unsplash.com/photo-1501785888041-af3ef285b470?auto=format&fit=crop&w=1200&q=60" alt="Forest"><div class="caption">Tall — Forest</div></a> <a class="tile" href="#"><img src="https://images.unsplash.com/photo-1519681393784-d120267933ba?auto=format&fit=crop&w=800&q=60" alt="Desert"><div class="caption">Desert</div></a> <a class="tile" href="#"><img src="https://images.unsplash.com/photo-1439396087961-98bc12c21176?auto=format&fit=crop&w=800&q=60" alt="Bridge"><div class="caption">Bridge</div></a> <a class="tile" href="#"><img src="https://images.unsplash.com/photo-1500530855697-b586d89ba3ee?auto=format&fit=crop&w=800&q=60" alt="Lake"><div class="caption">Lake</div></a> </div> </body> </html>