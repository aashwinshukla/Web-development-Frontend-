# HTML — Structure and Elements

## HTML Skeleton

Every HTML file follows the same core structure. This is the minimum you need for a valid HTML page:

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

## Common Elements

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

### Line Break
```html
<p>Line one.<br />Line two.</p>
```
`<br />` forces a line break inside an element. Don't overuse it — use it only when a break is meaningful, not for spacing.

### Horizontal Rule
```html
<hr />
```
Draws a horizontal line — useful as a visual divider between sections.

---

## Text Formatting

Some tags are purely visual. Others carry semantic meaning — that distinction matters for accessibility and SEO.

```html
<b>Bold</b>                    <!-- visually bold, no extra meaning -->
<strong>Strong</strong>         <!-- bold + signals importance -->

<i>Italic</i>                  <!-- visually italic, no extra meaning -->
<em>Emphasized</em>            <!-- italic + signals emphasis -->

<u>Underlined</u>              <!-- underline -->
<s>Strikethrough</s>           <!-- crossed out text -->

<mark>Highlighted</mark>        <!-- yellow highlight by default -->

<small>Small text</small>      <!-- renders text smaller -->

<sup>Superscript</sup>         <!-- e.g. x<sup>2</sup> → x² -->
<sub>Subscript</sub>           <!-- e.g. H<sub>2</sub>O → H₂O -->

<code>inline code</code>       <!-- monospace font, used for code snippets -->

<pre>
  Preformatted text
  preserves spacing and line breaks exactly as written
</pre>

<blockquote>
  Used for longer quotes pulled from another source.
</blockquote>

<abbr title="HyperText Markup Language">HTML</abbr>
<!-- hovering over the text shows the full form as a tooltip -->
```

**Semantic vs visual:**
Prefer `<strong>` over `<b>` and `<em>` over `<i>`. The semantic versions tell browsers and screen readers that the content is actually important or emphasized — not just styled differently.

---

## Div and Span

Both are generic containers with no visual style of their own. Their job is to group content so CSS or JavaScript can target it.

### `<div>` — block-level container
Takes up the full width of its parent and starts on a new line. Used to group larger chunks of content.

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

### The key difference

```html
<!-- div pushes content onto its own line -->
<div>First block</div>
<div>Second block</div>

<!-- span stays within the line -->
<p>This is <span>inline</span> and stays in the same line.</p>
```

On their own, neither `<div>` nor `<span>` does anything visually. They become useful once you give them a `class` or `id` and style them with CSS.
