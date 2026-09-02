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

## Variable
variable is a container that holds value, t need to be declared and the two variable of same name can not be declared

```javascript
// index.js
let x;
x = 100;
//OR
let y = 123;

console.log(x);
console.log(y);

let age = 19;
console.log(`you are ${age} years old`);

console.log(typeof age);
console.log(typeof x);

// output will be number

let firstName = "Aashwin";
console.log(typeof firstName);
// output will be string 

let online = true;
console.log(typeof online);
// output boolean 

```
${} using placeholder and putting the variable inside lets you use it in between of the statement you are printing 

using typeof and variable name inside console.log() gives you data type of the variable 

strings are different from number, it consists of alpha, num, and symbols but the numbers cant be used for artheatic purposes

```javascript
// index.js
let fullName = "Aashwin Shukla";
let age = "19";
let isStudent = true;

document.getEmementById("p1").textContent = `Your name is : ${fullName}`;
document.getEmementById("p2").textContent = `You are ${age} years old`;
document.getEmementById("p3").textContent = `Are you a Student : ${isStudent}`;
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