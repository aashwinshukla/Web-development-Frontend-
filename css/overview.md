# CSS — Overview

## What is CSS?

CSS stands for **Cascading Style Sheets**. It is the language used to control how HTML elements look on a page — things like color, font, size, spacing, layout, and animations.

If HTML is the skeleton of a webpage, **CSS is the skin and clothes** — it determines everything visual about how that skeleton is presented.

---

## How it Works

CSS works by **selecting** an HTML element and then applying **rules** to it.

```css
p {
  color: red;
  font-size: 18px;
}
```

- `p` — the **selector**. Targets all `<p>` elements on the page.
- `color: red` — a **declaration**. Made up of a property (`color`) and a value (`red`).
- The whole block `{ ... }` is called a **declaration block**.
- Together, the selector + declaration block is called a **rule**.

The browser reads your HTML, finds the elements that match each CSS selector, and applies the styles to them.

---

## The "Cascading" Part

The word *cascading* is the key to understanding how CSS handles conflicts. When multiple rules target the same element, CSS follows a priority order to decide which one wins:

1. **Specificity** — more specific selectors win over general ones. An `id` beats a `class`, a `class` beats a tag name.
2. **Order** — if two rules have equal specificity, the one written later in the file wins.
3. **Inheritance** — some properties (like `color` and `font-family`) are automatically inherited by child elements from their parent.

You don't need to memorize all the rules right now — just know that this system exists and is called the cascade.

---

## Three Ways to Add CSS

### 1. Inline — directly on the element
```html
<p style="color: red; font-size: 18px;">Hello</p>
```
Quick but messy. Hard to maintain. Avoid unless there's a specific reason.

### 2. Internal — inside a `<style>` tag in the HTML file
```html
<head>
  <style>
    p {
      color: red;
    }
  </style>
</head>
```
Fine for small single-page projects or quick testing. Not ideal for larger projects.

### 3. External — a separate `.css` file (recommended)
```html
<!-- In your HTML <head> -->
<link rel="stylesheet" href="styles.css" />
```
```css
/* In styles.css */
p {
  color: red;
}
```
This is the standard approach. Keeps your HTML and CSS separate, and one stylesheet can apply to many HTML pages.

---

## What CSS is Used For

- Setting colors, fonts, and text sizes
- Controlling spacing — padding and margin
- Building page layouts — side by side columns, grids, centered content
- Making pages responsive — adapting the design for different screen sizes
- Adding hover effects, transitions, and animations
- Controlling visibility and layering of elements

---

## How CSS and HTML Work Together

CSS does not work on its own — it always targets HTML. The connection is made through:

- **Tag names** — `p`, `h1`, `div`
- **Classes** — `class="card"` in HTML, `.card` in CSS
- **IDs** — `id="header"` in HTML, `#header` in CSS

Classes and IDs are how you give CSS something specific to target, rather than styling every element of the same type the same way.

```html
<p class="intro">This paragraph is styled differently.</p>
<p>This one uses the default style.</p>
```

```css
.intro {
  font-size: 20px;
  color: navy;
}
```

Only the first paragraph gets those styles. That is the core workflow of CSS — writing HTML, giving elements classes, then styling those classes.
