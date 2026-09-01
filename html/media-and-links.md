# HTML — Media and Links

## Hyperlinks

Links are created with the `<a>` (anchor) tag.

```html
<a href="https://www.google.com">Go to Google</a>
```

- `href` — the URL the link points to. Required.
- The text between the tags is what the user clicks on.

### Open in a new tab
```html
<a href="https://www.google.com" target="_blank">Open in new tab</a>
```
`target="_blank"` opens the link in a new browser tab instead of the current one.

### Link to another page in your project
```html
<a href="about.html">About Page</a>
```
Use a relative path to link to other HTML files in your project.

### Link to a section on the same page
```html
<!-- Give the target element an id -->
<h2 id="contact">Contact</h2>

<!-- Use # followed by that id in the href -->
<a href="#contact">Jump to Contact</a>
```
This is called an anchor link. Clicking it scrolls the page to that element.

### Email link
```html
<a href="mailto:someone@example.com">Send Email</a>
```
Opens the user's default email client with the address pre-filled.

---

## Images

Images use the `<img>` tag. It is self-closing — no closing `</img>` needed.

```html
<img src="photo.jpg" alt="A description of the photo" />
```

- `src` — path to the image. Can be a local file or a URL.
- `alt` — alternative text. Displayed if the image fails to load and read aloud by screen readers. Never skip it unless the image is purely decorative.

### Setting a size
```html
<img src="photo.jpg" alt="A photo" width="400" height="300" />
```
You can set dimensions in HTML, but sizing is more commonly handled with CSS.

### Image from the web
```html
<img src="https://example.com/image.jpg" alt="Image from the web" />
```

### Local image in a subfolder
```html
<img src="images/photo.jpg" alt="Local image" />
```

---

## Audio

```html
<audio controls>
  <source src="audio.mp3" type="audio/mpeg" />
  Your browser does not support the audio element.
</audio>
```

- `controls` — adds the play, pause, and volume UI. Without it, the audio is completely invisible on the page.
- `<source>` — specifies the file and its format.
- The fallback text between the tags is shown only if the browser doesn't support `<audio>`.

### Common attributes
```html
<audio controls autoplay loop muted>
  <source src="audio.mp3" type="audio/mpeg" />
</audio>
```

| Attribute  | What it does                                                              |
|------------|---------------------------------------------------------------------------|
| `controls` | Shows the playback controls                                               |
| `autoplay` | Plays on page load — usually requires `muted` to work in modern browsers  |
| `loop`     | Replays when the audio ends                                               |
| `muted`    | Starts with sound off                                                     |

### Multiple formats for compatibility
```html
<audio controls>
  <source src="audio.mp3" type="audio/mpeg" />
  <source src="audio.ogg" type="audio/ogg" />
</audio>
```
The browser plays the first format it supports and ignores the rest.

---

## Video

Works almost identically to audio, but with the `<video>` tag.

```html
<video controls width="640">
  <source src="video.mp4" type="video/mp4" />
  Your browser does not support the video element.
</video>
```

- `controls` — adds the playback UI.
- `width` — sets the display width. Height adjusts automatically to preserve the aspect ratio.

### Common attributes
```html
<video controls autoplay loop muted poster="thumbnail.jpg" width="640">
  <source src="video.mp4" type="video/mp4" />
</video>
```

| Attribute  | What it does                                                              |
|------------|---------------------------------------------------------------------------|
| `controls` | Shows the playback controls                                               |
| `autoplay` | Plays on page load — requires `muted` in most browsers                    |
| `loop`     | Loops the video                                                           |
| `muted`    | Starts with sound off                                                     |
| `poster`   | An image shown before the video starts, like a thumbnail                  |

---

## Favicon

A favicon is the small icon shown on the browser tab next to the page title. It goes inside `<head>`.

```html
<head>
  <link rel="icon" type="image/png" href="favicon.png" />
</head>
```

- `rel="icon"` — tells the browser this is the page icon.
- `href` — path to the icon file.

### Supported formats

| Format | Notes                                        |
|--------|----------------------------------------------|
| `.ico` | Classic format, works in every browser       |
| `.png` | Widely supported, easier to work with        |
| `.svg` | Modern, scales perfectly at any resolution   |

```html
<!-- .ico -->
<link rel="icon" type="image/x-icon" href="favicon.ico" />

<!-- .png -->
<link rel="icon" type="image/png" href="favicon.png" />

<!-- .svg -->
<link rel="icon" type="image/svg+xml" href="favicon.svg" />
```

If no favicon is set, the browser shows a generic blank icon. You can generate a favicon from any image at [favicon.io](https://favicon.io).
