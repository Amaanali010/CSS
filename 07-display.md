# Lecture 7: Display — block, inline, inline-block, none

## What does `display` do?

The `display` property controls **how an element behaves in the layout** — whether it takes up its own line, sits next to other elements, or is hidden entirely. Every HTML element has a default display value, but CSS lets you change it.

## 1. display: block

A block-level element:
- Always starts on a **new line**
- Takes up the **full width available** (by default)
- **Respects** width, height, margin, and padding on all sides

```css
div {
  display: block;
}
```

Elements that are `block` by default: `<div>`, `<p>`, `<h1>`–`<h6>`, `<section>`, `<ul>`, `<li>`, `<form>`

**Example use case:** A navigation menu item that should stack vertically, or a paragraph, always starts fresh on its own line.

## 2. display: inline

An inline element:
- Does **NOT** start on a new line — it flows within the surrounding text, like a word in a sentence
- Only takes up as much width as its content needs
- **Ignores** `width` and `height` — setting them has no effect
- Top/bottom margin and padding are **ignored visually** for layout purposes (though left/right padding does work)

```css
span {
  display: inline;
}
```

Elements that are `inline` by default: `<span>`, `<a>`, `<strong>`, `<em>`, `<img>`(technically inline but respects width/height)

**Example use case:** Making a single word bold or colored within a sentence, without breaking the flow of text.

```html
<p>This is <span style="color: red;">important</span> text.</p>
```

## 3. display: inline-block

This is the "best of both worlds":
- Does **NOT** start on a new line (flows like inline)
- **DOES** respect `width`, `height`, `margin`, and `padding` on all sides (like block)

```css
button {
  display: inline-block;
  width: 120px;
  height: 40px;
}
```

**Example use case:** Buttons or cards that need a defined size but should still sit side-by-side.

## Comparison Table

| Property | `block` | `inline` | `inline-block` |
|---|---|---|---|
| Starts new line? | Yes | No | No |
| Respects width/height? | Yes | No | Yes |
| Respects margin/padding (all sides)? | Yes | Only left/right fully | Yes |
| Common elements | `div`, `p`, `h1` | `span`, `a`, `strong` | Set manually |

## 4. display: none

This completely **removes** the element from the page — it takes up no space at all, as if it doesn't exist.

```css
.hidden {
  display: none;
}
```

This is different from `visibility: hidden`, which hides the element **but still reserves its space** in the layout (leaving an empty gap).

```css
.invisible-but-present {
  visibility: hidden; /* element is invisible, but space is kept */
}
```

**Example use case:** `display: none` is commonly used for hiding elements that will be shown later with JavaScript, like a dropdown menu or a modal popup.

## Other important display values (preview)

You'll learn these in depth in later lectures:
- `display: flex` — turns the element into a flex container (Lecture 9)
- `display: grid` — turns the element into a grid container (Lecture 10)

## Key Takeaways

- `block` elements stack vertically and take full available width.
- `inline` elements flow within text and ignore width/height.
- `inline-block` combines both: no forced new line, but width/height/margin work.
- `display: none` removes the element entirely (no space reserved); `visibility: hidden` hides it but keeps its space.

## Practice Exercise

Create three `<span>` elements in a row. First, observe their default inline behavior. Then change their `display` to `inline-block` and give them each a `width`, `height`, and `background-color` to see the difference.
