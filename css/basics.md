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

---

## Navigation Bar

A navbar is the horizontal (or vertical) bar that holds your site's main links. It is built from a `<nav>` and an `<ul>` — the dropdown menu section showed a basic version. Here is a more complete, real-world horizontal navbar.

### HTML
```html
<nav class="navbar">
  <div class="nav-logo">
    <a href="#">MySite</a>
  </div>
  <ul class="nav-links">
    <li><a href="#" class="active">Home</a></li>
    <li><a href="#">About</a></li>
    <li><a href="#">Services</a></li>
    <li><a href="#">Contact</a></li>
  </ul>
</nav>
```

### CSS
```css
.navbar {
  display: flex;
  justify-content: space-between;  /* logo on left, links on right */
  align-items: center;
  background-color: #1a1a2e;
  padding: 0 40px;
  height: 64px;
}

.nav-logo a {
  color: white;
  text-decoration: none;
  font-size: 1.4rem;
  font-weight: bold;
}

.nav-links {
  list-style: none;
  display: flex;
  gap: 8px;
  margin: 0;
  padding: 0;
}

.nav-links a {
  display: block;
  color: #ccc;
  text-decoration: none;
  padding: 8px 16px;
  border-radius: 4px;
  transition: background-color 0.2s, color 0.2s;
}

.nav-links a:hover {
  background-color: #ffffff20;  /* white at low opacity */
  color: white;
}

.nav-links a.active {
  background-color: royalblue;
  color: white;
}
```

### Sticky navbar

To make the navbar stick to the top when scrolling:

```css
.navbar {
  position: sticky;
  top: 0;
  z-index: 1000;
}
```

---

## Website Layout

A standard webpage is built from a few key sections stacked vertically. Here is the full structure using semantic HTML and CSS.

### HTML
```html
<body>

  <header class="site-header">
    <nav class="navbar"><!-- navbar here --></nav>
  </header>

  <main class="site-main">

    <section class="hero">
      <h1>Welcome to My Site</h1>
      <p>A short tagline goes here.</p>
      <a href="#" class="btn">Get Started</a>
    </section>

    <section class="content-section">
      <div class="container">
        <h2>About</h2>
        <p>Content goes here.</p>
      </div>
    </section>

    <section class="cards-section">
      <div class="container">
        <div class="card-grid">
          <div class="card">Card 1</div>
          <div class="card">Card 2</div>
          <div class="card">Card 3</div>
        </div>
      </div>
    </section>

  </main>

  <footer class="site-footer">
    <p>&copy; 2026 MySite. All rights reserved.</p>
  </footer>

</body>
```

### CSS
```css
/* Reset and base */
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, sans-serif;
  color: #333;
  line-height: 1.6;
}

/* Centered container — max width with auto margin */
.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

/* Hero section */
.hero {
  background-color: #1a1a2e;
  color: white;
  text-align: center;
  padding: 100px 20px;
}

.hero h1 {
  font-size: 3rem;
  margin-bottom: 16px;
}

.hero p {
  font-size: 1.2rem;
  margin-bottom: 32px;
  color: #ccc;
}

.btn {
  display: inline-block;
  padding: 14px 32px;
  background-color: royalblue;
  color: white;
  text-decoration: none;
  border-radius: 6px;
  transition: background-color 0.2s;
}

.btn:hover {
  background-color: #2541b2;
}

/* Content section */
.content-section {
  padding: 80px 0;
}

/* Card grid */
.cards-section {
  padding: 80px 0;
  background-color: #f5f5f5;
}

.card-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
}

.card {
  background-color: white;
  padding: 32px;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
}

/* Footer */
.site-footer {
  background-color: #1a1a2e;
  color: #aaa;
  text-align: center;
  padding: 32px 20px;
}
```

This layout follows a pattern used in nearly every real website — a centered `.container` inside full-width sections. The section takes up the full viewport width (for background colors), but the content inside stays readable with a max-width.

---

## Image Gallery

A gallery lays out images in a grid. CSS Grid makes this clean and easy.

### HTML
```html
<div class="gallery">
  <img src="img1.jpg" alt="Photo 1" />
  <img src="img2.jpg" alt="Photo 2" />
  <img src="img3.jpg" alt="Photo 3" />
  <img src="img4.jpg" alt="Photo 4" />
  <img src="img5.jpg" alt="Photo 5" />
  <img src="img6.jpg" alt="Photo 6" />
</div>
```

### CSS — uniform grid
```css
.gallery {
  display: grid;
  grid-template-columns: repeat(3, 1fr);  /* 3 equal columns */
  gap: 12px;
}

.gallery img {
  width: 100%;           /* fill the column */
  height: 250px;
  object-fit: cover;     /* crop to fill without stretching */
  border-radius: 6px;
  display: block;
}
```

`object-fit: cover` is the key here — it makes every image fill its cell uniformly, cropping if needed, instead of distorting.

### Hover effect
```css
.gallery img {
  transition: transform 0.3s, opacity 0.3s;
}

.gallery img:hover {
  transform: scale(1.03);
  opacity: 0.85;
}
```

### Responsive gallery — auto-fit
```css
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 12px;
}
```

`auto-fit` with `minmax` automatically adjusts the number of columns based on available space — no media queries needed. On a wide screen you get many columns, on mobile you get fewer.

---

## Icons

The most common way to add icons to a webpage is with an icon library. **Font Awesome** is the most widely used.

### Setup — add to your HTML `<head>`
```html
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" />
```

Or use the CDN from [fontawesome.com](https://fontawesome.com).

### Using icons
```html
<i class="fa-solid fa-house"></i>        <!-- house icon -->
<i class="fa-solid fa-user"></i>         <!-- user icon -->
<i class="fa-solid fa-magnifying-glass"></i>  <!-- search icon -->
<i class="fa-brands fa-github"></i>      <!-- GitHub logo -->
<i class="fa-brands fa-instagram"></i>   <!-- Instagram logo -->
```

Icons are inserted with an `<i>` tag and the appropriate classes. They scale with font size and inherit color from their parent.

### Sizing icons
```html
<i class="fa-solid fa-house fa-sm"></i>   <!-- small -->
<i class="fa-solid fa-house fa-lg"></i>   <!-- large -->
<i class="fa-solid fa-house fa-2x"></i>   <!-- 2x size -->
<i class="fa-solid fa-house fa-3x"></i>   <!-- 3x size -->
```

Or use CSS directly:
```css
i {
  font-size: 24px;
  color: royalblue;
}
```

### Icon with text
```html
<button>
  <i class="fa-solid fa-envelope"></i> Send Email
</button>
```

### Icons as bullet points
```html
<ul style="list-style: none; padding: 0;">
  <li><i class="fa-solid fa-check" style="color: green;"></i> Feature one</li>
  <li><i class="fa-solid fa-check" style="color: green;"></i> Feature two</li>
</ul>
```

### Accessibility
Icons that are purely decorative should be hidden from screen readers:
```html
<i class="fa-solid fa-house" aria-hidden="true"></i>
```

If the icon carries meaning on its own, add a label:
```html
<i class="fa-solid fa-house" aria-label="Home"></i>
```

---

## Flexbox

Flexbox is a layout model that arranges items in a row or column and gives you powerful control over alignment, spacing, and sizing. It works on two levels — the **container** and the **items** inside it.

You turn an element into a flex container with:
```css
.container {
  display: flex;
}
```
All direct children of that element become **flex items**.

---

### Container properties

#### `flex-direction` — which direction items flow
```css
.container {
  flex-direction: row;            /* default — left to right */
  flex-direction: row-reverse;    /* right to left */
  flex-direction: column;         /* top to bottom */
  flex-direction: column-reverse; /* bottom to top */
}
```

#### `justify-content` — alignment along the main axis
```css
.container {
  justify-content: flex-start;    /* default — items at the start */
  justify-content: flex-end;      /* items at the end */
  justify-content: center;        /* items centered */
  justify-content: space-between; /* equal space between items, none at edges */
  justify-content: space-around;  /* equal space around each item */
  justify-content: space-evenly;  /* equal space between items and edges */
}
```

#### `align-items` — alignment along the cross axis
```css
.container {
  align-items: stretch;      /* default — items stretch to fill height */
  align-items: flex-start;   /* items align to the top */
  align-items: flex-end;     /* items align to the bottom */
  align-items: center;       /* items centered vertically */
  align-items: baseline;     /* items align by their text baseline */
}
```

#### `flex-wrap` — whether items wrap to a new line
```css
.container {
  flex-wrap: nowrap;    /* default — all items stay on one line, may overflow */
  flex-wrap: wrap;      /* items wrap to next line when they don't fit */
}
```

#### `gap` — space between items
```css
.container {
  gap: 16px;          /* same gap in both directions */
  gap: 16px 24px;     /* row-gap column-gap */
}
```

---

### Item properties

#### `flex-grow` — how much an item grows to fill space
```css
.item {
  flex-grow: 0;   /* default — does not grow */
  flex-grow: 1;   /* grows to fill available space */
}
```

If all items have `flex-grow: 1`, they share the space equally. If one has `flex-grow: 2`, it takes twice the share.

#### `flex-shrink` — how much an item shrinks when space is tight
```css
.item {
  flex-shrink: 1;   /* default — can shrink */
  flex-shrink: 0;   /* will not shrink — stays at its set size */
}
```

#### `flex-basis` — the starting size before growing/shrinking
```css
.item {
  flex-basis: auto;    /* default — uses the item's width/height */
  flex-basis: 200px;   /* starts at 200px then grows/shrinks from there */
}
```

#### `flex` shorthand — grow, shrink, basis together
```css
.item {
  flex: 1;              /* flex-grow: 1, shrink: 1, basis: 0 */
  flex: 1 1 200px;      /* grow: 1, shrink: 1, basis: 200px */
  flex: 0 0 300px;      /* fixed width — no growing or shrinking */
}
```

`flex: 1` is the most common shorthand — it makes all items share space equally.

#### `align-self` — override align-items for a single item
```css
.item {
  align-self: flex-start;
  align-self: flex-end;
  align-self: center;
  align-self: stretch;
}
```

#### `order` — change visual order without changing HTML
```css
.item-a { order: 2; }
.item-b { order: 1; }   /* appears first visually */
.item-c { order: 3; }
```

Default order is `0`. Lower values appear first.

---

### Common patterns

#### Centering something perfectly
```css
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
```
This is the easiest way to center anything — horizontally and vertically — in CSS.

#### Equal-width columns
```css
.container {
  display: flex;
  gap: 24px;
}

.column {
  flex: 1;   /* all columns share space equally */
}
```

#### Navbar with logo left, links right
```css
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```

#### Push last item to the far end
```css
.container {
  display: flex;
}

.last-item {
  margin-left: auto;   /* pushes itself to the right */
}
```

---

## Transformations

The `transform` property lets you visually move, rotate, scale, or skew an element — without affecting the layout of surrounding elements. The element still occupies its original space in the document.

### Translate — move
```css
div {
  transform: translateX(50px);    /* move right 50px */
  transform: translateY(-20px);   /* move up 20px */
  transform: translate(50px, -20px);  /* move right and up together */
}
```

Negative values move left/up. Positive move right/down.

### Scale — resize
```css
div {
  transform: scale(1.5);      /* 1.5x bigger in both directions */
  transform: scaleX(2);       /* stretch horizontally only */
  transform: scaleY(0.5);     /* squish vertically only */
  transform: scale(1.2, 0.8); /* different x and y */
}
```

`scale(1)` is the original size. `scale(2)` is double. `scale(0.5)` is half.

### Rotate
```css
div {
  transform: rotate(45deg);    /* rotate 45 degrees clockwise */
  transform: rotate(-90deg);   /* rotate 90 degrees counter-clockwise */
}
```

### Skew — slant
```css
div {
  transform: skewX(20deg);    /* slant along the x axis */
  transform: skewY(10deg);    /* slant along the y axis */
  transform: skew(20deg, 10deg);
}
```

### Combining multiple transforms
```css
div {
  transform: translate(50px, 20px) rotate(45deg) scale(1.2);
}
```

List them space-separated on the same `transform` property. They are applied right to left — so in this example scale happens first, then rotate, then translate.

### Transform origin

By default, transformations happen from the center of the element. You can change that:

```css
div {
  transform-origin: top left;     /* rotate/scale from the top-left corner */
  transform-origin: bottom center;
  transform-origin: 50% 50%;      /* default — center */
  transform-origin: 0 0;          /* top-left corner */
}
```

### 3D transforms

```css
div {
  transform: rotateX(45deg);   /* tilt towards/away on x axis */
  transform: rotateY(45deg);   /* spin on y axis */
  transform: rotateZ(45deg);   /* same as rotate() */
  transform: translateZ(50px); /* move towards/away from viewer */
}
```

For 3D to look correct, add perspective to the parent:

```css
.parent {
  perspective: 800px;   /* lower = more dramatic 3D effect */
}
```

### Transforms with transition

Transforms are most useful when combined with `transition` for smooth effects:

```css
.card {
  transition: transform 0.3s ease;
}

.card:hover {
  transform: translateY(-8px) scale(1.02);  /* lift and slightly enlarge on hover */
}
```

---

## Animations

CSS animations let elements animate automatically — no hover or interaction required. They are built from two parts: the `@keyframes` rule and the `animation` property.

### @keyframes — define the animation

```css
@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
```

`from` is the start state, `to` is the end state. You can also use percentages for more control:

```css
@keyframes bounce {
  0%   { transform: translateY(0); }
  50%  { transform: translateY(-30px); }
  100% { transform: translateY(0); }
}
```

```css
@keyframes colorShift {
  0%   { background-color: red; }
  33%  { background-color: blue; }
  66%  { background-color: green; }
  100% { background-color: red; }
}
```

### animation property — apply it to an element

```css
div {
  animation: fadeIn 1s ease forwards;
}
```

This is shorthand. The individual properties are:

```css
div {
  animation-name: fadeIn;           /* name of the @keyframes */
  animation-duration: 1s;           /* how long one cycle takes */
  animation-timing-function: ease;  /* speed curve */
  animation-delay: 0.5s;            /* wait before starting */
  animation-iteration-count: 1;     /* how many times to run */
  animation-direction: normal;      /* direction of playback */
  animation-fill-mode: forwards;    /* what state to hold after it ends */
}
```

### Timing functions

Controls the pace of the animation — how it accelerates and decelerates.

| Value          | Description                                           |
|----------------|-------------------------------------------------------|
| `ease`         | Default. Slow start, fast middle, slow end            |
| `linear`       | Constant speed throughout                             |
| `ease-in`      | Starts slow, ends fast                                |
| `ease-out`     | Starts fast, ends slow                                |
| `ease-in-out`  | Slow start and slow end                               |
| `cubic-bezier` | Custom curve — full control                           |

```css
animation-timing-function: cubic-bezier(0.25, 0.1, 0.25, 1);
```

### Iteration count

```css
animation-iteration-count: 1;         /* plays once — default */
animation-iteration-count: 3;         /* plays 3 times */
animation-iteration-count: infinite;  /* loops forever */
```

### Direction

```css
animation-direction: normal;            /* default — forward each time */
animation-direction: reverse;           /* plays backwards */
animation-direction: alternate;         /* forward, then backward, then forward... */
animation-direction: alternate-reverse; /* backward, then forward, then backward... */
```

### Fill mode — what happens before and after

```css
animation-fill-mode: none;       /* default — element snaps back after animation */
animation-fill-mode: forwards;   /* holds the final keyframe state after it ends */
animation-fill-mode: backwards;  /* applies the first keyframe during the delay */
animation-fill-mode: both;       /* applies both forwards and backwards */
```

`forwards` is the most commonly used — it prevents the element from snapping back to its original state after the animation completes.

### Multiple animations

```css
div {
  animation: fadeIn 1s ease forwards, bounce 0.5s ease 1s infinite;
}
```

Separate multiple animations with a comma. Each runs independently.

### Pausing an animation

```css
div {
  animation-play-state: running;  /* default */
  animation-play-state: paused;
}

div:hover {
  animation-play-state: paused;   /* pause on hover */
}
```

---

### Transition vs Animation

These two are often confused. Here is the difference:

| | Transition | Animation |
|---|---|---|
| Trigger | Needs a state change (hover, focus, class added) | Runs automatically |
| Keyframes | No — just start and end | Yes — full control over every step |
| Looping | No | Yes — `infinite` |
| Use case | Hover effects, UI feedback | Loading spinners, intros, continuous motion |

```css
/* Transition — reacts to hover */
.btn {
  background-color: royalblue;
  transition: background-color 0.2s ease;
}
.btn:hover {
  background-color: darkblue;
}

/* Animation — plays on its own */
.spinner {
  animation: spin 1s linear infinite;
}
@keyframes spin {
  from { transform: rotate(0deg); }
  to   { transform: rotate(360deg); }
}
```

### Practical examples

#### Fade in on load
```css
.hero {
  animation: fadeIn 1s ease forwards;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to   { opacity: 1; transform: translateY(0); }
}
```

#### Pulse effect
```css
.badge {
  animation: pulse 1.5s ease-in-out infinite;
}

@keyframes pulse {
  0%, 100% { transform: scale(1); }
  50%       { transform: scale(1.1); }
}
```

#### Loading spinner
```css
.spinner {
  width: 40px;
  height: 40px;
  border: 4px solid #ddd;
  border-top-color: royalblue;
  border-radius: 50%;
  animation: spin 0.8s linear infinite;
}

@keyframes spin {
  to { transform: rotate(360deg); }
}
```
