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

`let` lets you reassign a variable anytime. But some values should never change — like `PI`. If someone (or you by accident) reassigns it, the whole program breaks in a subtle way that's hard to debug.

That's where `const` comes in. Once assigned, it cannot be reassigned.

```javascript
// with let — nothing stops you from accidentally changing it
let pi = 3.14159;
pi = 420.69; // no error, silently breaks your math
```

```javascript
// with const — JavaScript throws an error if you try to reassign
const PI = 3.14159;
PI = 420.69; // TypeError: Assignment to constant variable
```

By convention, constants are written in `ALL_CAPS` to signal that the value should never change.

Here's a full circle circumference calculator using `const`:

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>My Website</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <h1 id="myH1">Enter Radius:</h1>

    <label>Radius: </label>
    <input id="myText" /><br /><br />
    <button id="mySubmit">Submit</button>

    <h3 id="myResult"></h3>

    <script src="index.js"></script>
  </body>
</html>
```

```javascript
// index.js
const PI = 3.14159;
let radius;
let circumference;

document.getElementById("mySubmit").onclick = function() {
    radius = document.getElementById("myText").value;
    radius = Number(radius);
    circumference = 2 * PI * radius;
    document.getElementById("myResult").textContent = circumference + " cm";
};
```

---

## Counter Program

A practical example that brings together `const`, `onclick`, and updating the page — a simple counter with increase, decrease, and reset buttons.

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>My Website</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <label id="countLabel">0</label><br />
    <div id="btnContainer">
      <button id="decreaseBtn" class="buttons">Decrease</button>
      <button id="resetBtn" class="buttons">Reset</button>
      <button id="increaseBtn" class="buttons">Increase</button>
    </div>

    <script src="index.js"></script>
  </body>
</html>
```

```css
/* style.css */
#countLabel {
    display: block;
    text-align: center;
    font-size: 10em;
    font-family: Helvetica;
}

#btnContainer {
    text-align: center;
}

.buttons {
    padding: 10px 20px;
    color: white;
    font-size: 1.5em;
    background-color: hsl(214, 100%, 74%);
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.25s;
}

.buttons:hover {
    background-color: hsl(214, 100%, 56%);
}
```

```javascript
// index.js
const decreaseBtn = document.getElementById("decreaseBtn");
const resetBtn = document.getElementById("resetBtn");
const increaseBtn = document.getElementById("increaseBtn");
const countLabel = document.getElementById("countLabel");
let count = 0;

increaseBtn.onclick = function() {
    count++;
    countLabel.textContent = count;
};

resetBtn.onclick = function() {
    count = 0;
    countLabel.textContent = count;
};

decreaseBtn.onclick = function() {
    count--;
    countLabel.textContent = count;
};
```

The DOM references (`decreaseBtn`, `resetBtn`, etc.) are `const` because you never need to point them at a different element — the element stays the same, only `count` changes. `count` is `let` because its value changes on every click.

## Math Object

JavaScript has a built-in `Math` object with constants and methods for common mathematical operations.

### Constants

```javascript
console.log(Math.PI); // 3.141592653589793
console.log(Math.E);  // 2.718281828459045 — Euler's number
```

### Rounding methods

```javascript
let x = 3.21;

Math.round(x);  // 3 — rounds to nearest integer (up if .5 or above)
Math.floor(x);  // 3 — always rounds down
Math.ceil(x);   // 4 — always rounds up
Math.trunc(x);  // 3 — removes the decimal, no rounding
```

### Power, root, and logarithm

```javascript
let x = 3.21;
let y = 2;

Math.pow(x, y);  // 10.3041 — x to the power of y (same as x ** y)
Math.sqrt(x);    // 1.7916 — square root of x
Math.log(x);     // 1.1663 — natural logarithm of x (base e)
```

### Trigonometry

```javascript
Math.sin(x);  // sine of x (in radians)
Math.cos(x);  // cosine of x
Math.tan(x);  // tangent of x
```

Note: these work in **radians**, not degrees. To convert degrees to radians: `degrees * (Math.PI / 180)`.

### Other useful methods

```javascript
Math.abs(-5);        // 5 — absolute value, removes the negative sign
Math.sign(-5);       // -1 — returns -1 (negative), 0, or 1 (positive)
Math.max(1, 5, 3);   // 5 — largest value from the list
Math.min(1, 5, 3);   // 1 — smallest value from the list
Math.random();       // random decimal between 0 (inclusive) and 1 (exclusive)
```

`Math.random()` is very commonly used. To get a random whole number in a range:

```javascript
// Random integer from 1 to 10
let random = Math.floor(Math.random() * 10) + 1;
```

### Quick reference

| Method           | What it does                              | Example → Result        |
|------------------|-------------------------------------------|-------------------------|
| `Math.round(x)`  | Rounds to nearest integer                 | `3.21` → `3`            |
| `Math.floor(x)`  | Rounds down                               | `3.99` → `3`            |
| `Math.ceil(x)`   | Rounds up                                 | `3.01` → `4`            |
| `Math.trunc(x)`  | Removes decimal, no rounding              | `3.99` → `3`            |
| `Math.pow(x, y)` | x to the power of y                       | `2, 3` → `8`            |
| `Math.sqrt(x)`   | Square root                               | `9` → `3`               |
| `Math.abs(x)`    | Absolute value                            | `-5` → `5`              |
| `Math.sign(x)`   | Sign of the number (-1, 0, or 1)          | `-5` → `-1`             |
| `Math.max(...)`  | Largest value from arguments              | `1, 5, 3` → `5`         |
| `Math.min(...)`  | Smallest value from arguments             | `1, 5, 3` → `1`         |
| `Math.random()`  | Random decimal between 0 and 1            | `0.4829...`             |


---

## Random Number Generator

A practical project using `Math.random()`, `Math.floor()`, user input, and DOM manipulation — all things covered so far.

The user enters a minimum and maximum number, clicks a button, and a random number in that range appears on the page.

### HTML

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Random Number Generator</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <h1>Random Number Generator</h1>

    <label>Min: </label>
    <input id="minInput" type="number" /><br /><br />

    <label>Max: </label>
    <input id="maxInput" type="number" /><br /><br />

    <button id="generateBtn">Generate</button>

    <h2 id="result"></h2>

    <script src="index.js"></script>
  </body>
</html>
```

### JavaScript

```javascript
// index.js
const generateBtn = document.getElementById("generateBtn");
const result = document.getElementById("result");

generateBtn.onclick = function() {
    const min = Number(document.getElementById("minInput").value);
    const max = Number(document.getElementById("maxInput").value);

    if (min > max) {
        result.textContent = "Min can't be greater than Max";
    } else {
        const randomNum = Math.floor(Math.random() * (max - min + 1)) + min;
        result.textContent = randomNum;
    }
};
```

### How the formula works

```javascript
Math.floor(Math.random() * (max - min + 1)) + min
```

Breaking it down step by step with `min = 1` and `max = 10` as an example:

1. `Math.random()` — gives a decimal from `0` up to (but not including) `1`, e.g. `0.743`
2. `(max - min + 1)` — the size of the range, `10 - 1 + 1 = 10`
3. `Math.random() * 10` — scales the decimal to `0` up to `9.999...`
4. `Math.floor(...)` — removes the decimal, giving a whole number from `0` to `9`
5. `+ min` — shifts the range up so it starts at `1` instead of `0`, giving `1` to `10`

The `+ 1` inside the range makes it **inclusive** on both ends — both `min` and `max` can actually be generated.

### The if/else check

```javascript
if (min > max) {
    result.textContent = "Min can't be greater than Max";
} else {
    // generate the number
}
```

This is basic input validation — if the user enters something that doesn't make sense (like min 10, max 2), the program catches it and shows a message instead of producing a nonsense result. Always good practice.


## Conditionals

Conditionals let your program make decisions — run different code depending on whether something is true or false.

### if / else if / else

```javascript
let age = 25;

if (age >= 18) {
    console.log("You are old enough to enter this site");
} else if (age <= 0) {
    console.log("You are not born yet");
} else {
    console.log("You are not old enough to enter this site");
}
```

- `if` — checks the condition. If `true`, runs its block and skips the rest.
- `else if` — checked only if the `if` above was `false`. You can chain as many as you need.
- `else` — runs only if every condition above was `false`. It's the fallback. No condition needed.

Only one block ever runs — JavaScript goes top to bottom, finds the first `true` condition, runs it, and stops.

### Comparison operators

These are used inside conditions to compare values.

| Operator | Meaning                        | Example           |
|----------|--------------------------------|-------------------|
| `==`     | Equal in value (loose)         | `5 == "5"` → `true`  |
| `===`    | Equal in value AND type (strict) | `5 === "5"` → `false` |
| `!=`     | Not equal (loose)              | `5 != 3` → `true` |
| `!==`    | Not equal (strict)             | `5 !== "5"` → `true` |
| `>`      | Greater than                   | `10 > 5` → `true` |
| `<`      | Less than                      | `3 < 7` → `true`  |
| `>=`     | Greater than or equal          | `5 >= 5` → `true` |
| `<=`     | Less than or equal             | `4 <= 3` → `false`|

**Always prefer `===` over `==`**. The loose `==` does type conversion behind the scenes which leads to unexpected results. `===` checks both value and type — no surprises.

```javascript
console.log(5 == "5");   // true  — loose, converts types
console.log(5 === "5");  // false — strict, different types
```

### Logical operators

Used to combine multiple conditions.

| Operator | Meaning | True when                         |
|----------|---------|-----------------------------------|
| `&&`     | AND     | Both conditions are true          |
| `\|\|`   | OR      | At least one condition is true    |
| `!`      | NOT     | The condition is false (inverts it) |

```javascript
let age = 25;
let hasID = true;

// AND — both must be true
if (age >= 18 && hasID) {
    console.log("Entry allowed");
}

// OR — at least one must be true
if (age < 13 || age > 65) {
    console.log("Discounted ticket");
}

// NOT — inverts the condition
if (!hasID) {
    console.log("No ID, no entry");
}
```

### Nested if statements

You can put an `if` inside another `if` for more specific checks.

```javascript
let age = 20;
let hasTicket = true;

if (age >= 18) {
    if (hasTicket) {
        console.log("Welcome in");
    } else {
        console.log("You need a ticket");
    }
} else {
    console.log("You must be 18 or older");
}
```

Keep nesting shallow — if you find yourself three or four levels deep, it's usually a sign the logic needs to be restructured.

### Switch statement

`switch` is cleaner than a long chain of `else if` when you're checking one variable against many exact values.

```javascript
let day = "Monday";

switch (day) {
    case "Monday":
        console.log("Start of the work week");
        break;
    case "Friday":
        console.log("End of the work week");
        break;
    case "Saturday":
    case "Sunday":
        console.log("Weekend");
        break;
    default:
        console.log("Midweek");
}
```

- Each `case` checks if the variable matches that value.
- `break` exits the switch after a match. Without it, execution falls through to the next case.
- Two cases with no `break` between them (Saturday and Sunday above) share the same block — a useful pattern for grouping.
- `default` is the fallback if nothing matches — equivalent to `else`.

`switch` uses strict equality (`===`) internally, so types must match too.

### Ternary operator

A compact shorthand for a simple `if / else` — useful when you just need to assign one of two values.

```javascript
// Regular if/else
let message;
if (age >= 18) {
    message = "Adult";
} else {
    message = "Minor";
}

// Same thing as a ternary
let message = age >= 18 ? "Adult" : "Minor";
```

Syntax: `condition ? valueIfTrue : valueIfFalse`

Keep ternaries simple — one condition, one line. If the logic is more complex, use a regular `if/else` instead.