# Lecture 9: Flexbox — Arranging Elements in Rows and Columns

## What is Flexbox?

Flexbox (Flexible Box Layout) is a CSS layout system designed to arrange items **in a single row or a single column**, and to distribute space between them intelligently — even when their sizes are unknown or dynamic.

Before Flexbox, centering something vertically was famously painful in CSS. Flexbox solves that and much more.

## Two Key Players

1. **Flex Container** — the parent element; you turn it into a flex container using `display: flex`
2. **Flex Items** — the direct children of the flex container; they automatically become flexible

```css
.container {
  display: flex;
}
```

```html
<div class="container">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>
```

The moment you add `display: flex` to `.container`, all its direct children line up **in a row** automatically.

## The Two Axes

Flexbox thinking revolves around two axes:
- **Main axis** — the primary direction items are laid out (horizontal by default)
- **Cross axis** — perpendicular to the main axis (vertical by default)

Understanding these two axes is the key to mastering Flexbox, because different properties control alignment along each axis.

## flex-direction — sets the main axis

```css
.container {
  display: flex;
  flex-direction: row;    /* default: left to right */
  /* other options: row-reverse, column, column-reverse */
}
```

- `row` → items go left to right (main axis = horizontal)
- `column` → items go top to bottom (main axis = vertical)

## justify-content — aligns items along the MAIN axis

```css
.container {
  display: flex;
  justify-content: center; /* centers items horizontally (if row) */
}
```

Common values:
- `flex-start` — items packed at the start (default)
- `flex-end` — items packed at the end
- `center` — items centered
- `space-between` — items spread out, no space at edges
- `space-around` — items spread out with equal space around each
- `space-evenly` — items spread out with perfectly equal spacing everywhere

## align-items — aligns items along the CROSS axis

```css
.container {
  display: flex;
  align-items: center; /* centers items vertically (if row) */
}
```

Common values: `flex-start`, `flex-end`, `center`, `stretch` (default — items stretch to fill the container's height), `baseline`

### The famous "center everything" trick

```css
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
```

This perfectly centers content both horizontally and vertically — something that used to require complicated hacks before Flexbox existed.

## flex-wrap — allows items to wrap onto multiple lines

By default, flex items try to squeeze onto one line, even if they overflow. `flex-wrap: wrap` allows them to move to a new line when there isn't enough space.

```css
.container {
  display: flex;
  flex-wrap: wrap;
}
```

## Properties for individual flex ITEMS

These are applied to the children, not the container:

```css
.item {
  flex-grow: 1;   /* how much this item grows to fill extra space, relative to siblings */
  flex-shrink: 1; /* how much this item shrinks if space is tight */
  flex-basis: 200px; /* the item's default size before growing/shrinking */
}
```

**Shorthand:**
```css
.item {
  flex: 1 1 200px; /* grow shrink basis */
}
```

A very common pattern: `flex: 1;` on all items makes them **share the available space equally**.

```css
.item {
  flex: 1;
}
```

### align-self — override align-items for one specific item

```css
.item-special {
  align-self: flex-end; /* just this one item aligns differently */
}
```

## Gap — spacing between flex items

```css
.container {
  display: flex;
  gap: 16px; /* spacing between items, no manual margins needed */
}
```

This is much cleaner than adding margins to individual items.

## Full Example: A simple navigation bar

```css
nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 20px;
}
```

```html
<nav>
  <div class="logo">MySite</div>
  <div class="links">
    <a href="#">Home</a>
    <a href="#">About</a>
    <a href="#">Contact</a>
  </div>
</nav>
```

This creates a classic navbar: logo on the left, links on the right, vertically centered.

## Key Takeaways

- `display: flex` on a parent turns its children into flex items arranged in a row (by default).
- `flex-direction` sets whether items go in a `row` or `column`.
- `justify-content` aligns items along the main axis; `align-items` aligns along the cross axis.
- `flex-wrap` allows items to move to new lines when space runs out.
- `flex: 1` on items makes them grow to share space equally.
- `gap` adds spacing between items without manual margins.

## Practice Exercise

Build a row of 3 cards using Flexbox. Make them equally sized using `flex: 1`, add a `gap` of 20px between them, and center them vertically using `align-items: center`.
