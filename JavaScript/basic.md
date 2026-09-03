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

## Accepting User Input

There are two ways to accept input from a user:

1. **Window prompt** — quick and easy, but looks ugly and is rarely used in real projects
2. **HTML text box** — the proper way, used in actual websites

### Window prompt

```javascript
// index.js
let username;
username = window.prompt("What's your username?");
console.log(username);
```

A dialog box pops up asking the user to type something. Whatever they type is stored as a **string** in the variable.

### HTML Text Box

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>My Website</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <h1 id="myH1">Welcome</h1>

    <label>Username: </label>
    <input id="myText" /><br /><br />
    <button id="mySubmit">Submit</button>

    <script src="index.js"></script>
  </body>
</html>
```

```javascript
// index.js
let username;

document.getElementById("mySubmit").onclick = function() {
    username = document.getElementById("myText").value;
    console.log(username);
    document.getElementById("myH1").textContent = `Hello ${username}`;
};
```

- `.value` reads whatever the user typed into the input field
- `.onclick` assigns a function that runs when the button is clicked
- When the user clicks Submit, the `<h1>` text updates to greet them by name

---

## Data Type Conversion

Sometimes you need to change a value from one type to another. This comes up a lot with user input — `window.prompt` always returns a string, even if the user types a number.

### The problem

```javascript
let age = window.prompt("How old are you?");
age += 1;
console.log(age, typeof age);
// if user types 25, output is "251" — string concatenation, not math
```

`window.prompt` returns a string. Adding `1` to a string just glues them together instead of doing arithmetic.

### The fix — convert to a number first

```javascript
let age = window.prompt("How old are you?");
age = Number(age);
age += 1;
console.log(age, typeof age);
// now output is 26 — actual addition
```

### Converting between types

JavaScript gives you three conversion functions: `Number()`, `String()`, and `Boolean()`.

```javascript
let x = "pizza";
let y = 42;
let z = "";

x = Number(x);    // NaN — "pizza" can't be converted to a number
y = String(y);    // "42" — number becomes a string
z = Boolean(z);   // false — empty string is falsy
```

**What to expect from each conversion:**

| Original value | `Number()`  | `String()`   | `Boolean()` |
|----------------|-------------|--------------|-------------|
| `"25"`         | `25`        | `"25"`       | `true`      |
| `"pizza"`      | `NaN`       | `"pizza"`    | `true`      |
| `0`            | `0`         | `"0"`        | `false`     |
| `""`           | `0`         | `""`         | `false`     |
| `true`         | `1`         | `"true"`     | `true`      |
| `false`        | `0`         | `"false"`    | `false`     |

Key things to note:
- `NaN` stands for **Not a Number** — it's what you get when a conversion to number fails (like trying to convert `"pizza"`)
- Any non-empty string is `true` when converted to boolean
- `0` and `""` (empty string) are `false` when converted to boolean — these are called **falsy** values

### Constants

```javascript
let pi = 3.14159;
let radius;
let circumference;

radius = window.prompt('Enter the radius of a circle : ');
radius = Number(radius);

circumference = 2 * pi * radius;

console.log(circumference);
```

here averything works fine, but the point is till when. what if someone on purpose try to tweek the program in the worg direction so it doesnt work in the intended way. thats where const comes 

```javascript
const PI = 3.14159;
let radius;
let circumference;

pi = 420.69;

radius = window.prompt('Enter the radius of a circle : ');
radius = Number(radius);

circumference = 2 * pi * radius;

console.log(circumference);
```
now the pi value cannot be changed. 

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>My Website</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <h1 id="myH1">Enter Radius : </h1>

    <label>Radius : </label>
    <input id="myText" /><br /><br />
    <button id="mySubmit">Submit</button>

    <h3 id = "myResult"></h3>

    <script src="index.js"></script>
  </body>
</html>
```

```javascript
const PI = 3.14159;
let radius;
let circumference;

pi = 420.69;

document.getElementById("mySubmit").onclick = function(){
  radius = document.getElementById("myText").value;
  radius = Number(radius);
  circumference = 2 * pi * radius;
  radius = document.getElementById("mySubmit").textContent = circumference + "cm";
}
```

## Lets make a counter program 

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>My Website</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>

    <label id ="countLabel">0</label><br>
    <div id = "btnContainer">
      <button id = "decreaseBtn" class = "buttons">decrease</button>
      <button id = "resetBtn" class = "buttons">reset</button>
      <button id = "increaseBtn" class = "buttons">increase</button>
    </div>

    <script src="index.js"></script>
  </body>
</html>
```

```css
#countLabel{
  display: block; 
  text-align: center;
  font-size: 10em;
  font-family: Helvetica;
}

#btnContainer{
  text-align: center;
}
.buttons{
  padding: 10px 20px;
  color: white;
  font-size: 1.5em;
  background-color: hs1(214, 100%, 74%);
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.25s;
}
.butoons:hover{
    background-color: hs1(214, 100%, 56%);
}
```
```javascript

const decreaseBtn = document.getElementById("decreaseBtn");
const resetBtn = document.getElementById("resetBtn");
const increaseBtn = document.getElementById("increaseBtn");
const countLabel = document.getElementById("countLabel");
let count = 0;

increaseBtn.onclick = function(){
  count++;
  countLabel.textContent = count;
}

resetBtn.onclick = function(){
  count = 0;
  countLabel.textContent = count;
}

decreaseBtn.onclick = function(){
  count--;
  countLabel.textContent = count;
}
```