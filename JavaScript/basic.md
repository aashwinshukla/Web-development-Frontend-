# JavaScript Basics

## Overview

We already saw that HTML creates the structure and CSS styles it. JavaScript adds **interactivity** — it makes things actually work.

Without JavaScript, a webpage is static. It just sits there. JavaScript is what makes a calculator calculate, a dropdown open, a form validate before submitting, or content update without reloading the page.

JS runs directly in the browser — no installation needed. Every browser has a JavaScript engine built in (Chrome uses V8, Firefox uses SpiderMonkey). You write the code, the browser runs it.

---

## Creating the Files

To tell your editor a file contains JavaScript, name it with the `.js` extension.

For a standard project you will typically have three files:

```
index.html
style.css
index.js
```

---

## Linking Everything Together

All three files are connected through `index.html`.

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>My Website</title>
    <link rel="stylesheet" href="style.css" /> <!-- link to CSS -->
  </head>
  <body>
    <h1></h1>
    <h2></h2>
    <p></p>

    <script src="index.js"></script> <!-- link to JS, always at the bottom -->
  </body>
</html>
```

```css
/* style.css */
body {
  font-family: Verdana;
  font-size: 2em;
}
```

The `<script>` tag goes at the **bottom of `<body>`**, just before `</body>`. This way the HTML loads and renders first — if there's a JS error, at least the page structure is visible. Putting it in `<head>` would make the browser wait for the JS to load before showing anything.

---

## Getting Output

### console.log

The main way to print output in JavaScript is `console.log()`. You won't see it on the webpage — it appears in the browser's developer console.

```javascript
// index.js
console.log(`hello`);
console.log('i like pizza');
console.log("hello world");
```

All three quote styles work — single `'`, double `"`, and backticks `` ` ``. Backticks are the most flexible (explained later), but all three are valid.

To see the output:
1. Open your page with Live Server
2. Right-click anywhere on the page → **Inspect**
3. Go to the **Console** tab — your output appears there

### window.alert

This creates a pop-up dialog on the page with the text inside.

```javascript
// index.js
window.alert(`This is an alert`);
```

Useful for quick testing but annoying in real projects — don't overuse it.

---

## Putting Content on the Page

Instead of hardcoding text in HTML, you can set it from JavaScript using `document.getElementById()`.

First, give your HTML elements an `id`:

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>My Website</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <h1 id="myH1"></h1>   <!-- id so JS can find it -->
    <p id="myP"></p>       <!-- id so JS can find it -->

    <script src="index.js"></script>
  </body>
</html>
```

Then in JavaScript, grab those elements by their `id` and set their content:

```javascript
// index.js
document.getElementById("myH1").textContent = `Hello`;
document.getElementById("myP").textContent = `I like solving and making things`;
```

The browser will display `Hello` as an `<h1>` and the second string as a `<p>` — even though the HTML tags were empty. JavaScript filled them in.

This is the foundation of how JavaScript talks to the page — find an element, then do something with it.

## Variables

A variable is a container that holds a value. It needs to be declared before use, and two variables with the same name cannot be declared in the same scope.

```javascript
// index.js
let x;
x = 100;
// OR declare and assign in one line
let y = 123;

console.log(x);
console.log(y);
```

### Data types

JavaScript has a few basic data types. You can check what type a value is using `typeof`.

```javascript
let age = 19;
console.log(typeof age);       // number

let firstName = "Aashwin";
console.log(typeof firstName); // string

let online = true;
console.log(typeof online);    // boolean
```

- **number** — any numeric value (`19`, `3.14`, `-5`)
- **string** — text wrapped in quotes (`"hello"`, `'world'`, `` `backtick` ``)
- **boolean** — only two values: `true` or `false`

Strings can contain letters, numbers, and symbols — but numbers stored as strings can't be used for arithmetic.

### Template literals

Backticks (`` ` ``) allow you to embed variables directly inside a string using `${}`. This is called a template literal.

```javascript
let age = 19;
console.log(`You are ${age} years old`);
// output: You are 19 years old
```

### Putting variables on the page

```javascript
// index.js
let fullName = "Aashwin Shukla";
let age = 19;
let isStudent = true;

document.getElementById("p1").textContent = `Your name is: ${fullName}`;
document.getElementById("p2").textContent = `You are ${age} years old`;
document.getElementById("p3").textContent = `Are you a student: ${isStudent}`;
```

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>My Website</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <p id="p1"></p>
    <p id="p2"></p>
    <p id="p3"></p>
    <script src="index.js"></script>
  </body>
</html>
```

---

## Arithmetic Operators

Used to perform math on numbers.

| Operator | Description       | Example          |
|----------|-------------------|------------------|
| `+`      | Addition          | `5 + 3` → `8`   |
| `-`      | Subtraction       | `5 - 3` → `2`   |
| `*`      | Multiplication    | `5 * 3` → `15`  |
| `/`      | Division          | `6 / 2` → `3`   |
| `**`     | Exponent (power)  | `2 ** 3` → `8`  |
| `%`      | Modulo (remainder)| `7 % 2` → `1`   |

```javascript
let students = 30;

students = students + 1;  // 31
students = students - 1;  // 30
students = students * 2;  // 60
students = students / 2;  // 30
students = students ** 2; // 900
students = students % 2;  // 0
```

### Shorthand assignment operators

Instead of writing `students = students + 1` you can shorten it:

```javascript
students += 1;   // same as students = students + 1
students -= 1;
students *= 2;
students /= 2;
students **= 2;
students %= 2;
```

For incrementing or decrementing by 1 specifically:

```javascript
students++;   // same as students += 1
students--;   // same as students -= 1
```

### Operator precedence

When multiple operators are in one expression, JavaScript follows this order:

1. Parentheses `()`
2. Exponents `**`
3. Multiplication `*`, Division `/`, Modulo `%`
4. Addition `+`, Subtraction `-`

```javascript
let result = 2 + 3 * 4;    // 14, not 20 — multiplication first
let result2 = (2 + 3) * 4; // 20 — parentheses first
```