# CSS — Selectors, Properties, and Styling

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
  color: #ff0000;         /* red */
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
  color: rgb(255, 0, 0);    /* red */
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
Stands for **Hue, Saturation, Lightness**. More intuitive for adjusting shades — just tweak the lightness or saturation.

### Where colors are used
```css
p {
  color: #333;                 /* text color */
  background-color: #f5f5f5;  /* background */
  border-color: #ccc;          /* border */
  outline-color: blue;         /* outline */
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
Multiple fonts separated by commas — called a **font stack**. The browser uses the first one it has installed. The last value should always be a generic fallback: `sans-serif`, `serif`, or `monospace`.

### Font size
```css
p {
  font-size: 16px;    /* pixels — fixed size */
  font-size: 1rem;    /* relative to root element font size */
  font-size: 1.2em;   /* relative to the parent element's font size */
  font-size: 120%;    /* percentage of the parent font size */
}
```
`px` is the most straightforward. `rem` is widely used in real projects because it scales well across screen sizes and user preferences.

### Font weight
```css
p {
  font-weight: normal;  /* default */
  font-weight: bold;
  font-weight: 400;     /* same as normal */
  font-weight: 700;     /* same as bold */
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
  line-height: 1.6;   /* 1.6x the font size — unitless is recommended */
  line-height: 24px;
}
```
Controls vertical space between lines. A value around `1.5`–`1.6` is comfortable for body text.

### Letter spacing
```css
p {
  letter-spacing: 2px;   /* space between characters */
}
```

### Google Fonts
To use a font not installed on the user's system, load one from Google Fonts.

```html
<!-- In your HTML <head> -->
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet" />
```
```css
body {
  font-family: 'Roboto', sans-serif;
}
```
Go to [fonts.google.com](https://fonts.google.com), pick a font, copy the `<link>` tag, and use the font name in your CSS.

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
border-style: solid;    /* continuous line */
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

Or with longhand properties:
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
  border-radius: 50%;       /* circle if width == height */
  border-radius: 4px 12px;  /* top-left/bottom-right, top-right/bottom-left */
}
```

### Outline
Sits outside the element and does not affect layout — takes up no space.

```css
input:focus {
  outline: 2px solid blue;
  outline-offset: 3px;   /* gap between element and outline */
}
```

---

## Margin and Padding

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
padding: 20px;              /* all four sides */
padding: 10px 20px;         /* top/bottom, left/right */
padding: 10px 20px 15px;    /* top, left/right, bottom */
padding: 10px 20px 15px 5px; /* top, right, bottom, left — clockwise */
```
The same pattern applies to `margin`.

### Individual sides
```css
div {
  margin-top: 10px;
  margin-right: 20px;
  margin-bottom: 10px;
  margin-left: 20px;
}
```

### Auto margin — centering
```css
div {
  width: 600px;
  margin: 0 auto;   /* 0 top/bottom, auto left/right — centers horizontally */
}
```
Requires a fixed width to work.

### Collapsing margins
Vertical margins between two block elements collapse — only the larger of the two is used, not the sum.

```css
/* These two paragraphs will have 20px between them, not 30px */
p { margin-bottom: 20px; }
p { margin-top: 10px; }
```
Only happens with vertical margins, never horizontal.

### box-sizing
By default, `width` and `height` only apply to the content area. Padding and border are added on top.

```css
/* Apply universally — standard practice in every project */
* {
  box-sizing: border-box;
}
```
With `border-box`, padding and border are included *inside* the declared width and height.

---

## Float

Float was designed for wrapping text around images — the same way magazines wrap text around photos.

```css
img {
  float: left;    /* image floats left, text wraps around the right */
  float: right;   /* image floats right, text wraps around the left */
  float: none;    /* default */
}
```

```html
<img src="photo.jpg" alt="A photo" style="float: left; margin-right: 16px;" />
<p>This text will wrap around the image on the right side.</p>
```

### The float problem — clearing
Floated elements are removed from the normal flow. A parent container won't expand to wrap floated children — it collapses.

```css
/* Fix: clearfix on the parent */
.clearfix::after {
  content: "";
  display: block;
  clear: both;
}
```

Or clear on a specific element:
```css
.clear {
  clear: both;    /* drops below all floated elements */
  clear: left;
  clear: right;
}
```

### Float today
Float is still used for wrapping text around images. For page layout, use **Flexbox** or **CSS Grid** instead — they are purpose-built and don't have clearing problems.

---

## Overflow

Controls what happens when content is too large to fit inside its container.

| Value     | What it does                                                        |
|-----------|---------------------------------------------------------------------|
| `visible` | Default. Content spills outside the element                         |
| `hidden`  | Overflow is clipped — extra content is invisible                    |
| `scroll`  | Always shows scrollbars, whether content overflows or not           |
| `auto`    | Only shows scrollbars when content actually overflows — recommended |

```css
div {
  overflow: hidden;
  overflow: scroll;
  overflow: auto;
}
```

### Per-axis control
```css
div {
  overflow-x: auto;
  overflow-y: hidden;
}
```

### Text truncation with ellipsis
```css
p {
  width: 200px;
  white-space: nowrap;      /* prevent text from wrapping */
  overflow: hidden;         /* clip the overflow */
  text-overflow: ellipsis;  /* add ... at the cutoff */
}
```
All three properties are needed together.

---

## Display Property

Controls how an element behaves in the layout.

### Block
```css
div { display: block; }
```
- Full width of its parent, starts on a new line
- Respects width, height, margin, padding on all sides
- Default for: `<div>`, `<p>`, `<h1>`–`<h6>`, `<section>`, `<ul>`

### Inline
```css
span { display: inline; }
```
- Only as wide as its content, stays in text flow
- Width and height have no effect
- Default for: `<span>`, `<a>`, `<strong>`, `<em>`

### Inline-block
```css
div { display: inline-block; }
```
- Sits inline but respects width, height, margin, padding like a block
- Useful for nav buttons or icon+text combos side by side

### None
```css
div { display: none; }
```
Removes the element completely — no space, not visible. Different from `visibility: hidden` which hides it but keeps the space.

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

| Unit   | What it means                                   |
|--------|-------------------------------------------------|
| `px`   | Fixed pixels                                    |
| `%`    | Percentage of the parent element                |
| `vw`   | Percentage of the viewport width                |
| `vh`   | Percentage of the viewport height               |
| `rem`  | Relative to the root font size                  |
| `em`   | Relative to the current element's font size     |
| `auto` | Browser calculates based on content and context |

### Min and Max
```css
div {
  min-width: 200px;   /* never shrinks below this */
  max-width: 800px;   /* never grows beyond this */
  min-height: 100px;
  max-height: 500px;
}
```

Common centered container pattern:
```css
.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
}
```
Full width on small screens, capped at 1200px on large screens, always centered.

### Height and percentages
`height: 100%` only works if the parent has an explicit height. If the parent is `auto`, the percentage is ignored.

```css
html, body {
  height: 100%;   /* required for percentage heights to work down the chain */
}
```

---

## Position

Controls how an element is placed in the page relative to the normal document flow.

### Static (default)
```css
div { position: static; }
```
Normal flow. `top`, `right`, `bottom`, `left` have no effect.

### Relative
```css
div {
  position: relative;
  top: 20px;
  left: 10px;
}
```
Moved relative to where it would normally be. Original space is still reserved.

### Absolute
```css
div {
  position: absolute;
  top: 0;
  right: 0;
}
```
Removed from flow. Positioned relative to the nearest ancestor with a non-static position. If none exists, positions relative to the page.

Common pattern:
```css
.parent { position: relative; }
.child  { position: absolute; bottom: 10px; right: 10px; }
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
Removed from flow. Positioned relative to the viewport — stays in place on scroll. Used for sticky headers and floating buttons.

### Sticky
```css
div {
  position: sticky;
  top: 0;
}
```
Acts like `relative` until the user scrolls to the threshold, then sticks like `fixed`. Common for navbars.

### Z-index
When elements overlap, `z-index` controls which is on top. Only works on non-static elements.

```css
.modal   { position: fixed; z-index: 1000; }
.overlay { position: fixed; z-index: 999; }
```

### Summary

| Value      | In flow? | Positioned relative to                         |
|------------|----------|------------------------------------------------|
| `static`   | Yes      | Normal flow — offsets have no effect            |
| `relative` | Yes      | Its own normal position                         |
| `absolute` | No       | Nearest non-static ancestor                    |
| `fixed`    | No       | Viewport — stays during scroll                 |
| `sticky`   | Yes/No   | Normal flow until scroll threshold, then fixed  |

---

## Background Images

```css
div {
  background-image: url('image.jpg');
}
```
The image tiles by default to fill the element.

### Background repeat
```css
background-repeat: repeat;      /* default — tiles both directions */
background-repeat: repeat-x;    /* horizontal only */
background-repeat: repeat-y;    /* vertical only */
background-repeat: no-repeat;   /* shows once, no tiling */
```

### Background size
```css
background-size: auto;          /* original image size */
background-size: cover;         /* fills the element, may crop */
background-size: contain;       /* fits inside, may leave gaps */
background-size: 300px 200px;
```
`cover` is the most common — fills without gaps.

### Background position
```css
background-position: center;
background-position: top left;
background-position: 50% 50%;
background-position: 20px 40px;
```

### Background attachment
```css
background-attachment: scroll;  /* default — scrolls with page */
background-attachment: fixed;   /* stays fixed — parallax effect */
```

### Shorthand
```css
div {
  background: #1a1a2e url('image.jpg') no-repeat center / cover;
}
```
Order: `color` `image` `repeat` `position` / `size`.

### Multiple backgrounds
```css
div {
  background-image: url('overlay.png'), url('background.jpg');
}
```
First image sits on top. Good for layering a transparent overlay over a photo.

### Gradients
```css
/* Linear */
background-image: linear-gradient(to right, #ff6b6b, #4ecdc4);
background-image: linear-gradient(135deg, #667eea, #764ba2);

/* Radial */
background-image: radial-gradient(circle, #ff6b6b, #4ecdc4);
```
Gradients go in `background-image`, not `background-color`.

---

## Combinators

Define the relationship between selectors — target elements based on where they sit in the HTML structure.

### Descendant (space)
```css
div p { color: red; }
```
Every `<p>` anywhere inside a `<div>`, no matter how deeply nested.

### Child (`>`)
```css
div > p { color: red; }
```
Only `<p>` elements that are direct children of a `<div>`.

### Adjacent sibling (`+`)
```css
h1 + p { color: red; }
```
A `<p>` that immediately follows an `<h1>` and shares the same parent.

### General sibling (`~`)
```css
h1 ~ p { color: red; }
```
All `<p>` siblings that come after an `<h1>`.

### Quick reference

| Combinator | Syntax  | Targets                                        |
|------------|---------|------------------------------------------------|
| Descendant | `A B`   | Any B inside A, at any depth                   |
| Child      | `A > B` | B that is a direct child of A                  |
| Adjacent   | `A + B` | B that immediately follows A (same parent)     |
| General    | `A ~ B` | All B siblings that come after A (same parent) |

---

## Pseudo-classes

Target elements based on their **state** or **position**. Written with a single colon `:`.

### Interaction states
```css
a:link    { color: blue; }     /* unvisited */
a:visited { color: purple; }   /* visited */
a:hover   { color: red; }      /* mouse over */
a:active  { color: orange; }   /* being clicked */
```
Use this order for links — **L**o**V**e **HA**te — to avoid specificity conflicts.

```css
button:hover   { background-color: darkblue; }
input:focus    { border-color: blue; }
input:checked  { accent-color: green; }
button:disabled { opacity: 0.5; cursor: not-allowed; }
```

### Structural pseudo-classes
```css
li:first-child        { font-weight: bold; }
li:last-child         { color: gray; }
li:nth-child(odd)     { background: #f5f5f5; }
li:nth-child(even)    { background: #ffffff; }
li:nth-child(3n)      { }   /* every third: 3, 6, 9... */
p:only-child          { font-style: italic; }
p:first-of-type       { font-size: 1.2em; }
p:last-of-type        { margin-bottom: 0; }
```

### Other useful ones
```css
p:not(.special)  { color: #333; }      /* everything except .special */
div:empty        { display: none; }    /* element with no children or text */
input:required   { border-color: red; }
input:valid      { border-color: green; }
input:invalid    { border-color: red; }
```

---

## Pseudo-elements

Target a **specific part** of an element or insert content without changing HTML. Written with double colon `::`.

### `::before` and `::after`
Insert generated content before or after an element's content. The `content` property is required.

```css
h1::before { content: "🔥 "; }
h1::after  { content: " ✅"; }

/* Decorative underline */
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
```css
p::first-line {
  font-weight: bold;
  font-size: 1.1em;
}
```
Styles only the first rendered line. Adjusts dynamically with container width.

### `::first-letter`
```css
p::first-letter {
  font-size: 3em;
  font-weight: bold;
  float: left;
  margin-right: 4px;
}
```
Classic drop cap effect.

### `::selection`
```css
::selection {
  background-color: royalblue;
  color: white;
}
```
Styles text the user has highlighted.

### `::placeholder`
```css
input::placeholder {
  color: #aaa;
  font-style: italic;
}
```

### Quick reference

| Pseudo-element   | What it targets                              |
|------------------|----------------------------------------------|
| `::before`       | Inserts content before the element's content |
| `::after`        | Inserts content after the element's content  |
| `::first-line`   | The first rendered line of a text block      |
| `::first-letter` | The first character of a text block          |
| `::selection`    | Text the user has highlighted                |
| `::placeholder`  | Placeholder text in inputs                   |
