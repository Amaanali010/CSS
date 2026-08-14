# Lecture 10: CSS Grid — Creating Two-Dimensional Layouts

## Flexbox vs. Grid — what's the difference?

- **Flexbox** is best for **one-dimensional** layouts — a single row OR a single column.
- **CSS Grid** is best for **two-dimensional** layouts — rows AND columns at the same time.

Think of Grid as designing a spreadsheet or a checkerboard, where you can place items into specific rows and columns.

## Turning on Grid

```css
.container {
  display: grid;
}
```

Just like Flexbox, this makes the direct children of `.container` become **grid items**.

## Defining Columns and Rows

```css
.container {
  display: grid;
  grid-template-columns: 200px 200px 200px; /* 3 columns, each 200px wide */
  grid-template-rows: 100px 100px;          /* 2 rows, each 100px tall */
}
```

This creates a grid with 3 columns and 2 rows — 6 total cells — and items automatically fill them in order.

## The `fr` unit — fractional space

`fr` stands for "fraction" and represents a portion of the **available space**. This is one of Grid's most powerful features.

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr; /* 3 equal-width columns */
}
```

You can mix fixed and flexible sizes:

```css
.container {
  display: grid;
  grid-template-columns: 200px 1fr 1fr; /* first column fixed at 200px, other two share remaining space equally */
}
```

## repeat() — avoid repetitive typing

```css
.container {
  display: grid;
  grid-template-columns: repeat(4, 1fr); /* same as: 1fr 1fr 1fr 1fr */
}
```

## gap — spacing between grid cells

```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px; /* spacing between rows AND columns */
  /* or separately: row-gap: 20px; column-gap: 10px; */
}
```

## Placing items into specific spots

Every grid line has a number, starting at 1. You can tell a specific item exactly where to go using `grid-column` and `grid-row`.

```css
.item-1 {
  grid-column: 1 / 3; /* start at column line 1, end at column line 3 (spans 2 columns) */
  grid-row: 1 / 2;
}
```

Shorthand using `span`:
```css
.item-1 {
  grid-column: span 2; /* spans across 2 columns, wherever it naturally falls */
}
```

**Real-world use case:** A "featured" article on a blog homepage that's twice as wide as the other articles.

## grid-template-areas — the most intuitive way to build layouts

This lets you literally **draw** your layout using named areas, which is one of the most beloved Grid features because it reads almost like a picture.

```css
.container {
  display: grid;
  grid-template-columns: 200px 1fr;
  grid-template-rows: auto 1fr auto;
  grid-template-areas:
    "sidebar header"
    "sidebar main"
    "sidebar footer";
  height: 100vh;
}

.header { grid-area: header; }
.sidebar { grid-area: sidebar; }
.main    { grid-area: main; }
.footer  { grid-area: footer; }
```

Just by looking at `grid-template-areas`, you can visually understand this is a classic layout: a sidebar on the left spanning the full height, with a header, main content, and footer stacked on the right.

## Responsive Grids with auto-fit / auto-fill and minmax()

This combination creates a grid that **automatically adjusts** the number of columns based on available space — extremely useful for responsive design without writing a single media query.

```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 20px;
}
```

This says: "Fit as many columns as possible, each at least 200px wide, and let them grow to fill leftover space equally." On a wide screen you might get 5 columns; on a narrow screen, just 1 or 2 — automatically, with no extra code.

## Aligning items in a grid

```css
.container {
  display: grid;
  justify-items: center; /* aligns items horizontally within their cell */
  align-items: center;   /* aligns items vertically within their cell */
}
```

## Key Takeaways

- Grid handles **two-dimensional** layouts (rows + columns); Flexbox handles **one-dimensional** layouts.
- `grid-template-columns` / `grid-template-rows` define the structure of the grid.
- The `fr` unit distributes available space proportionally.
- `grid-template-areas` lets you visually design layouts using named regions.
- `repeat(auto-fit, minmax(...))` creates powerful responsive grids with minimal code.

## Practice Exercise

Build a page layout with a header, sidebar, main content area, and footer using `grid-template-areas`. Then create a separate photo gallery grid using `repeat(auto-fit, minmax(150px, 1fr))` and observe how it responds when you resize the browser window.
