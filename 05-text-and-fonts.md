# Lecture 5: Text & Fonts — font-size, font-family, text-align

Good typography (text styling) makes the difference between a page that's pleasant to read and one that feels messy. This lecture covers the core properties for controlling text.

## font-family

This sets which typeface (font) is used for text.

```css
p {
  font-family: Arial, sans-serif;
}
```

**Why are there two values?** The first is your preferred font (`Arial`). The second (`sans-serif`) is a **fallback** — if the user's device doesn't have Arial installed, the browser uses any generic sans-serif font instead. This is called a **font stack**.

Common generic font families:
- `serif` — fonts with small decorative strokes (e.g., Times New Roman) — often used for formal/traditional text
- `sans-serif` — clean fonts with no decorative strokes (e.g., Arial, Helvetica) — common for modern web design
- `monospace` — every character has equal width (e.g., Courier New) — used for code

### Using custom/web fonts (like Google Fonts)

```html
<link href="https://fonts.googleapis.com/css2?family=Roboto" rel="stylesheet">
```
```css
body {
  font-family: 'Roboto', sans-serif;
}
```

## font-size

Sets how big the text appears. Common units:

```css
h1 {
  font-size: 32px;   /* fixed pixel size */
}
p {
  font-size: 1.2em;  /* relative to the parent element's font size */
}
small {
  font-size: 0.8rem; /* relative to the root (html) font size */
}
```

| Unit | Meaning | Best for |
|---|---|---|
| `px` | Fixed pixels | Precise control |
| `em` | Relative to the parent's font size | Component-based scaling |
| `rem` | Relative to the root (`<html>`) font size | Consistent, predictable scaling — recommended for most projects |
| `%` | Percentage of parent | Similar to `em` |

## font-weight

Controls how bold or thin text looks.

```css
p {
  font-weight: bold;   /* or: normal, lighter, bolder, or a number 100–900 */
}
```

## font-style

```css
p {
  font-style: italic; /* or: normal, oblique */
}
```

## text-align

Controls the horizontal alignment of text inside its container.

```css
h1 {
  text-align: center; /* left, right, center, justify */
}
```
- `left` — default for most languages
- `center` — centers text, common for headings
- `right` — aligns to the right
- `justify` — stretches text so both edges line up evenly (like in newspapers)

## Other useful text properties

```css
p {
  text-decoration: underline;   /* none, underline, line-through, overline */
  text-transform: uppercase;    /* none, uppercase, lowercase, capitalize */
  line-height: 1.6;             /* space between lines of text */
  letter-spacing: 1px;          /* space between characters */
}
```

- `line-height` is extremely important for readability — a value between `1.4` and `1.8` usually makes paragraphs much easier to read.
- `text-transform: capitalize` makes the First Letter Of Each Word uppercase, without changing the actual text.

## Putting it all together

```css
body {
  font-family: 'Segoe UI', Arial, sans-serif;
}

h1 {
  font-size: 2.5rem;
  font-weight: bold;
  text-align: center;
  text-transform: uppercase;
  letter-spacing: 2px;
}

p {
  font-size: 1rem;
  line-height: 1.6;
  color: #333333;
}
```

## Key Takeaways

- `font-family` sets the typeface; always include a fallback generic font.
- `font-size` controls text size; `rem` is often the safest unit for consistency.
- `font-weight` and `font-style` control boldness and italics.
- `text-align` controls horizontal alignment; `line-height` controls vertical spacing between lines and greatly affects readability.

## Practice Exercise

Style a paragraph so it uses a sans-serif font stack, a font size of `1rem`, a line-height of `1.6`, and is center-aligned. Then style a heading above it with a bold, uppercase, letter-spaced look.
