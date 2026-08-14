# Lecture 12: Responsive Design — Media Queries and Mobile Layouts

## What is Responsive Design?

Responsive design means building a webpage that **automatically adapts** its layout to look good on any screen size — a huge desktop monitor, a laptop, a tablet, or a small phone screen. Instead of building separate websites for each device, we build one website that reshapes itself.

## The Viewport Meta Tag (essential first step)

Before writing any responsive CSS, every HTML page needs this line inside `<head>`:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

Without this tag, mobile browsers will render the page as if it were a full desktop-sized page and then shrink it down — making everything tiny and unusable. This tag tells the browser: "match the page width to the actual device width."

## Media Queries — the core tool

A media query lets you apply CSS rules **only when certain conditions are true** — most commonly, when the screen is below or above a certain width.

```css
/* Default styles apply to all screen sizes */
.container {
  display: flex;
  flex-direction: row;
}

/* This block ONLY applies when the screen is 768px wide or less */
@media (max-width: 768px) {
  .container {
    flex-direction: column;
  }
}
```

In this example, items sit side-by-side normally, but stack vertically once the screen becomes narrow — a very common pattern for mobile-friendly layouts.

## Mobile-First vs. Desktop-First

There are two common strategies:

### Desktop-First (using max-width)
You write styles for large screens first, then override for smaller screens as they shrink.
```css
.box { width: 50%; }

@media (max-width: 600px) {
  .box { width: 100%; }
}
```

### Mobile-First (using min-width) — the recommended modern approach
You write styles for small screens first (the default/base styles), then add complexity as the screen grows.
```css
.box { width: 100%; } /* mobile default */

@media (min-width: 600px) {
  .box { width: 50%; } /* applies on larger screens */
}
```

**Why mobile-first is preferred:** More people browse the web on phones than desktops today, and it forces you to prioritize the essential content first, adding enhancements as space allows.

## Common Breakpoints (reference guide)

There's no single "correct" set of breakpoints, but these are common starting points:

```css
/* Small phones */
@media (max-width: 480px) { }

/* Tablets */
@media (max-width: 768px) { }

/* Small laptops */
@media (max-width: 1024px) { }

/* Large desktops */
@media (min-width: 1200px) { }
```

**Best practice:** Rather than designing around specific devices, resize your browser slowly and add a breakpoint wherever the design starts to look broken. This is called designing based on **content**, not devices.

## Combining Conditions

```css
@media (min-width: 600px) and (max-width: 900px) {
  /* applies only between 600px and 900px */
}
```

## Responsive Units (working alongside media queries)

- `%` — relative to the parent element's size
- `vw` / `vh` — relative to the viewport's width/height (1vw = 1% of screen width)
- `rem` — relative to the root font size (great for scalable, accessible text)

```css
h1 {
  font-size: 5vw; /* text scales fluidly with screen width */
}
```

## A Practical Example: Responsive Card Grid

```css
.cards {
  display: grid;
  grid-template-columns: 1fr; /* mobile: 1 column by default */
  gap: 16px;
}

@media (min-width: 600px) {
  .cards {
    grid-template-columns: repeat(2, 1fr); /* tablets: 2 columns */
  }
}

@media (min-width: 1000px) {
  .cards {
    grid-template-columns: repeat(3, 1fr); /* desktop: 3 columns */
  }
}
```

**Reminder:** As covered in the Grid lecture, `repeat(auto-fit, minmax(...))` can often achieve similar responsiveness with less code and no media queries at all — both approaches are valid depending on how much control you need.

## Key Takeaways

- Always include the viewport meta tag in your HTML.
- Media queries (`@media`) apply CSS conditionally based on screen size.
- Mobile-first design (using `min-width`) is the modern recommended approach.
- Choose breakpoints based on where your specific design breaks, not fixed device sizes.
- Responsive units (`%`, `vw`, `vh`, `rem`) work hand-in-hand with media queries for fluid design.

## Practice Exercise

Build a 3-column layout using Flexbox or Grid. Add a media query so that below 768px width, the columns stack into a single column. Test it by resizing your browser window.
