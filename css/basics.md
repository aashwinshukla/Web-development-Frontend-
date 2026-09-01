# CSS Basics

## Colors

CSS gives you several ways to define colors. They all work the same way — just different formats.

### Named colors
```css
p {
  color: red;
  background-color: lightblue;
}
```
CSS has 140+ built-in named colors. Good for quick testing, not ideal for precise design work.

### Hex
```css
p {
  color: #ff0000;        /* red */
  background-color: #1a1a2e;
}
```
A `#` followed by 6 hex digits — two each for red, green, and blue. The most commonly used format in real projects.

Short form works when each pair repeats:
```css
color: #fff;    /* same as #ffffff — white */
color: #000;    /* same as #000000 — black */
```

### RGB
```css
p {
  color: rgb(255, 0, 0);       /* red */
  color: rgb(30, 30, 50);
}
```
Three values — red, green, blue — each from 0 to 255.

### RGBA — RGB with transparency
```css
p {
  background-color: rgba(0, 0, 0, 0.5);  /* black at 50% opacity */
}
```
The fourth value is **alpha** — opacity from `0` (fully transparent) to `1` (fully opaque).

### HSL
```css
p {
  color: hsl(0, 100%, 50%);   /* red */
}
```
Stands for **Hue, Saturation, Lightness**. More intuitive for adjusting shades — just tweak the lightness or saturation value.

### Where colors are used
```css
p {
  color: #333;                  /* text color */
  background-color: #f5f5f5;   /* background */
  border-color: #ccc;           /* border */
  outline-color: blue;          /* outline */
}
```

---

## Fonts

### Font family
```css
p {
  font-family: Arial, Helvetica, sans-serif;
}
```
You list multiple fonts separated by commas — this is called a **font stack**. The browser uses the first one it has installed. The last value should always be a generic fallback: `sans-serif`, `serif`, or `monospace`.

### Font size
```css
p {
  font-size: 16px;     /* pixels — fixed size */
  font-size: 1rem;     /* relative to root element (html) font size */
  font-size: 1.2em;    /* relative to the parent element's font size */
  font-size: 120%;     /* percentage of the parent font size */
}
```

`px` is the most straightforward. `rem` is widely used in real projects because it scales well across different screen sizes and user preferences.

### Font weight
```css
p {
  font-weight: normal;   /* default */
  font-weight: bold;
  font-weight: 400;      /* same as normal */
  font-weight: 700;      /* same as bold */
}
```
Numeric values go from 100 (thin) to 900 (extra bold). Not all fonts support every weight.

### Font style
```css
p {
  font-style: normal;
  font-style: italic;
  font-style: oblique;
}
```

### Text decoration
```css
p {
  text-decoration: none;          /* removes underline from links */
  text-decoration: underline;
  text-decoration: line-through;
  text-decoration: overline;
}
```

### Text transform
```css
p {
  text-transform: uppercase;
  text-transform: lowercase;
  text-transform: capitalize;   /* capitalizes first letter of each word */
}
```

### Text alignment
```css
p {
  text-align: left;
  text-align: center;
  text-align: right;
  text-align: justify;
}
```

### Line height
```css
p {
  line-height: 1.6;    /* 1.6x the font size — unitless is recommended */
  line-height: 24px;
}
```
Controls the vertical space between lines of text. A value around `1.5`–`1.6` is comfortable for body text.

### Letter spacing
```css
p {
  letter-spacing: 2px;   /* space between characters */
}
```

### Google Fonts
To use a font not installed on the user's system, you can load one from Google Fonts.

```html
<!-- In your HTML <head> -->
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet" />
```

```css
body {
  font-family: 'Roboto', sans-serif;
}
```

Go to [fonts.google.com](https://fonts.google.com), pick a font, copy the `<link>` tag, and then use the font name in your CSS.

---

## Borders

```css
div {
  border: 2px solid black;
}
```

The shorthand takes three values: **width**, **style**, **color**. The style is required — without it the border won't show.

### Border styles
```css
border-style: solid;    /* a continuous line */
border-style: dashed;   /* dashed line */
border-style: dotted;   /* dotted line */
border-style: double;   /* two parallel lines */
border-style: none;     /* no border */
```

### Setting each side individually
```css
div {
  border-top: 2px solid red;
  border-right: 1px dashed blue;
  border-bottom: 3px dotted green;
  border-left: none;
}
```

Or using longhand properties:
```css
div {
  border-width: 2px;
  border-style: solid;
  border-color: black;
}
```

### Border radius — rounded corners
```css
div {
  border-radius: 8px;       /* all four corners */
  border-radius: 50%;       /* makes a circle if width == height */
  border-radius: 4px 12px;  /* top-left/bottom-right, top-right/bottom-left */
}
```

### Outline
Similar to border but sits outside the element and does not affect layout (does not take up space).

```css
input:focus {
  outline: 2px solid blue;
  outline-offset: 3px;   /* gap between element and outline */
}
```

---

## Margin and Padding

These two control spacing. They are often confused but work differently.

- **Padding** — space *inside* the element, between the content and the border.
- **Margin** — space *outside* the element, between the element and everything around it.

```css
div {
  padding: 20px;
  margin: 10px;
}
```

### The Box Model

Every HTML element is a box made up of four layers from the inside out:

```
┌─────────────────────────────┐
│           MARGIN            │
│  ┌───────────────────────┐  │
│  │        BORDER         │  │
│  │  ┌─────────────────┐  │  │
│  │  │     PADDING     │  │  │
│  │  │  ┌───────────┐  │  │  │
│  │  │  │  CONTENT  │  │  │  │
│  │  │  └───────────┘  │  │  │
│  │  └─────────────────┘  │  │
│  └───────────────────────┘  │
└─────────────────────────────┘
```

### Shorthand

```css
/* All four sides the same */
padding: 20px;

/* Top/bottom, Left/right */
padding: 10px 20px;

/* Top, Left/right, Bottom */
padding: 10px 20px 15px;

/* Top, Right, Bottom, Left (clockwise) */
padding: 10px 20px 15px 5px;
```

The same shorthand pattern applies to `margin`.

### Individual sides

```css
div {
  margin-top: 10px;
  margin-right: 20px;
  margin-bottom: 10px;
  margin-left: 20px;

  padding-top: 10px;
  padding-right: 15px;
  padding-bottom: 10px;
  padding-left: 15px;
}
```

### Auto margin — centering an element

```css
div {
  width: 600px;
  margin: 0 auto;   /* 0 top/bottom, auto left/right — centers horizontally */
}
```

`margin: auto` on left and right pushes a block element to the center. The element needs a fixed width for this to work.

### Collapsing margins

Vertical margins (top and bottom) between two block elements **collapse** — meaning only the larger of the two margins is used, not the sum.

```css
/* These two paragraphs will have 20px between them, not 30px */
p { margin-bottom: 20px; }
p { margin-top: 10px; }
```

This only happens with vertical margins, never horizontal.

### box-sizing

By default, `width` and `height` only apply to the content area. Padding and border are added on top, making elements larger than expected.

```css
/* This is the fix — apply it universally */
* {
  box-sizing: border-box;
}
```

With `border-box`, padding and border are included *inside* the declared width and height. This is the standard practice in modern CSS — almost every project starts with this rule.

---

## Float

Float was originally designed for wrapping text around images — the same way magazines wrap text around photos.

```css
img {
  float: left;    /* image floats left, text wraps around the right side */
  float: right;   /* image floats right, text wraps around the left side */
  float: none;    /* default — no float */
}
```

```html
<img src="photo.jpg" alt="A photo" style="float: left; margin-right: 16px;" />
<p>This text will wrap around the image on the right side.</p>
```

### The float problem — clearing

Floated elements are removed from the normal document flow. This means a parent container will not expand to wrap its floated children — it collapses to zero height.

```css
/* Fix: add a clearfix to the parent */
.clearfix::after {
  content: "";
  display: block;
  clear: both;
}
```

```html
<div class="clearfix">
  <img src="photo.jpg" style="float: left;" />
  <p>Some text.</p>
</div>
```

Or you can clear on a specific element:
```css
.clear {
  clear: both;    /* element drops below all floated elements */
  clear: left;    /* drops below left-floated elements only */
  clear: right;   /* drops below right-floated elements only */
}
```

### Float today

Float is still used for its original purpose — wrapping text around images. But it was also used for years to build entire page layouts before better tools existed. 

For layout today, **Flexbox** and **CSS Grid** are used instead. They are purpose-built for layout, easier to control, and don't have the float clearing problems.

---

## Overflow

Overflow controls what happens when content is too large to fit inside its container.

```css
div {
  width: 300px;
  height: 150px;
  overflow: visible;   /* default — content spills outside the box */
}
```

### Values

| Value     | What it does                                                        |
|-----------|---------------------------------------------------------------------|
| `visible` | Default. Content overflows and is visible outside the element       |
| `hidden`  | Overflow is clipped — the extra content is invisible                |
| `scroll`  | Always shows scrollbars, whether content overflows or not           |
| `auto`    | Only shows scrollbars when content actually overflows — recommended |

```css
div {
  overflow: hidden;   /* clips overflowing content */
  overflow: scroll;   /* always shows scrollbars */
  overflow: auto;     /* scrollbars only when needed */
}
```

### Controlling each axis separately

```css
div {
  overflow-x: auto;    /* horizontal scrollbar when needed */
  overflow-y: hidden;  /* clip vertical overflow */
}
```

### Common use case — text truncation with ellipsis

```css
p {
  width: 200px;
  white-space: nowrap;      /* prevents text from wrapping */
  overflow: hidden;         /* clips the overflowing text */
  text-overflow: ellipsis;  /* adds ... at the cutoff point */
}
```

All three properties are needed together for this to work.

---

## Display Property

The `display` property controls how an element behaves in the layout — whether it sits on its own line, inline with other content, or something else entirely.

### Block
```css
div {
  display: block;
}
```
- Takes up the full width of its parent
- Starts on a new line
- Respects width, height, margin, and padding on all sides
- Default for: `<div>`, `<p>`, `<h1>`–`<h6>`, `<section>`, `<ul>`, etc.

### Inline
```css
span {
  display: inline;
}
```
- Only as wide as its content
- Does not start on a new line — sits within text flow
- Width and height have no effect
- Top/bottom margin and padding have limited effect
- Default for: `<span>`, `<a>`, `<strong>`, `<em>`, `<img>`, etc.

### Inline-block
```css
div {
  display: inline-block;
}
```
- Sits inline with other elements (no forced new line)
- But respects width, height, margin, and padding like a block element
- Useful for things like nav buttons or icon+text combos sitting side by side

### None
```css
div {
  display: none;
}
```
Removes the element completely from the page — it takes up no space and is invisible. Different from `visibility: hidden`, which hides it but keeps the space.

### Flex and Grid
```css
div {
  display: flex;
  display: grid;
}
```
These turn the element into a **flex container** or **grid container** and change how its children are laid out. These are covered separately as they are large topics of their own.

### Quick comparison

| Value          | New line? | Respects width/height? |
|----------------|-----------|------------------------|
| `block`        | Yes       | Yes                    |
| `inline`       | No        | No                     |
| `inline-block` | No        | Yes                    |
| `none`         | —         | Removed from page      |

---

## Height and Width

```css
div {
  width: 400px;
  height: 200px;
}
```

### Units

| Unit  | What it means                                            |
|-------|----------------------------------------------------------|
| `px`  | Fixed pixels                                             |
| `%`   | Percentage of the parent element's width/height          |
| `vw`  | Percentage of the viewport (screen) width                |
| `vh`  | Percentage of the viewport (screen) height               |
| `rem` | Relative to the root font size                           |
| `em`  | Relative to the current element's font size              |
| `auto`| Browser calculates based on content and context          |

```css
div {
  width: 100%;       /* full width of parent */
  height: 100vh;     /* full height of the screen */
  width: 50vw;       /* half the screen width */
}
```

### Min and Max

```css
div {
  min-width: 200px;    /* never shrinks below this */
  max-width: 800px;    /* never grows beyond this */
  min-height: 100px;
  max-height: 500px;
}
```

Very useful for responsive layouts — the element can flex between a min and max as the screen size changes.

```css
/* Common pattern for readable content blocks */
.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
}
```

This makes the container full width on small screens but caps it at 1200px on large screens, and keeps it centered.

### Height and percentages

`height: 100%` only works if the parent has an explicit height defined. If the parent's height is `auto` (default), the percentage has nothing to calculate against and is ignored.

```css
html, body {
  height: 100%;    /* required for 100% height to work down the chain */
}
```

---

## Position

The `position` property controls how an element is placed in the page. It changes the element's relationship to the normal document flow.

### Static (default)
```css
div {
  position: static;
}
```
The element sits in its normal position in the flow. `top`, `right`, `bottom`, `left` have no effect here.

### Relative
```css
div {
  position: relative;
  top: 20px;
  left: 10px;
}
```
The element is moved *relative to where it would normally be*. The original space it occupied is still reserved — surrounding elements are not affected.

### Absolute
```css
div {
  position: absolute;
  top: 0;
  right: 0;
}
```
The element is removed from the normal flow and positioned relative to its **nearest ancestor that has a non-static position**. If no such ancestor exists, it positions relative to the page.

Common pattern — parent set to `relative`, child set to `absolute`:

```css
.parent {
  position: relative;
}

.child {
  position: absolute;
  bottom: 10px;
  right: 10px;
}
```

### Fixed
```css
div {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
}
```
Removed from the normal flow and positioned relative to the **viewport** (the browser window). Stays in place even when the page is scrolled. Used for sticky headers, floating buttons, cookie banners.

### Sticky
```css
div {
  position: sticky;
  top: 0;
}
```
Acts like `relative` until the user scrolls to a certain point, then it "sticks" and behaves like `fixed`. The `top` value defines where it sticks.

Common use case — a navigation bar that sticks to the top when you scroll past it.

### Z-index

When elements overlap, `z-index` controls which one appears on top.

```css
.modal {
  position: fixed;
  z-index: 1000;
}

.overlay {
  position: fixed;
  z-index: 999;
}
```

Higher `z-index` = on top. Only works on elements that have a `position` value other than `static`.

### Summary

| Value      | In flow? | Positioned relative to                        |
|------------|----------|-----------------------------------------------|
| `static`   | Yes      | Normal flow — offsets have no effect           |
| `relative` | Yes      | Its own normal position                        |
| `absolute` | No       | Nearest non-static ancestor                   |
| `fixed`    | No       | Viewport — stays during scroll                |
| `sticky`   | Yes/No   | Normal flow until scroll threshold, then fixed |

---

## Background Images

### Setting a background image
```css
div {
  background-image: url('image.jpg');
}
```

The image tiles (repeats) by default to fill the element.

### Background repeat
```css
div {
  background-repeat: repeat;      /* default — tiles in both directions */
  background-repeat: repeat-x;    /* tiles horizontally only */
  background-repeat: repeat-y;    /* tiles vertically only */
  background-repeat: no-repeat;   /* shows the image once, no tiling */
}
```

### Background size
```css
div {
  background-size: auto;          /* default — original image size */
  background-size: cover;         /* scales to cover the entire element, may crop */
  background-size: contain;       /* scales to fit inside the element, may leave gaps */
  background-size: 300px 200px;   /* explicit size */
  background-size: 100%;          /* full width of the element */
}
```

`cover` is the most commonly used — it fills the container without leaving gaps, cropping the image if needed.

### Background position
```css
div {
  background-position: center;           /* centered */
  background-position: top left;
  background-position: bottom right;
  background-position: 50% 50%;          /* same as center */
  background-position: 20px 40px;        /* x y from top-left */
}
```

### Background attachment
```css
div {
  background-attachment: scroll;   /* default — image scrolls with the page */
  background-attachment: fixed;    /* image stays fixed as you scroll — parallax effect */
}
```

### Shorthand
```css
div {
  background: url('image.jpg') no-repeat center / cover;
}
```

Order: `image` `repeat` `position` / `size`. You can include color too:

```css
div {
  background: #1a1a2e url('image.jpg') no-repeat center / cover;
}
```

### Multiple backgrounds
```css
div {
  background-image: url('overlay.png'), url('background.jpg');
}
```
The first image listed sits on top. Useful for layering a semi-transparent overlay over a photo.

### Gradient as background
```css
/* Linear gradient */
div {
  background-image: linear-gradient(to right, #ff6b6b, #4ecdc4);
}

/* Top to bottom */
div {
  background-image: linear-gradient(to bottom, #000, #fff);
}

/* At an angle */
div {
  background-image: linear-gradient(135deg, #667eea, #764ba2);
}

/* Radial gradient */
div {
  background-image: radial-gradient(circle, #ff6b6b, #4ecdc4);
}
```

Gradients are treated as images in CSS, so they go in `background-image`, not `background-color`.

---

## Combinators

Combinators define the relationship between selectors — they let you target elements based on where they sit in the HTML structure.

### Descendant combinator (space)
```css
div p {
  color: red;
}
```
Targets every `<p>` that is anywhere inside a `<div>` — doesn't matter how deeply nested.

```html
<div>
  <p>Targeted</p>         <!-- yes -->
  <section>
    <p>Also targeted</p>  <!-- yes — still a descendant -->
  </section>
</div>
<p>Not targeted</p>       <!-- no — outside the div -->
```

### Child combinator (`>`)
```css
div > p {
  color: red;
}
```
Targets only `<p>` elements that are **direct children** of a `<div>` — not deeper descendants.

```html
<div>
  <p>Targeted</p>           <!-- yes — direct child -->
  <section>
    <p>Not targeted</p>     <!-- no — child of section, not div -->
  </section>
</div>
```

### Adjacent sibling combinator (`+`)
```css
h1 + p {
  color: red;
}
```
Targets a `<p>` that **immediately follows** an `<h1>` and shares the same parent.

```html
<h1>Heading</h1>
<p>Targeted</p>      <!-- yes — immediately after h1 -->
<p>Not targeted</p>  <!-- no — not immediately after h1 -->
```

### General sibling combinator (`~`)
```css
h1 ~ p {
  color: red;
}
```
Targets **all** `<p>` siblings that come after an `<h1>` — not just the first one.

```html
<h1>Heading</h1>
<p>Targeted</p>    <!-- yes -->
<p>Targeted</p>    <!-- yes -->
<p>Targeted</p>    <!-- yes -->
```

### Quick reference

| Combinator | Syntax   | Targets                                          |
|------------|----------|--------------------------------------------------|
| Descendant | `A B`    | Any B inside A, at any depth                     |
| Child      | `A > B`  | B that is a direct child of A                    |
| Adjacent   | `A + B`  | B that immediately follows A (same parent)       |
| General    | `A ~ B`  | All B siblings that come after A (same parent)   |

---

## Pseudo-classes

Pseudo-classes target elements based on their **state** or **position** — things that can't be selected with a plain class or tag name.

They are written with a single colon `:`.

### User interaction states

```css
/* Link states */
a:link    { color: blue; }      /* unvisited link */
a:visited { color: purple; }    /* already visited */
a:hover   { color: red; }       /* mouse is over it */
a:active  { color: orange; }    /* being clicked */
```

When styling links, use this order — **L**o**V**e **HA**te — to avoid specificity conflicts.

```css
/* Hover — works on any element */
button:hover {
  background-color: darkblue;
}

/* Focus — element is selected/active (keyboard or click) */
input:focus {
  border-color: blue;
  outline: none;
}

/* Checked — checkbox or radio is selected */
input:checked {
  accent-color: green;
}

/* Disabled */
button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
```

### Structural pseudo-classes

These select elements based on their position in the DOM.

```css
/* First and last child */
li:first-child { font-weight: bold; }
li:last-child  { color: gray; }

/* Nth child — pick by number, keyword, or formula */
li:nth-child(1)        { }    /* first item */
li:nth-child(2)        { }    /* second item */
li:nth-child(odd)      { background: #f5f5f5; }
li:nth-child(even)     { background: #ffffff; }
li:nth-child(3n)       { }    /* every third item: 3, 6, 9... */

/* Only child — element has no siblings */
p:only-child { font-style: italic; }

/* First and last of their type */
p:first-of-type { font-size: 1.2em; }
p:last-of-type  { margin-bottom: 0; }

/* Nth of type */
p:nth-of-type(2) { color: gray; }
```

### Other useful pseudo-classes

```css
/* Negation — everything except .special */
p:not(.special) {
  color: #333;
}

/* Empty element — no children or text */
div:empty {
  display: none;
}

/* Required and optional form fields */
input:required { border-color: red; }
input:optional { border-color: gray; }

/* Valid and invalid input values */
input:valid   { border-color: green; }
input:invalid { border-color: red; }
```

---

## Pseudo-elements

Pseudo-elements target a **specific part** of an element rather than the whole thing, or let you insert content without touching the HTML.

They are written with a double colon `::`.

### `::before` and `::after`

Insert generated content before or after an element's actual content. They require the `content` property — even if it's empty.

```css
h1::before {
  content: "🔥 ";
}

h1::after {
  content: " ✅";
}
```

```html
<h1>Title</h1>
<!-- Renders as: 🔥 Title ✅ -->
```

They are used heavily for decorative elements, icons, and the clearfix hack — all without adding extra HTML.

```css
/* Clearfix using ::after */
.clearfix::after {
  content: "";
  display: block;
  clear: both;
}

/* Decorative line under a heading */
h2::after {
  content: "";
  display: block;
  width: 50px;
  height: 3px;
  background-color: royalblue;
  margin-top: 6px;
}
```

### `::first-line`

Styles only the first line of a block of text.

```css
p::first-line {
  font-weight: bold;
  font-size: 1.1em;
}
```

The "first line" adjusts dynamically based on the container width.

### `::first-letter`

Styles only the first character — classic drop cap effect.

```css
p::first-letter {
  font-size: 3em;
  font-weight: bold;
  float: left;
  margin-right: 4px;
}
```

### `::selection`

Styles the text a user has highlighted/selected.

```css
::selection {
  background-color: royalblue;
  color: white;
}
```

### `::placeholder`

Styles the placeholder text inside form inputs.

```css
input::placeholder {
  color: #aaa;
  font-style: italic;
}
```

### Quick reference

| Pseudo-element    | What it targets                             |
|-------------------|---------------------------------------------|
| `::before`        | Inserts content before the element's content |
| `::after`         | Inserts content after the element's content  |
| `::first-line`    | The first rendered line of a text block      |
| `::first-letter`  | The first character of a text block          |
| `::selection`     | Text the user has highlighted               |
| `::placeholder`   | Placeholder text in inputs                  |

---

## Pagination

Pagination is a row of links/buttons used to navigate between pages — common on blogs, search results, and product listings.

Here is a clean, commonly used pattern built with an unordered list:

### HTML
```html
<nav aria-label="Pagination">
  <ul class="pagination">
    <li><a href="#">&laquo;</a></li>   <!-- « previous -->
    <li><a href="#" class="active">1</a></li>
    <li><a href="#">2</a></li>
    <li><a href="#">3</a></li>
    <li><a href="#">4</a></li>
    <li><a href="#">5</a></li>
    <li><a href="#">&raquo;</a></li>   <!-- » next -->
  </ul>
</nav>
```

### CSS
```css
.pagination {
  list-style: none;
  display: flex;
  gap: 4px;
  padding: 0;
  margin: 0;
}

.pagination a {
  display: block;
  padding: 8px 14px;
  text-decoration: none;
  color: #333;
  border: 1px solid #ddd;
  border-radius: 4px;
  transition: background-color 0.2s;
}

.pagination a:hover {
  background-color: #f0f0f0;
}

.pagination a.active {
  background-color: royalblue;
  color: white;
  border-color: royalblue;
}
```

- `&laquo;` and `&raquo;` are HTML entities for the « and » characters — used as previous/next arrows.
- The `.active` class marks the current page.
- `transition` adds a smooth hover effect.
- Using `<nav>` with `aria-label` makes it accessible to screen readers.

---

## Dropdown Menu

A dropdown menu shows a hidden submenu when the user hovers over (or clicks) a parent item. The core technique uses `display: none` toggled to `display: block` on `:hover`.

### HTML
```html
<nav>
  <ul class="nav-menu">
    <li><a href="#">Home</a></li>

    <li class="dropdown">
      <a href="#">Services</a>
      <ul class="dropdown-menu">
        <li><a href="#">Web Design</a></li>
        <li><a href="#">Development</a></li>
        <li><a href="#">SEO</a></li>
      </ul>
    </li>

    <li><a href="#">About</a></li>
    <li><a href="#">Contact</a></li>
  </ul>
</nav>
```

### CSS
```css
/* Base nav */
.nav-menu {
  list-style: none;
  display: flex;
  gap: 0;
  padding: 0;
  margin: 0;
  background-color: #333;
}

.nav-menu > li > a {
  display: block;
  padding: 14px 20px;
  color: white;
  text-decoration: none;
}

.nav-menu > li > a:hover {
  background-color: #555;
}

/* Dropdown wrapper */
.dropdown {
  position: relative;   /* anchor for the absolute dropdown */
}

/* The hidden submenu */
.dropdown-menu {
  list-style: none;
  padding: 0;
  margin: 0;
  position: absolute;
  top: 100%;            /* sits right below the parent item */
  left: 0;
  background-color: #444;
  min-width: 180px;
  display: none;        /* hidden by default */
  z-index: 100;
}

.dropdown-menu li a {
  display: block;
  padding: 12px 20px;
  color: white;
  text-decoration: none;
}

.dropdown-menu li a:hover {
  background-color: #666;
}

/* Show the dropdown on hover */
.dropdown:hover .dropdown-menu {
  display: block;
}
```

### How it works

1. `.dropdown` is set to `position: relative` so the submenu can be positioned against it.
2. `.dropdown-menu` is set to `position: absolute; top: 100%` — this places it directly below the parent item.
3. It starts with `display: none` — invisible and takes up no space.
4. `.dropdown:hover .dropdown-menu` uses the descendant combinator to reveal it when the parent is hovered.
5. `z-index: 100` keeps it above other page content.
