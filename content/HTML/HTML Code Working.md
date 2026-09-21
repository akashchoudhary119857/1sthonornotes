---
tags:
  - web-dev/architecture
  - javascript/v8
  - performance/rendering
  - computer-science/networking
type: study-notes
---

# Web Architecture, Rendering Engines & JS Runtime Internals

---

## 1. Network Request to Screen Pixels (Behind the Scenes)

### 1.1 What Happens When You Type a URL & Press Enter?

When a user types a web address (e.g., `https://www.example.com/index.html`) into the browser's address bar (Omnibox) and hits **Enter**, a multi-step networking and client pipeline executes:


````

```mermaid
graph TD
    A[1. URL Parsing] --> B[2. DNS Lookup]
    B --> C[3. TCP / TLS Handshake]
    C --> D[4. HTTP Request / Response]
    D --> E[5. Engine Hand-off]
````

- **Step 1: URL Parsing**: The browser checks if the input is a valid URL or a search query. If it is a search term, it routes the request to the default search engine.
    
- **Step 2: DNS Lookup**: Resolves the domain name into an IP address (e.g., `93.184.216.34`). Checks in order:
    
    - Browser Cache
        
    - OS Cache
        
    - Router Cache
        
    - ISP DNS Resolver
        
    - Authoritative DNS Servers
        
- **Step 3: TCP / TLS Handshake**: Establishes a socket connection via a **TCP 3-Way Handshake** (`SYN` -> `SYN-ACK` -> `ACK`). For HTTPS, it performs a **TLS Handshake** to exchange encryption keys and validate certificates.
    
- **Step 4: HTTP Request / Response**: Sends an HTTP `GET` request. The server responds with headers (`HTTP/1.1 200 OK`) and streams back the raw HTML byte payload.
    
- **Step 5: Engine Hand-off**: The networking layer passes the raw HTML byte stream to the browser's **Rendering Engine**.
    

### 1.2 The Critical Rendering Path (CRP)

The **Critical Rendering Path** is the sequence of steps the browser performs to convert raw HTML, CSS, and JavaScript bytes into visible screen pixels.

Code snippet

```
graph TD
    HTML[1. HTML Bytes] --> DOM[DOM Tree Construction]
    CSS[2. CSS Bytes] --> CSSOM[CSSOM Tree Construction]
    DOM --> RenderTree[3. Render Tree Construction]
    CSSOM --> RenderTree
    RenderTree --> Layout[4. Layout / Reflow]
    Layout --> Paint[5. Paint / Repaint]
    Paint --> Composite[6. Compositing & GPU Display]
```

#### Detailed CRP Pipeline Stages

1. **DOM (Document Object Model) Tree Construction**:
    
    - HTML bytes are decoded into characters -> tokens ($\langle\text{html}\rangle, \langle\text{body}\rangle$) -> node objects -> **DOM Tree**.
        
    - Incremental process: Parsing starts as soon as raw chunks arrive over the network.
        
2. **CSSOM (CSS Object Model) Tree Construction**:
    
    - Encountering `<link rel="stylesheet">` or `<style>` tags triggers CSS parsing into the **CSSOM Tree**.
        
    - CSS is **render-blocking**: Rendering cannot begin without style rules to prevent a Flash of Unstyled Content (FOUC).
        
3. **Render Tree Construction**:
    
    - Combines DOM and CSSOM into a tree of visible nodes.
        
    - Elements with `display: none` and non-visual nodes (`<head>`, `<script>`) are excluded. (`visibility: hidden` elements ARE included).
        
4. **Layout (Reflow)**:
    
    - Calculates the exact screen position and box model size ($X, Y, \text{Width}, \text{Height}$) for each Render Tree node.
        
5. **Paint (Repaint)**:
    
    - Fills in visual details: backgrounds, text colors, borders, shadows, and images (rasterization).
        
6. **Compositing**:
    
    - Calculates separate layer hierarchies (`z-index`, CSS transforms) and sends layer textures to the GPU to composite on screen.
        

> [!ABSTRACT] Key Distinction: Reflow vs. Repaint
> 
> - **Reflow (Layout)** happens whenever geometric dimensions change (e.g., modifying `width`, `margin`, or adding DOM nodes). High CPU cost.
>     
> - **Repaint** happens when visual appearance changes without geometric layout changes (e.g., changing `color` or `background-color`). Lower CPU cost.
>     

## 2. Browser Rendering Engines & The Chromium Shift

### 2.1 Major Browser Rendering Engines

|**Engine**|**Primary Maintainer**|**Powered Browsers**|**Status**|
|---|---|---|---|
|**Blink**|Google, Microsoft, Opera|Chrome, MS Edge, Brave, Opera, Vivaldi|Active / Dominant|
|**Gecko**|Mozilla Foundation|Firefox, Firefox Focus, Waterfox|Active|
|**WebKit**|Apple Inc.|Safari (macOS, iOS, iPadOS)|Active|
|**EdgeHTML**|Microsoft|Legacy Edge (2015–2019)|Deprecated|
|**Trident**|Microsoft|Internet Explorer (1995–2020)|Retired / EOL|

### 2.2 Why Microsoft Retired Internet Explorer & EdgeHTML for Chromium

In December 2018, Microsoft abandoned its proprietary **EdgeHTML** engine and rebuilt Microsoft Edge on top of Google's open-source **Chromium** project (Blink + V8).

> [!INFO] Core Reasons for the Chromium Shift
> 
> - **Web Compatibility**: Web developers optimized sites primarily for Chromium due to Chrome's 65%+ market dominance. Legacy IE (Trident) and Edge (EdgeHTML) frequently rendered sites incorrectly.
>     
> - **Engineering Overhead**: Maintaining a modern browser engine requires massive engineering resources. Joining open-source Chromium eliminated redundant work on core engine standards.
>     
> - **Developer Ecosystem**: Developers disliked maintaining polyfills, CSS hacks (`-ms-`), and browser-specific fixes for IE/Edge. Standardizing on Chromium ensured predictable cross-browser behavior.
>     
> - **Multi-Platform Deployment**: EdgeHTML was bound to Windows 10 OS binaries. Chromium allowed Microsoft to deploy Edge across macOS, Linux, iOS, Android, and older Windows versions.
>     

### 2.3 How C/C++ Executables Read HTML, CSS & JavaScript

> [!QUESTION] How do low-level compiled languages (C/C++) execute high-level web code? Browsers do **NOT** convert HTML files into C++ source files. Instead, C++ executables contain **Parsers, Lexers, AST Generators, and Compilers** designed to process raw text files as data to build C++ objects in memory.

- **Parsing HTML into C++ Memory Objects**: When a C++ HTML parser encounters `<div id="box">`, it executes object allocation logic in system RAM:
    
    C++
    
    ```
    // Conceptual C++ DOM Creation
    class HTMLElement {
    public:
        std::string tag_name;
        std::unordered_map<std::string, std::string> attributes;
        std::vector<HTMLElement*> children;
    };
    
    HTMLElement* node = new HTMLElement();
    node->tag_name = "div";
    node->attributes["id"] = "box";
    ```
    
- **Translating Styles into C++ Graphics Commands**: The CSS parser converts style strings into C++ data structures. These are passed to native graphics libraries (**Skia, DirectX, OpenGL, Metal**) which send assembly instructions to the GPU.
    
- **Executing JS via C++ Engines (V8)**: The V8 engine (written in C++) parses JS text into an Abstract Syntax Tree (AST), translates it into Bytecode, and uses a **Just-In-Time (JIT) Compiler** to output native machine code ($0$s and $1$s) directly to the CPU.
    

## 3. Deep Dive into V8 Engine & Asynchronous Architecture

### 3.1 V8 Engine Architecture

JavaScript is a **single-threaded** language operating on a single Main Thread with one Call Stack and one Memory Heap.

- **Memory Heap**: Unstructured memory region where objects, variables, and closures are dynamically allocated in RAM.
    
- **Call Stack (LIFO)**: Last-In, First-Out data structure that tracks active function execution contexts. Pushes on call, pops on return.
    

### 3.2 The Browser Runtime Environment

V8 operates alongside browser-provided **Web APIs**, **Task Queues**, and the **Event Loop** to allow non-blocking execution.

Code snippet

```
flowchart TD
    subgraph V8 [V8 Engine]
        CS[Call Stack]
        MH[Memory Heap]
    end
    
    subgraph WebAPI [Web APIs Threads]
        DOM[DOM Events]
        Timer[setTimeout / setInterval]
        Fetch[fetch / Network]
    end
    
    subgraph Queues [Task Queues]
        MTQ[Microtask Queue - Promises]
        MacQ[Macrotask Queue - Timers/Events]
    end
    
    subgraph Pipeline [Rendering Pipeline]
        Render[rAF / Reflow / Repaint]
    end

    WebAPI -->|Callbacks| Queues
    V8 -->|Async Calls| WebAPI
    
    EL((Event Loop)) --> CS
    Queues --> EL
    Pipeline --> EL
```

### 3.3 Microtasks vs. Macrotasks

|**Feature**|**Microtask Queue**|**Macrotask Queue**|
|---|---|---|
|**Sources**|`Promise.then()`, `async/await`, `queueMicrotask()`, `MutationObserver`|`setTimeout`, `setInterval`, DOM events, `setImmediate`|
|**Priority**|**HIGH PRIORITY**|**STANDARD PRIORITY**|
|**Execution Rule**|Drained **completely** until empty in every loop tick.|Executed **ONE task at a time** per loop tick.|

### 3.4 The Event Loop Algorithm (Step-by-Step)

1. **Execute Call Stack**: Run synchronous code on the Call Stack until it is completely empty.
    
2. **Drain Microtasks**: Check the Microtask Queue. Execute and pop tasks **one by one until the queue size is 0**.
    
3. **Render Check (16.6ms / 60 FPS)**: Determine if frame rendering is required:
    
    - Execute `requestAnimationFrame` callbacks.
        
    - Calculate Style recalculation, Layout (Reflow), and Repaint.
        
4. **Execute Macrotask**: Pick the **oldest single task** from the Macrotask Queue and push it onto the Call Stack.
    
5. **Loop**: Repeat step 1 continuously.
    

### 3.5 Async JS & HTML Rendering on the Main Thread

> [!WARNING] The Single Main Thread Limitation ("Jank") JavaScript execution and Screen Rendering (Layout + Paint) run on the exact same main thread. At 60 FPS, the browser has a target budget of **16.66 milliseconds** per frame:
> 
> $\text{Frame Budget} = \frac{1000\text{ms}}{60\text{ FPS}} = 16.66\text{ms}$
> 
> - **Frame Dropping**: If a synchronous JS execution takes > 16.6ms, the Event Loop cannot reach the rendering phase, causing UI stutter.
>     
> - **Microtask Starvation**: Infinite recursive Promises continuously push tasks to the Microtask Queue, freezing rendering and hanging the tab.
>     

## 4. Execution Trace Walkthrough & Performance

### 4.1 Code Execution Walkthrough

JavaScript

```
console.log("1: Script Start");

setTimeout(() => {
  console.log("2: Macrotask (setTimeout)");
}, 0);

Promise.resolve().then(() => {
  console.log("3: Microtask 1");
}).then(() => {
  console.log("4: Microtask 2");
});

console.log("5: Script End");
```

#### Step-by-Step State Tracking Table

|**Step**|**Action / Stack**|**Microtask Queue**|**Macrotask Queue**|**Console Output**|
|---|---|---|---|---|
|**1**|`console.log("1: Script Start")`|`[]`|`[]`|`1: Script Start`|
|**2**|`setTimeout()` offloaded to Web API|`[]`|`[ cb2 ]`|_(No change)_|
|**3**|`Promise.then()` callback registered|`[ cb3 ]`|`[ cb2 ]`|_(No change)_|
|**4**|`console.log("5: Script End")`|`[ cb3 ]`|`[ cb2 ]`|`5: Script End`|
|**5**|Stack Empty -> **Drain Microtask Queue**|Runs `cb3` -> queues `cb4`|`[ cb2 ]`|`3: Microtask 1`|
|**6**|Microtask Queue draining|Runs `cb4` -> empty|`[ cb2 ]`|`4: Microtask 2`|
|**7**|Microtasks Empty -> **Execute 1 Macrotask**|`[]`|Runs `cb2` -> empty|`2: Macrotask (setTimeout)`|

> [!SUCCESS] Final Console Output
> 
> Plaintext
> 
> ```
> 1: Script Start
> 5: Script End
> 3: Microtask 1
> 4: Microtask 2
> 2: Macrotask (setTimeout)
> ```

### 4.2 Web Performance Optimization Strategies

> [!TIP] Performance Checklist
> 
> - **Web Workers**: Move heavy CPU computations to background worker threads so the Main Thread remains free for rendering.
>     
> - **`requestAnimationFrame()`**: Align visual modifications with the browser's refresh rate right before the paint stage.
>     
> - **`requestIdleCallback()`**: Schedule low-priority analytics tasks during frame idle periods.
>     
> - **Avoid Layout Thrashing**: Do not read geometry properties (e.g., `element.offsetWidth`) right after setting styles in JavaScript[cite: 1].


---
tags:
  - web-dev/rendering
  - browser/internals
  - devtools
type: study-notes
---

# Quirks Mode (BackCompat), DevTools & Document Parsing Internals

---

## 1. Why Deleting `<!DOCTYPE>` in DevTools Doesn't Trigger `BackCompat`

When inspecting a live page (like `google.com`) and deleting `<!DOCTYPE html>` in DevTools, `document.compatMode` remains `"CSS1Compat"`. 

```mermaid
flowchart TD
    A[Raw HTML Stream] --> B[HTML Parser Reads <!DOCTYPE>]
    B --> C[Internal C++ Flag Set: QuirksMode = False]
    C --> D[Document Instantiated in CSS1Compat Mode]
    
    E[DevTools: Delete <!DOCTYPE> Node] --> F[Removes DOM Node from Memory Tree]
    F --> G[Layout Engine Rendering Mode Unchanged]
````



# Quirks Mode (BackCompat), DevTools & Document Parsing Internals

---

## 1. Why Deleting `<!DOCTYPE>` in DevTools Doesn't Trigger `BackCompat`

When inspecting a live page (like `google.com`) and deleting `<!DOCTYPE html>` in DevTools, `document.compatMode` remains `"CSS1Compat"`. 

```mermaid


flowchart TD
    A[Raw HTML Stream] --> B[HTML Parser Reads <!DOCTYPE>]
    B --> C[Internal C++ Flag Set: QuirksMode = False]
    C --> D[Document Instantiated in CSS1Compat Mode]
    
    E[DevTools: Delete <!DOCTYPE> Node] --> F[Removes DOM Node from Memory Tree]
    F --> G[Layout Engine Rendering Mode Unchanged]
````

### Core Engine Mechanics

- **Parsing-Stage Lock**: The browser rendering engine (Blink, Gecko, WebKit) determines whether a document runs in **Standards Mode** (`CSS1Compat`) or **Quirks Mode** (`BackCompat`) **once** during the initial HTML parsing stream as network packets arrive.
    
- **Immutable Document Context**: The rendering mode status is saved as an internal C++ boolean flag on the core `Document` instance. Modifying, deleting, or adding DOM nodes after parsing has started only alters the tree data structure; it **does not trigger a full re-parse** or reset the engine state.
    

## 2. `document.compatMode` Quick Reference

|**Property Value**|**Rendering Mode**|**Cause**|**Key Characteristics**|
|---|---|---|---|
|**`"CSS1Compat"`**|Standards Mode|Valid `<!DOCTYPE html>` present at top of source.|Modern W3C CSS box model, case-sensitive classes, proper layout rules.|
|**`"BackCompat"`**|Quirks Mode|Missing, misspelled, or legacy `<!DOCTYPE>`.|IE5 box model, table font inheritance bugs, case-insensitive selector matching.|

## 3. Key Behavioral Breaks in `BackCompat` (Quirks Mode)

> [!WARNING] Modern Layouts Break under Quirks Mode
> 
> When a browser falls back to `BackCompat`, it intentionally reintroduces legacy layout bugs:
> 
> - **IE Box Model Sizing**: Width and height calculations include padding and borders rather than placing them outside the content box ($W = \text{content} + \text{padding} + \text{border}$).
>     
> - **Table Font Inheritance Failure**: Form elements and `<table>` cells do not inherit `font-family` or `font-size` from `body` rules, defaulting to standard browser fonts (e.g., Times New Roman).
>     
> - **Inline Sizing Anomalies**: Inline non-replaced elements (like `<span>`) incorrectly honor `width` and `height` properties instead of ignoring them.
>     
> - **Selector Case Insensitivity**: Class names and IDs behave as case-insensitive (`.myClass` matches `.MYCLASS`).
>     

## 4. How to Force Live Sites into `BackCompat` for Testing

### Method 1: Dynamic `<iframe>` Injection (Console Snippet)

Because the top-level document mode is locked at load, you can dynamically create a isolated, unrendered `<iframe>` without a DOCTYPE from the console to test `BackCompat`:

JavaScript

```
// Create a new unparsed iframe context
const iframe = document.createElement('iframe');
document.body.appendChild(iframe);

// Write HTML without a DOCTYPE into the iframe's document stream
const iframeDoc = iframe.contentDocument;
iframeDoc.open();
iframeDoc.write('<html><body><h1>Testing Quirks Mode</h1></body></html>');
iframeDoc.close();

// Verify the rendering mode inside the iframe
console.log('Iframe Compat Mode:', iframeDoc.compatMode); // Outputs: "BackCompat"
```

### Method 2: DevTools Local Overrides (Full Page Simulation)

To force an entire web page (e.g., `google.com`) to reload and parse from scratch in `BackCompat` mode:

1. Open **DevTools** (`F12`) on the target page.
    
2. Go to the **Sources** tab and click the **Overrides** sub-tab in the left panel.
    
3. Click `+ Select folder for overrides` and grant DevTools file access to a local directory.
    
4. Switch to the **Network** tab, right-click the top document request (e.g., `google.com` or `index.html`), and choose **Override content**.
    
5. In the editor tab that opens, **delete the `<!DOCTYPE html>` line** at the very top of the document.
    
6. Press `Ctrl + S` (`Cmd + S` on macOS) to save the file override.
    
7. Reload the page (`F5` or `Ctrl + R`).
    
8. Run `document.compatMode` in the Console — it will now return **`"BackCompat"`**.