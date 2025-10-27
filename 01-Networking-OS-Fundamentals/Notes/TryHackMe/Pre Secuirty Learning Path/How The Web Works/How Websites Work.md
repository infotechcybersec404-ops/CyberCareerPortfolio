### How Websites Work

### 🔑 Core Idea

- When you visit a website, your **browser** (Chrome, Safari, etc.) sends a **request** to a **web server**.
- The server responds with data (HTML, CSS, JavaScript, images, etc.), which your browser renders into the page you see.
- A **web server** is simply a dedicated computer somewhere on the internet that handles these requests.

### 🖥️ Two Major Components of a Website

| Component | Role | Example Responsibilities |
| --- | --- | --- |
| **Front End (Client-Side)** | What the user sees and interacts with in the browser | Layout, styling, interactivity (HTML, CSS, JavaScript) |
| **Back End (Server-Side)** | Processes requests and sends responses | Database queries, authentication, business logic |

👉 **In short:**

- **Front End** = Presentation (the “face” of the website).
- **Back End** = Processing (the “brain” of the website).
- **Browser ↔ Server** = Constant request/response cycle that makes the web work.

### HTML

Websites are primarily built using three foundational technologies:

- **HTML (HyperText Markup Language):** Defines the **structure** of a webpage.
- **CSS (Cascading Style Sheets):** Adds **styling** (colors, layouts, fonts, etc.).
- **JavaScript:** Provides **interactivity** and dynamic features.

## 📄 HTML Basics

HTML is the backbone of every website. It uses **elements (tags)** to tell the browser how to display content.

### 🔑 Standard HTML Document Structure

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My First Page</title>
  </head>
  <body>
    <h1>Hello World</h1>
    <p>This is a paragraph.</p>
  </body>
</html>

```

### 🧩 Key Components

| Element | Purpose |
| --- | --- |
| `<!DOCTYPE html>` | Declares the document as HTML5 for browser standardization. |
| `<html>` | Root element; everything else goes inside. |
| `<head>` | Metadata about the page (title, links to CSS/JS, etc.). |
| `<body>` | Visible content of the page. |
| `<h1>` | Heading (largest level). |
| `<p>` | Paragraph text. |

## 🎨 Attributes in HTML

- **`class`** → Used for styling multiple elements with CSS.
    
    ```html
    <p class="bold-text">Styled text</p>
    ```
    
- **`id`** → Unique identifier for one element (used in CSS/JavaScript).
    
    ```html
    <p id="intro">Unique element</p>
    ```
    
- **`src`** → Specifies the source of an image or media file.
    
    ```html
    <img src="img/cat.jpg" alt="A cat">
    ```
    
- Elements can have **multiple attributes**:
    
    ```html
    <p class="highlight" id="example">Text</p>
    ```
    

## 🔍 Viewing HTML in the Browser

- **Chrome:** Right‑click → *View Page Source*
- **Safari:** Right‑click → *Show Page Source*

👉 **In short:**

- **HTML = structure**
- **CSS = style**
- **JavaScript = behavior**

### JavaScript

### 🔑 What is JavaScript?

- One of the most popular programming languages in the world.
- Adds **interactivity** and **dynamic behavior** to otherwise static HTML pages.
- Can update content in **real-time** (e.g., animations, button effects, live updates).

### 📄 How JavaScript is Added

- **Inline in HTML** using `<script>` tags.
- **External file** using the `src` attribute:
    
    ```html
    <script src="/location/of/javascript_file.js"></script>
    ```
    

### 🧩 Example: Changing Content

```jsx
document.getElementById("demo").innerHTML = "Hack the Planet";
```

- Finds the element with `id="demo"`.
- Replaces its content with `"Hack the Planet"`.

### 🎛️ Events in JavaScript

HTML elements can trigger JavaScript when certain **events** occur.

**Example: Onclick Event**

```html
<button onclick='document.getElementById("demo").innerHTML = "Button Clicked";'>
  Click Me!
</button>
```

- When the button is clicked, the text of the element with `id="demo"` changes to **“Button Clicked”**.

> Events like onclick, onhover, onload, etc., can also be defined inside <script> tags instead of directly in the element.
> 

👉 **In short:**

- **HTML = structure**
- **CSS = style**
- **JavaScript = behavior & interactivity**

### Sensitive Data Exposure

- Happens when websites leave sensitive information (like credentials or hidden links) visible in frontend code (HTML/JavaScript).
- Developers may forget to remove this data, leaving it accessible through “view page source.”
- Attackers can exploit exposed info (e.g., credentials in comments) to gain unauthorized access to other parts of the application or backend systems.
- **Best practice:** Always review page source during security assessments to check for exposed credentials or hidden links.

### HTML Injection

- **Definition:**
    
    HTML Injection occurs when unfiltered user input is directly displayed on a webpage. If input isn’t sanitized, attackers can inject HTML or JavaScript into the site.
    
- **Cause:**
    - Website fails to sanitize user input.
    - User-controlled data is inserted into frontend code (HTML/JavaScript).
- **Impact:**
    - Attackers can alter page appearance or functionality.
    - Malicious scripts may run in the victim’s browser.
    - Can serve as a stepping stone to more severe attacks.
- **Example:**
    
    A form field (e.g., “What’s your name?”) outputs user input directly into the page. If an attacker enters `<h1>Hacked</h1>`, the browser renders it as HTML instead of plain text.
    
- **Prevention:**
    - **Never trust user input.**
    - Sanitize and validate all input before using it in frontend or backend code.
    - Strip or escape HTML tags to ensure input is treated as text, not executable code.
