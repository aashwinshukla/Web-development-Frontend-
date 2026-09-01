# CSS — Flexbox, Transformations, and Animations

## Flexbox

Flexbox is a layout model that arranges items in a row or column with powerful control over alignment, spacing, and sizing. It works on two levels — the **container** and the **items** inside it.

```css
.container {
  display: flex;
}
```
All direct children become **flex items**.

---

### Container Properties

#### `flex-direction` — which direction items flow
```css
.container {
  flex-direction: row;             /* default — left to right */
  flex-direction: row-reverse;     /* right to left */
  flex-direction: column;          /* top to bottom */
  flex-direction: column-reverse;  /* bottom to top */
}
```

#### `justify-content` — alignment along the main axis
```css
.container {
  justify-content: flex-start;    /* default — items at the start */
  justify-content: flex-end;      /* items at the end */
  justify-content: center;        /* items centered */
  justify-content: space-between; /* equal space between, none at edges */
  justify-content: space-around;  /* equal space around each item */
  justify-content: space-evenly;  /* equal space between items and edges */
}
```

#### `align-items` — alignment along the cross axis
```css
.container {
  align-items: stretch;     /* default — items stretch to fill height */
  align-items: flex-start;  /* align to the top */
  align-items: flex-end;    /* align to the bottom */
  align-items: center;      /* centered vertically */
  align-items: baseline;    /* align by text baseline */
}
```

#### `flex-wrap` — whether items wrap to a new line
```css
.container {
  flex-wrap: nowrap;  /* default — one line, may overflow */
  flex-wrap: wrap;    /* wraps to next line when items don't fit */
}
```

#### `gap` — space between items
```css
.container {
  gap: 16px;         /* same in both directions */
  gap: 16px 24px;    /* row-gap column-gap */
}
```

---

### Item Properties

#### `flex-grow` — how much an item grows to fill space
```css
.item {
  flex-grow: 0;  /* default — does not grow */
  flex-grow: 1;  /* grows to fill available space */
}
```
If all items have `flex-grow: 1` they share space equally. If one has `flex-grow: 2` it takes twice the share.

#### `flex-shrink` — how much an item shrinks when space is tight
```css
.item {
  flex-shrink: 1;  /* default — can shrink */
  flex-shrink: 0;  /* will not shrink — stays at its set size */
}
```

#### `flex-basis` — the starting size before growing/shrinking
```css
.item {
  flex-basis: auto;    /* default — uses the item's own width/height */
  flex-basis: 200px;   /* starts at 200px, then grows/shrinks from there */
}
```

#### `flex` shorthand — grow, shrink, basis together
```css
.item {
  flex: 1;          /* grow: 1, shrink: 1, basis: 0 */
  flex: 1 1 200px;  /* grow: 1, shrink: 1, basis: 200px */
  flex: 0 0 300px;  /* fixed — no growing or shrinking */
}
```
`flex: 1` is the most common shorthand — makes all items share space equally.

#### `align-self` — override `align-items` for one item
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
.item-b { order: 1; }  /* appears first visually */
.item-c { order: 3; }
```
Default is `0`. Lower values appear first.

---

### Common Patterns

#### Center anything perfectly
```css
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
```
The easiest way to center something both horizontally and vertically.

#### Equal-width columns
```css
.container {
  display: flex;
  gap: 24px;
}
.column {
  flex: 1;
}
```

#### Logo left, links right
```css
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```

#### Push one item to the far end
```css
.container {
  display: flex;
}
.last-item {
  margin-left: auto;
}
```

---

## Transformations

The `transform` property visually moves, rotates, scales, or skews an element — without affecting the layout of surrounding elements. The element still occupies its original space.

### Translate — move
```css
div {
  transform: translateX(50px);         /* move right */
  transform: translateY(-20px);        /* move up */
  transform: translate(50px, -20px);   /* move right and up */
}
```
Negative values move left/up. Positive move right/down.

### Scale — resize
```css
div {
  transform: scale(1.5);       /* 1.5x bigger both directions */
  transform: scaleX(2);        /* stretch horizontally only */
  transform: scaleY(0.5);      /* squish vertically only */
  transform: scale(1.2, 0.8);  /* different x and y */
}
```
`scale(1)` = original. `scale(2)` = double. `scale(0.5)` = half.

### Rotate
```css
div {
  transform: rotate(45deg);   /* clockwise */
  transform: rotate(-90deg);  /* counter-clockwise */
}
```

### Skew — slant
```css
div {
  transform: skewX(20deg);
  transform: skewY(10deg);
  transform: skew(20deg, 10deg);
}
```

### Combining transforms
```css
div {
  transform: translate(50px, 20px) rotate(45deg) scale(1.2);
}
```
Space-separated on the same property. Applied right to left — scale first, then rotate, then translate.

### Transform origin
By default transforms happen from the center. Change it:

```css
div {
  transform-origin: top left;
  transform-origin: bottom center;
  transform-origin: 50% 50%;  /* default */
  transform-origin: 0 0;      /* top-left corner */
}
```

### 3D transforms
```css
div {
  transform: rotateX(45deg);   /* tilt on x axis */
  transform: rotateY(45deg);   /* spin on y axis */
  transform: translateZ(50px); /* move towards/away from viewer */
}
```

Add perspective to the parent for 3D to look correct:
```css
.parent {
  perspective: 800px;  /* lower = more dramatic effect */
}
```

### Transforms with transition
Transforms are most useful combined with `transition`:

```css
.card {
  transition: transform 0.3s ease;
}
.card:hover {
  transform: translateY(-8px) scale(1.02);
}
```

---

## Animations

CSS animations let elements animate automatically — no interaction required. Built from two parts: `@keyframes` and the `animation` property.

### @keyframes — define the animation

```css
@keyframes fadeIn {
  from { opacity: 0; }
  to   { opacity: 1; }
}
```

Use percentages for more control:
```css
@keyframes bounce {
  0%   { transform: translateY(0); }
  50%  { transform: translateY(-30px); }
  100% { transform: translateY(0); }
}

@keyframes colorShift {
  0%   { background-color: red; }
  33%  { background-color: blue; }
  66%  { background-color: green; }
  100% { background-color: red; }
}
```

### animation — apply it to an element

```css
div {
  animation: fadeIn 1s ease forwards;
}
```

Shorthand order: `name` `duration` `timing-function` `delay` `iteration-count` `direction` `fill-mode`.

Individual properties:
```css
div {
  animation-name: fadeIn;
  animation-duration: 1s;
  animation-timing-function: ease;
  animation-delay: 0.5s;
  animation-iteration-count: 1;
  animation-direction: normal;
  animation-fill-mode: forwards;
}
```

### Timing functions

| Value          | Description                             |
|----------------|-----------------------------------------|
| `ease`         | Default. Slow start, fast middle, slow end |
| `linear`       | Constant speed                          |
| `ease-in`      | Starts slow, ends fast                  |
| `ease-out`     | Starts fast, ends slow                  |
| `ease-in-out`  | Slow start and slow end                 |
| `cubic-bezier` | Custom curve — full control             |

### Iteration count
```css
animation-iteration-count: 1;         /* plays once */
animation-iteration-count: 3;         /* plays 3 times */
animation-iteration-count: infinite;  /* loops forever */
```

### Direction
```css
animation-direction: normal;            /* forward each time — default */
animation-direction: reverse;           /* plays backwards */
animation-direction: alternate;         /* forward, then backward, repeat */
animation-direction: alternate-reverse; /* backward, then forward, repeat */
```

### Fill mode
```css
animation-fill-mode: none;      /* snaps back after animation — default */
animation-fill-mode: forwards;  /* holds final state after it ends */
animation-fill-mode: backwards; /* applies first keyframe during delay */
animation-fill-mode: both;      /* forwards + backwards */
```
`forwards` is the most used — prevents the element snapping back after finishing.

### Multiple animations
```css
div {
  animation: fadeIn 1s ease forwards, bounce 0.5s ease 1s infinite;
}
```
Comma-separated. Each runs independently.

### Pausing
```css
div:hover {
  animation-play-state: paused;
}
```

---

### Transition vs Animation

| | Transition | Animation |
|---|---|---|
| Trigger | Needs a state change (hover, focus, class) | Runs automatically |
| Keyframes | No — just start and end | Yes — full control |
| Looping | No | Yes — `infinite` |
| Use case | Hover effects, UI feedback | Spinners, intros, continuous motion |

---

### Practical Examples

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

#### Pulse
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
