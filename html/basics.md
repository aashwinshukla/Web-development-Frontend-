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
