# HTML — Overview

## What is HTML?

HTML stands for **HyperText Markup Language**. It is the standard language used to create and structure content on the web.

It is not a programming language — it does not have logic, loops, or conditions. It is a **markup language**, meaning you use it to label and organize content so the browser knows what each piece of content is.

Every webpage you visit is built on top of HTML at its core.

---

## How it Works

HTML works through **elements**, which are written as **tags**. Tags tell the browser what kind of content something is.

For example:
- `<h1>` tells the browser "this is a main heading"
- `<p>` tells the browser "this is a paragraph"
- `<img>` tells the browser "this is an image"

Most tags come in pairs — an opening tag and a closing tag:

```
<p>This is a paragraph.</p>
```

The browser reads the HTML file from top to bottom and **renders** it — meaning it takes all those tags and turns them into the visual page you actually see.

The structure of every HTML file follows this basic skeleton:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Page Title</title>
  </head>
  <body>
    <!-- visible content goes here -->
  </body>
</html>
```

- `<!DOCTYPE html>` — tells the browser this is a modern HTML5 document
- `<head>` — holds metadata, the page title, links to CSS, etc. Nothing here is visible on the page
- `<body>` — everything visible on the page lives here

---

## What HTML is Used For

- Structuring text — headings, paragraphs, lists
- Embedding media — images, videos, audio
- Creating links to other pages
- Building forms — inputs, buttons, dropdowns
- Organizing page layout with containers like `<div>` and `<section>`
- Providing the base that CSS and JavaScript layer on top of

In short: **HTML is the skeleton of a webpage.** CSS handles how it looks, JavaScript handles how it behaves — but HTML is always the foundation.

---

## Live Server Extension (VS Code)

When you write an HTML file and open it directly in the browser, it works — but every time you make a change and save, you have to manually refresh the browser to see the update. That gets annoying fast.

**Live Server** is a VS Code extension that solves this. It spins up a local development server and **automatically refreshes the browser every time you save your file**.

### How to install it
1. Open VS Code
2. Go to the Extensions panel (the icon on the left sidebar, or `Ctrl+Shift+X`)
3. Search for **Live Server** by Ritwick Dey
4. Click Install

### How to use it
- Open your HTML file in VS Code
- Right-click anywhere in the file → **Open with Live Server**
- Or click the **"Go Live"** button in the bottom-right corner of VS Code

A browser tab will open and stay in sync with your file as you edit. Save the file, the browser updates instantly.

This is the standard way to preview HTML/CSS work locally during development.
