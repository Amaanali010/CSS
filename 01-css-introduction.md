# Lecture 1: CSS Introduction

## What is CSS?

CSS stands for **Cascading Style Sheets**. It is the language used to make web pages look nice.

Think of it this way:
- **HTML** = the skeleton of a webpage (the structure: headings, paragraphs, images, buttons)
- **CSS** = the skin and clothes (the colors, fonts, spacing, layout)
- **JavaScript** = the muscles and brain (the behavior and interactivity)

Without CSS, every webpage would look like a plain black-and-white document with no design at all.

## Why do we need CSS?

Imagine a house built with only bricks and no paint, no furniture arrangement, and no design. It would work, but it wouldn't be pleasant to live in. CSS is what turns a "working" webpage into a "beautiful and usable" webpage.

CSS lets us control:
- Colors and backgrounds
- Fonts and text size
- Spacing between elements
- Layout (where things sit on the page)
- Animations and transitions
- How a page looks on phones vs. computers

## How does CSS work?

CSS works by **selecting** HTML elements and then **applying styles** to them.

The basic idea has three parts:
1. **Selector** — which element do you want to style?
2. **Property** — what feature do you want to change (color, size, spacing)?
3. **Value** — what should that feature be set to?

### A simple example

```html
<!-- HTML file -->
<h1>Hello World</h1>
```

```css
/* CSS file */
h1 {
  color: blue;
  font-size: 32px;
}
```

Here:
- `h1` is the selector (it targets the `<h1>` tag)
- `color` and `font-size` are properties
- `blue` and `32px` are values

Result: the heading "Hello World" will now appear in blue color and a larger font size.

## Three ways to add CSS to HTML

1. **Inline CSS** — written directly inside an HTML tag using the `style` attribute.
```html
<h1 style="color: red;">Hello</h1>
```

2. **Internal CSS** — written inside a `<style>` tag in the HTML file's `<head>`.
```html
<head>
  <style>
    h1 { color: red; }
  </style>
</head>
```

3. **External CSS** — written in a separate `.css` file and linked to the HTML file. **This is the best and most common method** because it keeps design separate from structure, and one CSS file can style many HTML pages.
```html
<head>
  <link rel="stylesheet" href="style.css">
</head>
```

## The word "Cascading" — what does it mean?

"Cascading" means styles can come from multiple places (inline, internal, external, browser defaults), and CSS has rules to decide **which style wins** when there's a conflict. Generally:
- Inline styles beat internal styles
- Internal/external styles beat browser default styles
- More specific selectors beat general ones
- Styles written later can override styles written earlier (if they have equal specificity)

We will explore this "who wins" concept more deeply in later lectures, but for now, just remember: CSS rules can stack and override each other, like water flowing (cascading) down layers.

## Key Takeaways

- CSS is the language that styles and designs webpages.
- It works by selecting HTML elements and applying property-value pairs to them.
- External CSS files are the preferred method in real projects.
- "Cascading" means multiple style rules can apply, and CSS decides which one wins.

## Practice Exercise

Create a simple HTML file with a heading and a paragraph. Link an external CSS file to it, and try changing the heading's color and the paragraph's font size.
