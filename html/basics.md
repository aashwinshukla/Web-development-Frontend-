# HTML Basics

## HTML Structure

Every HTML file follows the same core skeleton. This is the minimum you need for a valid HTML page:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>My Page</title>
  </head>
  <body>

    <h1>Hello World</h1>
    <p>This is a paragraph.</p>

  </body>
</html>
```

**Breaking it down:**

- `<!DOCTYPE html>` — declares this as an HTML5 document. Always the first line.
- `<html lang="en">` — the root element wrapping everything. `lang` helps browsers and screen readers know the language.
- `<head>` — invisible to the user. Holds metadata, the page title, links to CSS/JS, etc.
  - `<meta charset="UTF-8">` — ensures characters like accents and symbols display correctly.
  - `<meta name="viewport" ...>` — makes the page responsive on mobile devices.
  - `<title>` — the text shown on the browser tab.
- `<body>` — everything the user actually sees goes here.

---

## Common HTML Elements

### Headings
```html
<h1>Main Heading</h1>
<h2>Sub Heading</h2>
<h3>Smaller Heading</h3>
```
Goes from `<h1>` (largest/most important) to `<h6>` (smallest). There should only be one `<h1>` per page.

### Paragraph
```html
<p>This is a paragraph of text.</p>
```

### Bold and Italic
```html
<strong>Bold text</strong>
<em>Italic text</em>
```
`<strong>` and `<em>` also carry meaning — strong means importance, em means emphasis.

### Line Break
```html
<p>Line one.<br />Line two.</p>
```
`<br />` forces a line break inside an element.

### Horizontal Rule
```html
<hr />
```
Draws a horizontal line — useful as a visual divider.

### Lists
```html
<!-- Unordered (bullet points) -->
<ul>
  <li>Item one</li>
  <li>Item two</li>
</ul>

<!-- Ordered (numbered) -->
<ol>
  <li>First</li>
  <li>Second</li>
</ol>
```

### Div and Span
```html
<div>Block-level container</div>
<span>Inline container</span>
```
`<div>` groups block content (takes up full width). `<span>` groups inline content (only as wide as its content). Both are used heavily for layout and styling with CSS.

---

## Hyperlinks

Links are created with the `<a>` (anchor) tag.

```html
<a href="https://www.google.com">Go to Google</a>
```

- `href` — the URL the link points to. This is required.
- The text between the tags is what the user clicks on.

### Open in a new tab
```html
<a href="https://www.google.com" target="_blank">Open in new tab</a>
```
`target="_blank"` opens the link in a new browser tab.

### Link to another page in your project
```html
<a href="about.html">About Page</a>
```
You can link to other HTML files in your project using a relative path.

### Link to a section on the same page
```html
<!-- The target needs an id -->
<h2 id="contact">Contact</h2>

<!-- The link uses # followed by the id -->
<a href="#contact">Jump to Contact</a>
```

### Email link
```html
<a href="mailto:someone@example.com">Send Email</a>
```

---

## Images

Images are added with the `<img>` tag. It is a self-closing tag — no closing `</img>` needed.

```html
<img src="photo.jpg" alt="A description of the photo" />
```

- `src` — the path to the image file (can be a local file or a URL).
- `alt` — alternative text. Shown if the image fails to load. Also read by screen readers — important for accessibility. Never leave it empty unless the image is purely decorative.

### Sizing an image
```html
<img src="photo.jpg" alt="A photo" width="400" height="300" />
```
You can set width and height in HTML, but it's more common to handle sizing in CSS.

### Using an image from the web
```html
<img src="https://example.com/image.jpg" alt="Image from the web" />
```

### Local image in a subfolder
```html
<img src="images/photo.jpg" alt="Local image" />
```

---

## Audio

Audio is added with the `<audio>` tag.

```html
<audio controls>
  <source src="audio.mp3" type="audio/mpeg" />
  Your browser does not support the audio element.
</audio>
```

- `controls` — adds the play, pause, and volume controls. Without this the audio is invisible and uncontrollable.
- `<source>` — specifies the audio file and its type.
- The fallback text between the tags shows if the browser doesn't support the element.

### Common attributes
```html
<audio controls autoplay loop muted>
  <source src="audio.mp3" type="audio/mpeg" />
</audio>
```
- `autoplay` — plays automatically when the page loads (often blocked by browsers unless `muted` is also set).
- `loop` — replays the audio when it ends.
- `muted` — starts muted.

### Multiple formats for browser compatibility
```html
<audio controls>
  <source src="audio.mp3" type="audio/mpeg" />
  <source src="audio.ogg" type="audio/ogg" />
</audio>
```
The browser picks the first format it supports.

---

## Video

Video works almost the same as audio but with the `<video>` tag.

```html
<video controls width="640">
  <source src="video.mp4" type="video/mp4" />
  Your browser does not support the video element.
</video>
```

- `controls` — same as audio, adds the playback controls.
- `width` — sets the display width (height adjusts automatically to keep aspect ratio).

### Common attributes
```html
<video controls autoplay loop muted poster="thumbnail.jpg" width="640">
  <source src="video.mp4" type="video/mp4" />
</video>
```
- `autoplay` — plays automatically (requires `muted` in most browsers).
- `loop` — loops the video.
- `muted` — starts with no sound.
- `poster` — an image shown before the video plays, like a thumbnail.

---

## Favicon

A favicon is the small icon that appears on the browser tab next to the page title.

```html
<head>
  <link rel="icon" type="image/png" href="favicon.png" />
</head>
```

- This goes inside the `<head>` tag.
- `rel="icon"` — tells the browser this is the page icon.
- `href` — path to your icon file.

### Common formats
- `.ico` — the classic format, works everywhere.
- `.png` — widely supported and easier to work with.
- `.svg` — modern, scales perfectly at any size.

```html
<!-- .ico example -->
<link rel="icon" type="image/x-icon" href="favicon.ico" />

<!-- .png example -->
<link rel="icon" type="image/png" href="favicon.png" />

<!-- .svg example -->
<link rel="icon" type="image/svg+xml" href="favicon.svg" />
```

If no favicon is set, the browser shows a default blank icon. You can generate a favicon from any image using free tools like [favicon.io](https://favicon.io).

---

## Text Formatting

HTML has several tags specifically for formatting text. Some are visual, some carry meaning.

```html
<b>Bold</b>                   <!-- visually bold, no extra meaning -->
<strong>Strong</strong>        <!-- bold + signals importance -->

<i>Italic</i>                 <!-- visually italic, no extra meaning -->
<em>Emphasized</em>           <!-- italic + signals emphasis -->

<u>Underlined</u>             <!-- underline -->
<s>Strikethrough</s>          <!-- crossed out text -->

<mark>Highlighted</mark>       <!-- yellow highlight by default -->

<small>Small text</small>     <!-- renders text smaller -->

<sup>Superscript</sup>        <!-- e.g. x<sup>2</sup> → x² -->
<sub>Subscript</sub>          <!-- e.g. H<sub>2</sub>O → H₂O -->

<code>inline code</code>      <!-- monospace, used for code snippets -->

<pre>
  Preformatted text
  preserves spacing and line breaks
</pre>

<blockquote>
  Used for longer quotes from another source.
</blockquote>

<abbr title="HyperText Markup Language">HTML</abbr>
<!-- hovering over the text shows the full form -->
```

**Semantic vs visual:**
Tags like `<strong>` and `<em>` are preferred over `<b>` and `<i>` because they carry meaning — screen readers and search engines treat them as signals of importance, not just styling.

---

## Div and Span

Both are generic containers with no visual style of their own. Their purpose is to group content so you can target it with CSS or JavaScript.

### `<div>` — block-level container
Takes up the full width of its parent. Starts on a new line. Used to group larger sections of content.

```html
<div class="card">
  <h2>Title</h2>
  <p>Some description here.</p>
</div>
```

### `<span>` — inline container
Only as wide as its content. Sits inside a line of text without breaking the flow. Used to target a specific word or phrase.

```html
<p>The sky is <span class="highlight">bright blue</span> today.</p>
```

### Key difference
```html
<!-- div breaks onto its own line -->
<div>First block</div>
<div>Second block</div>

<!-- span stays inline -->
<p>This is <span>inline</span> and stays in the same line.</p>
```

On their own, `<div>` and `<span>` do nothing visually. They become useful when you add a `class` or `id` and style them with CSS.

---

## Lists

### Unordered List
Displays items with bullet points. Order does not matter.

```html
<ul>
  <li>HTML</li>
  <li>CSS</li>
  <li>JavaScript</li>
</ul>
```

### Ordered List
Displays items with numbers. Order matters.

```html
<ol>
  <li>Boil water</li>
  <li>Add pasta</li>
  <li>Cook for 10 minutes</li>
</ol>
```

You can change the numbering style with the `type` attribute:
```html
<ol type="A">   <!-- A, B, C -->
<ol type="a">   <!-- a, b, c -->
<ol type="I">   <!-- I, II, III -->
<ol type="i">   <!-- i, ii, iii -->
<ol start="5">  <!-- starts counting from 5 -->
```

### Description List
Used for term-definition pairs — like a glossary.

```html
<dl>
  <dt>HTML</dt>
  <dd>The structure of a webpage.</dd>

  <dt>CSS</dt>
  <dd>The styling of a webpage.</dd>

  <dt>JavaScript</dt>
  <dd>The behaviour of a webpage.</dd>
</dl>
```

- `<dl>` — the description list wrapper
- `<dt>` — the term
- `<dd>` — the definition (indented by default)

### Nested Lists
You can put any list inside an `<li>` to create sub-levels.

```html
<ul>
  <li>Frontend
    <ul>
      <li>HTML</li>
      <li>CSS</li>
      <li>JavaScript</li>
    </ul>
  </li>
  <li>Backend
    <ul>
      <li>Node.js</li>
      <li>Python</li>
    </ul>
  </li>
</ul>
```

You can nest ordered inside unordered and vice versa:

```html
<ol>
  <li>Step one</li>
  <li>Step two
    <ul>
      <li>Sub-step A</li>
      <li>Sub-step B</li>
    </ul>
  </li>
  <li>Step three</li>
</ol>
```

---

## Tables

Tables are used to display data in rows and columns.

```html
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Age</th>
      <th>City</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Alice</td>
      <td>24</td>
      <td>New York</td>
    </tr>
    <tr>
      <td>Bob</td>
      <td>30</td>
      <td>London</td>
    </tr>
  </tbody>
</table>
```

**Tags used:**
- `<table>` — the table wrapper
- `<thead>` — groups the header row(s)
- `<tbody>` — groups the data rows
- `<tr>` — table row
- `<th>` — table header cell (bold and centered by default)
- `<td>` — table data cell

### Spanning columns and rows
```html
<!-- colspan: cell stretches across 2 columns -->
<td colspan="2">Merged across 2 columns</td>

<!-- rowspan: cell stretches across 2 rows -->
<td rowspan="2">Merged across 2 rows</td>
```

### Table with a caption
```html
<table>
  <caption>Student Results</caption>
  <thead>
    <tr>
      <th>Name</th>
      <th>Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Alice</td>
      <td>95</td>
    </tr>
  </tbody>
</table>
```

`<caption>` appears above the table and acts as its title.

> Tables are for tabular data only — not for page layout. CSS is used for layout.

---

## Buttons

The `<button>` tag creates a clickable button.

```html
<button>Click Me</button>
```

### Button types
The `type` attribute controls what the button does:

```html
<!-- Submit: submits a form (default behavior inside a form) -->
<button type="submit">Submit</button>

<!-- Reset: clears all inputs in a form -->
<button type="reset">Reset</button>

<!-- Button: does nothing by default, used with JavaScript -->
<button type="button">Click Me</button>
```

Always specify `type="button"` when using a button outside a form or with JavaScript — without it, some browsers default to `type="submit"` which can cause unexpected behavior.

### Disabled button
```html
<button type="button" disabled>Not Available</button>
```
Greyed out and unclickable.

### Button vs input type button
You may also see this older style:
```html
<input type="button" value="Click Me" />
```
The `<button>` tag is preferred because it can contain HTML inside it (like icons), while `<input>` can only show plain text.

---

## Forms

Forms are used to collect input from the user — login forms, search bars, contact forms, sign-up pages, etc.

```html
<form action="/submit" method="POST">
  <!-- inputs go here -->
</form>
```

- `action` — the URL where the form data is sent when submitted. If left empty, it submits to the current page.
- `method` — how the data is sent:
  - `GET` — data is appended to the URL (visible, used for searches)
  - `POST` — data is sent in the request body (hidden, used for sensitive data like passwords)

---

### Input Fields

The `<input>` tag is the most common form element. The `type` attribute defines what kind of input it is.

```html
<!-- Text -->
<input type="text" placeholder="Enter your name" />

<!-- Email -->
<input type="email" placeholder="Enter your email" />

<!-- Password -->
<input type="password" placeholder="Enter password" />

<!-- Number -->
<input type="number" min="1" max="100" />

<!-- Date -->
<input type="date" />

<!-- Checkbox -->
<input type="checkbox" /> Remember me

<!-- Radio buttons -->
<input type="radio" name="gender" value="male" /> Male
<input type="radio" name="gender" value="female" /> Female

<!-- File upload -->
<input type="file" />

<!-- Hidden field (not visible to user) -->
<input type="hidden" name="userId" value="42" />

<!-- Color picker -->
<input type="color" />

<!-- Range slider -->
<input type="range" min="0" max="100" />
```

> Radio buttons with the same `name` are grouped — only one can be selected at a time.

---

### Labels

Labels connect to inputs and tell the user what to fill in. Clicking the label focuses the input — improves usability and accessibility.

```html
<!-- Using 'for' and 'id' to connect them -->
<label for="username">Username</label>
<input type="text" id="username" name="username" />

<!-- Wrapping the input inside the label (also works) -->
<label>
  Email
  <input type="email" name="email" />
</label>
```

Always use labels — they are important for screen readers and accessibility.

---

### Textarea

For multi-line text input.

```html
<label for="message">Message</label>
<textarea id="message" name="message" rows="5" cols="40" placeholder="Write your message..."></textarea>
```

- `rows` and `cols` set the default visible size.
- Unlike `<input>`, `<textarea>` has a closing tag.

---

### Select Dropdown

```html
<label for="country">Country</label>
<select id="country" name="country">
  <option value="">-- Select --</option>
  <option value="us">United States</option>
  <option value="uk">United Kingdom</option>
  <option value="in">India</option>
</select>
```

- The `value` of the selected `<option>` is what gets submitted.
- Add `selected` to an option to make it the default: `<option value="in" selected>India</option>`

### Grouped options
```html
<select name="car">
  <optgroup label="German">
    <option value="bmw">BMW</option>
    <option value="audi">Audi</option>
  </optgroup>
  <optgroup label="Japanese">
    <option value="toyota">Toyota</option>
    <option value="honda">Honda</option>
  </optgroup>
</select>
```

---

### Common Input Attributes

| Attribute     | What it does                                              |
|---------------|-----------------------------------------------------------|
| `name`        | The key sent with the form data — required for submission |
| `id`          | Used to link with a `<label>` and target with CSS/JS      |
| `placeholder` | Hint text shown inside the input when empty               |
| `value`       | Pre-filled value                                          |
| `required`    | Makes the field mandatory before the form can submit      |
| `disabled`    | Input is visible but not editable or submittable          |
| `readonly`    | Input is visible and selectable but not editable          |
| `maxlength`   | Maximum number of characters allowed                      |
| `min` / `max` | Minimum and maximum values for number/date inputs         |

---

### Fieldset and Legend

Used to group related inputs and give the group a label.

```html
<fieldset>
  <legend>Personal Information</legend>

  <label for="fname">First Name</label>
  <input type="text" id="fname" name="fname" />

  <label for="lname">Last Name</label>
  <input type="text" id="lname" name="lname" />
</fieldset>
```

`<fieldset>` draws a box around the group. `<legend>` is the title of that box.

---

### A Complete Form Example

```html
<form action="/register" method="POST">
  <fieldset>
    <legend>Create Account</legend>

    <label for="username">Username</label>
    <input type="text" id="username" name="username" required />

    <label for="email">Email</label>
    <input type="email" id="email" name="email" required />

    <label for="password">Password</label>
    <input type="password" id="password" name="password" required />

    <label for="country">Country</label>
    <select id="country" name="country">
      <option value="">-- Select --</option>
      <option value="us">United States</option>
      <option value="in">India</option>
    </select>

    <label>
      <input type="checkbox" name="terms" required />
      I agree to the terms and conditions
    </label>

    <button type="submit">Register</button>
  </fieldset>
</form>
```

---

## Header and Footer

These are semantic HTML elements — they give meaning to the structure of a page, making it easier to read, maintain, and understand for both developers and browsers.

---

### `<header>`

Represents the top section of a page or a section. Typically contains the site logo, navigation, and page title.

```html
<header>
  <h1>My Website</h1>
  <nav>
    <a href="index.html">Home</a>
    <a href="about.html">About</a>
    <a href="contact.html">Contact</a>
  </nav>
</header>
```

- `<header>` is not the same as `<head>`. The `<head>` is invisible metadata. The `<header>` is visible page content.
- You can have multiple `<header>` elements on a page — one for the page, one inside an `<article>`, etc.

---

### `<nav>`

Used inside a header (or anywhere) to wrap navigation links.

```html
<nav>
  <ul>
    <li><a href="index.html">Home</a></li>
    <li><a href="about.html">About</a></li>
    <li><a href="contact.html">Contact</a></li>
  </ul>
</nav>
```

Using a list inside `<nav>` is a common and accessible pattern.

---

### `<footer>`

Represents the bottom section of a page or section. Typically contains copyright info, links, contact details, or social media icons.

```html
<footer>
  <p>&copy; 2026 My Website. All rights reserved.</p>
  <nav>
    <a href="privacy.html">Privacy Policy</a>
    <a href="terms.html">Terms of Service</a>
  </nav>
</footer>
```

- `&copy;` is an HTML entity that renders the © symbol.
- Like `<header>`, you can have multiple `<footer>` elements — one for the page, one inside an article, etc.

---

### Other Semantic Layout Elements

While we're here — these are commonly used alongside header and footer to build a full page structure:

```html
<body>

  <header>
    <!-- logo, nav -->
  </header>

  <main>
    <!-- the primary content of the page, only one per page -->

    <section>
      <!-- a themed group of content -->
    </section>

    <article>
      <!-- self-contained content like a blog post or news item -->
    </article>

    <aside>
      <!-- secondary content, like a sidebar -->
    </aside>

  </main>

  <footer>
    <!-- copyright, links -->
  </footer>

</body>
```

These tags don't add any visual style on their own — but they make the page structure clear and meaningful. This matters for SEO, accessibility, and working with CSS later.
