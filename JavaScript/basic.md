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

## Checked Property

---

## Checked Property

When working with checkboxes and radio buttons, you can't use `.value` to know if one is selected — `.value` just gives you the value attribute regardless of whether it's checked or not. Instead you use `.checked`, which returns `true` if selected and `false` if not.

### Checkbox

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>My Website</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <input type="checkbox" id="myCheckbox" />
    <label for="myCheckbox">I agree to the terms</label><br /><br />
    <button id="myBtn">Submit</button>
    <p id="myResult"></p>

    <script src="index.js"></script>
  </body>
</html>
```

```javascript
// index.js
const myBtn = document.getElementById("myBtn");
const myCheckbox = document.getElementById("myCheckbox");
const myResult = document.getElementById("myResult");

myBtn.onclick = function() {
    if (myCheckbox.checked) {
        myResult.textContent = "Terms accepted";
    } else {
        myResult.textContent = "Please accept the terms first";
    }
};
```

`.checked` returns `true` or `false` — so you can use it directly as the condition in an `if` statement without comparing it to anything.

---

### Radio Buttons

Radio buttons come in a group — only one can be selected at a time. They share the same `name` attribute to form that group. You check each one individually with `.checked`.

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>My Website</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <input type="radio" id="creditCard" name="payment" value="credit card" />
    <label for="creditCard">Credit Card</label><br />

    <input type="radio" id="debitCard" name="payment" value="debit card" />
    <label for="debitCard">Debit Card</label><br />

    <input type="radio" id="paypal" name="payment" value="PayPal" />
    <label for="paypal">PayPal</label><br /><br />

    <button id="myBtn">Confirm</button>
    <p id="myResult"></p>

    <script src="index.js"></script>
  </body>
</html>
```

```javascript
// index.js
const myBtn = document.getElementById("myBtn");
const myResult = document.getElementById("myResult");

myBtn.onclick = function() {
    const creditCard = document.getElementById("creditCard");
    const debitCard = document.getElementById("debitCard");
    const paypal = document.getElementById("paypal");

    if (creditCard.checked) {
        myResult.textContent = `Payment method: ${creditCard.value}`;
    } else if (debitCard.checked) {
        myResult.textContent = `Payment method: ${debitCard.value}`;
    } else if (paypal.checked) {
        myResult.textContent = `Payment method: ${paypal.value}`;
    } else {
        myResult.textContent = "Please select a payment method";
    }
};
```

- All three radio buttons share `name="payment"` — that's what groups them so only one can be selected.
- You check each one with `.checked` and read its label with `.value`.
- The final `else` handles the case where the user clicks Confirm without selecting anything.

### `.checked` vs `.value` — the difference

```javascript
// .value always returns the value attribute, selected or not
document.getElementById("creditCard").value;   // "credit card" — always

// .checked tells you if it's actually selected
document.getElementById("creditCard").checked; // true or false
```

Use `.value` to get what it says, `.checked` to know if it's ticked.



---

## String Methods

Strings have built-in methods — functions you can call directly on them to get information or produce a new modified string. The original string is never changed.

```javascript
let str = "Hello, World!";
```

---

### Length

Not a method but a property — returns the number of characters in the string.

```javascript
console.log(str.length); // 13
```

---

### Case

```javascript
str.toUpperCase(); // "HELLO, WORLD!"
str.toLowerCase(); // "hello, world!"
```

Useful for case-insensitive comparisons:

```javascript
let input = "YeS";
if (input.toLowerCase() === "yes") {
    console.log("Confirmed");
}
```

---

### Trimming whitespace

Removes spaces (and tabs/newlines) from the start and end of a string. Very common when dealing with user input.

```javascript
let messy = "   hello world   ";

messy.trim();       // "hello world"     — both sides
messy.trimStart();  // "hello world   "  — left side only
messy.trimEnd();    // "   hello world"  — right side only
```

---

### Checking contents

```javascript
let str = "Hello, World!";

str.includes("World");      // true  — checks if substring exists anywhere
str.startsWith("Hello");    // true  — checks the beginning
str.endsWith("!");          // true  — checks the end
```

All three return `true` or `false`, so you can use them directly in `if` conditions:

```javascript
if (str.includes("World")) {
    console.log("Found it");
}
```

---

### Finding position

```javascript
str.indexOf("o");      // 4  — index of first occurrence, -1 if not found
str.lastIndexOf("o");  // 8  — index of last occurrence
```

Indexes start at `0`. Returns `-1` if the substring is not found — useful for checking existence before proceeding.

---

### Extracting parts

```javascript
let str = "Hello, World!";

str.slice(7, 12);     // "World"  — from index 7 up to (not including) 12
str.slice(7);         // "World!" — from index 7 to the end
str.slice(-6);        // "orld!" — negative counts from the end

str.substring(7, 12); // "World"  — similar to slice, but no negative indexes
```

`slice` is the more flexible and modern choice — use it over `substring`.

---

### Replacing

```javascript
str.replace("World", "JavaScript");  // "Hello, JavaScript!" — replaces first match only
str.replaceAll("l", "r");            // "Herro, Worrd!"      — replaces every match
```

You can also use a regex for more powerful matching, but that's a separate topic.

---

### Splitting into an array

Splits a string into an array of pieces, divided at the separator you specify.

```javascript
let csv = "apple,banana,mango,grape";
csv.split(","); // ["apple", "banana", "mango", "grape"]

let sentence = "Hello World";
sentence.split(" ");  // ["Hello", "World"]
sentence.split("");   // ["H","e","l","l","o"," ","W","o","r","l","d"] — every character
```

---

### Padding

Adds characters to the start or end to reach a desired length. Useful for formatting output.

```javascript
"5".padStart(3, "0");  // "005" — pad left to length 3
"5".padEnd(3, "0");    // "500" — pad right to length 3
```

---

### Repeat

```javascript
"ha".repeat(3); // "hahaha"
```

---

### Chaining methods

Since each method returns a new string, you can chain them:

```javascript
let input = "   Hello World   ";
let cleaned = input.trim().toLowerCase().replace("world", "JavaScript");
// "hello JavaScript"
```

---

### Quick reference

| Method                  | What it does                                      | Example → Result               |
|-------------------------|---------------------------------------------------|--------------------------------|
| `.length`               | Number of characters                              | `"hello".length` → `5`         |
| `.toUpperCase()`        | All uppercase                                     | `"hi"` → `"HI"`                |
| `.toLowerCase()`        | All lowercase                                     | `"HI"` → `"hi"`                |
| `.trim()`               | Remove whitespace from both ends                  | `" hi "` → `"hi"`              |
| `.includes(str)`        | Check if substring exists                         | `true` / `false`               |
| `.startsWith(str)`      | Check if string starts with                       | `true` / `false`               |
| `.endsWith(str)`        | Check if string ends with                         | `true` / `false`               |
| `.indexOf(str)`         | Index of first match, -1 if not found             | `"hello".indexOf("l")` → `2`   |
| `.slice(start, end)`    | Extract part of a string                          | `"hello".slice(1,3)` → `"el"`  |
| `.replace(old, new)`    | Replace first match                               | `"aabbaa".replace("a","x")` → `"xabbaa"` |
| `.replaceAll(old, new)` | Replace all matches                               | `"aabbaa".replaceAll("a","x")` → `"xxbbxx"` |
| `.split(sep)`           | Split into array                                  | `"a,b".split(",")` → `["a","b"]` |
| `.padStart(len, char)`  | Pad left to reach length                          | `"5".padStart(3,"0")` → `"005"` |
| `.padEnd(len, char)`    | Pad right to reach length                         | `"5".padEnd(3,"0")` → `"500"`  |
| `.repeat(n)`            | Repeat the string n times                         | `"ha".repeat(2)` → `"haha"`    |

---

## Equality in JavaScript

JavaScript has more than one way to check equality, and they behave very differently. Getting this wrong is one of the most common sources of bugs.

---

### `==` — Loose equality

Compares values **after converting types** to match. This is called type coercion — JS tries to make both sides the same type before comparing.

```javascript
5 == "5"       // true  — number and string, JS converts "5" to 5
0 == false     // true  — false converts to 0
1 == true      // true  — true converts to 1
null == undefined  // true  — special case, only these two are loosely equal
"" == false    // true  — both coerce to 0
0 == ""        // true  — both coerce to 0
```

The results are often surprising and hard to reason about. Avoid `==` in real code.

---

### `===` — Strict equality

Compares both **value and type**. No type conversion happens. This is what you should use by default.

```javascript
5 === "5"          // false — same value, different types
5 === 5            // true
0 === false        // false — number vs boolean
null === undefined // false — different types
"" === false       // false
```

Simple rule: **always use `===` unless you have a specific reason not to.**

---

### `!=` — Loose inequality

The opposite of `==`. Returns `true` if values are not equal after type conversion.

```javascript
5 != "5"   // false — they are loosely equal, so != is false
5 != 6     // true
```

---

### `!==` — Strict inequality

The opposite of `===`. Returns `true` if value or type differ. Use this instead of `!=`.

```javascript
5 !== "5"  // true  — different types
5 !== 5    // false — same value and type
```

---

### `Object.is()` — Same-value equality

Works almost exactly like `===` but handles two edge cases differently.

```javascript
Object.is(5, 5);       // true
Object.is(5, "5");     // false

// The two edge cases where it differs from ===
Object.is(NaN, NaN);   // true  — === returns false for this
Object.is(0, -0);      // false — === returns true for this
```

`NaN === NaN` is `false` in JavaScript — one of the language's quirks. If you ever need to check if something is `NaN`, use `Number.isNaN()` or `Object.is(value, NaN)`.

```javascript
let x = NaN;
x === NaN;          // false — doesn't work
Number.isNaN(x);    // true  — correct way
Object.is(x, NaN);  // true  — also works
```

---

### Equality with objects and arrays

Primitive values (numbers, strings, booleans) are compared by **value**. Objects and arrays are compared by **reference** — meaning whether they point to the exact same thing in memory, not whether they look the same.

```javascript
// Primitives — compared by value
5 === 5          // true
"hello" === "hello"  // true

// Objects — compared by reference
let a = { name: "Aashwin" };
let b = { name: "Aashwin" };
let c = a;

a === b  // false — same content, but different objects in memory
a === c  // true  — both point to the exact same object
```

Same applies to arrays:

```javascript
[1, 2, 3] === [1, 2, 3]  // false — two separate arrays in memory
```

To compare object or array contents, you need to check each property/element individually, or use `JSON.stringify()` as a quick workaround:

```javascript
JSON.stringify(a) === JSON.stringify(b)  // true — compares the string representation
```

---

### Summary

| Operator      | Type check | Coercion | Use it?              |
|---------------|------------|----------|----------------------|
| `==`          | No         | Yes      | Avoid                |
| `===`         | Yes        | No       | Yes — default choice |
| `!=`          | No         | Yes      | Avoid                |
| `!==`         | Yes        | No       | Yes                  |
| `Object.is()` | Yes        | No       | For NaN / -0 checks  |

---

## Loops

Loops let you run the same block of code repeatedly without writing it out multiple times. JavaScript has several types — each suited for different situations.

---

### while loop

Repeats as long as the condition is `true`. The condition is checked **before** each iteration.

```javascript
let count = 1;

while (count <= 5) {
    console.log(count);
    count++;
}
// 1, 2, 3, 4, 5
```

Use `while` when you don't know in advance how many times you'll loop — you just loop until something changes.

```javascript
// Keep asking until valid input
let input = "";
while (input !== "quit") {
    input = window.prompt("Type something (or 'quit' to stop):");
}
```

---

### do...while loop

Same as `while`, except the code block runs **at least once** — the condition is checked **after** the first iteration.

```javascript
let count = 1;

do {
    console.log(count);
    count++;
} while (count <= 5);
// 1, 2, 3, 4, 5
```

The difference shows when the condition starts out false:

```javascript
let count = 10;

// while — never runs because condition is false from the start
while (count <= 5) {
    console.log(count); // never executes
}

// do...while — runs once regardless
do {
    console.log(count); // prints 10
} while (count <= 5);
```

Use `do...while` when you always need to run the code at least once — like showing a menu before checking if the user wants to exit.

---

### for loop

The most common loop. Best when you know exactly how many times you want to iterate.

```javascript
for (let i = 0; i < 5; i++) {
    console.log(i);
}
// 0, 1, 2, 3, 4
```

The three parts inside `for(...)`:
1. `let i = 0` — initializer, runs once before the loop starts
2. `i < 5` — condition, checked before each iteration
3. `i++` — update, runs after each iteration

```javascript
// Count down
for (let i = 10; i >= 1; i--) {
    console.log(i);
}

// Count by 2
for (let i = 0; i <= 10; i += 2) {
    console.log(i); // 0, 2, 4, 6, 8, 10
}
```

---

### for...of loop

Iterates over the **values** of an iterable — arrays, strings, etc. Cleaner than a regular `for` loop when you just need each value.

```javascript
let fruits = ["apple", "banana", "mango"];

for (let fruit of fruits) {
    console.log(fruit);
}
// apple
// banana
// mango
```

Works on strings too — iterates character by character:

```javascript
let name = "Aashwin";

for (let char of name) {
    console.log(char);
}
// A, a, s, h, w, i, n
```

---

### for...in loop

Iterates over the **keys** (property names) of an object.

```javascript
let person = {
    name: "Aashwin",
    age: 19,
    city: "Lucknow"
};

for (let key in person) {
    console.log(`${key}: ${person[key]}`);
}
// name: Aashwin
// age: 19
// city: Lucknow
```

- `key` gives you the property name (`"name"`, `"age"`, `"city"`)
- `person[key]` uses that key to get the value

`for...in` can also be used on arrays (it gives you the indexes), but `for...of` is preferred for arrays.

---

### break and continue

These give you control over loop flow.

**`break`** — exits the loop immediately.

```javascript
for (let i = 0; i < 10; i++) {
    if (i === 5) break;
    console.log(i);
}
// 0, 1, 2, 3, 4 — stops when i hits 5
```

**`continue`** — skips the current iteration and moves to the next one.

```javascript
for (let i = 0; i < 10; i++) {
    if (i % 2 === 0) continue;
    console.log(i);
}
// 1, 3, 5, 7, 9 — skips even numbers
```

Both work in `while`, `do...while`, `for`, `for...of`, and `for...in`.

---

### Nested loops

A loop inside another loop. The inner loop completes fully for each iteration of the outer loop.

```javascript
for (let i = 1; i <= 3; i++) {
    for (let j = 1; j <= 3; j++) {
        console.log(`${i} x ${j} = ${i * j}`);
    }
}
// 1 x 1 = 1
// 1 x 2 = 2
// 1 x 3 = 3
// 2 x 1 = 2
// ... and so on
```

---

### Which loop to use

| Loop         | Use when                                                      |
|--------------|---------------------------------------------------------------|
| `for`        | You know how many times to loop                               |
| `while`      | You loop until a condition changes, count unknown             |
| `do...while` | Same as while but must run at least once                      |
| `for...of`   | You need each value from an array or string                   |
| `for...in`   | You need each key from an object                              |

---

## Number Guessing Game

A practical project using everything covered so far — `Math.random()`, `Math.floor()`, variables, `const`, conditionals, loops, DOM manipulation, and `.checked`.

The computer picks a random number between 1 and 100. The user keeps guessing until they get it right.

### HTML

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Number Guessing Game</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <h1>Number Guessing Game</h1>
    <p>I'm thinking of a number between 1 and 100</p>

    <label>Your guess: </label>
    <input type="number" id="guessInput" /><br /><br />
    <button id="guessBtn">Guess</button>
    <button id="resetBtn">New Game</button>

    <p id="result"></p>
    <p id="attempts"></p>

    <script src="index.js"></script>
  </body>
</html>
```

### JavaScript

```javascript
// index.js
const guessBtn = document.getElementById("guessBtn");
const resetBtn = document.getElementById("resetBtn");
const guessInput = document.getElementById("guessInput");
const result = document.getElementById("result");
const attempts = document.getElementById("attempts");

let secretNumber = Math.floor(Math.random() * 100) + 1;
let attemptCount = 0;
let gameOver = false;

guessBtn.onclick = function() {
    if (gameOver) {
        result.textContent = "Game over. Click New Game to play again.";
        return;
    }

    const guess = Number(guessInput.value);

    if (guess < 1 || guess > 100) {
        result.textContent = "Please enter a number between 1 and 100.";
        return;
    }

    attemptCount++;
    attempts.textContent = `Attempts: ${attemptCount}`;

    if (guess === secretNumber) {
        result.textContent = `Correct! You guessed it in ${attemptCount} attempt(s)!`;
        gameOver = true;
    } else if (guess < secretNumber) {
        result.textContent = "Too low. Try higher.";
    } else {
        result.textContent = "Too high. Try lower.";
    }

    guessInput.value = "";
};

resetBtn.onclick = function() {
    secretNumber = Math.floor(Math.random() * 100) + 1;
    attemptCount = 0;
    gameOver = false;
    result.textContent = "";
    attempts.textContent = "";
    guessInput.value = "";
};
```

### How it works

- `secretNumber` is generated once when the page loads using `Math.random()` and `Math.floor()`
- Every time the user clicks Guess, `attemptCount` increments and the guess is compared to `secretNumber` using `===`
- `if / else if / else` gives the user a hint — too low, too high, or correct
- `gameOver` is a boolean flag — once the user wins, further guesses are blocked until reset
- The `return` keyword exits the function early — the code below it doesn't run
- Reset generates a fresh `secretNumber` and clears everything back to the starting state
