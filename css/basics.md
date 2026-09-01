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
