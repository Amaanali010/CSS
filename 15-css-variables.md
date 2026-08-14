# Lecture 15: CSS Variables — Reusable Values with --variable-name

## What is a CSS Variable?

A CSS Variable (officially called a **Custom Property**) lets you store a value — a color, a size, a font, anything — **once**, give it a name, and reuse it anywhere in your stylesheet. If you ever need to change that value, you only update it in **one place**, and it updates everywhere it's used.

Think of it like a labeled jar: you put a value in a jar labeled `--main-color`, and any time you need that color, you just grab it from the jar instead of retyping the exact color code.

## Why do we need this?

Imagine a website uses the brand color `#3498db` in 50 different places across your CSS file. If the design changes to a new blue, you'd have to manually find and replace it 50 times — risky and easy to make mistakes. With a variable, you change it once.

## Declaring a Variable

Variables are declared with two dashes `--` followed by a name, and are usually defined inside the `:root` selector so they're available **globally** across the whole page.

```css
:root {
  --main-color: #3498db;
  --spacing: 16px;
  --font-main: 'Arial', sans-serif;
}
```

**What is `:root`?** It refers to the highest-level element in the document (essentially the `<html>` tag), so anything defined there is accessible everywhere on the page.

## Using a Variable

You retrieve a variable's value using the `var()` function.

```css
h1 {
  color: var(--main-color);
  font-family: var(--font-main);
}

.card {
  padding: var(--spacing);
  border: 1px solid var(--main-color);
}
```

Now, `--main-color` is used in two different rules. Change it once in `:root`, and both update automatically.

## Fallback Values

`var()` can accept a second argument — a fallback value used if the variable isn't defined or fails to load.

```css
p {
  color: var(--text-color, black); /* uses black if --text-color isn't set */
}
```

## Variables Can Be Scoped (not just global)

While `:root` makes a variable global, you can also define variables inside a specific selector, and it will only apply within that element (and its children).

```css
.dark-card {
  --card-bg: #222;
  --card-text: #fff;

  background-color: var(--card-bg);
  color: var(--card-text);
}

.light-card {
  --card-bg: #fff;
  --card-text: #222;

  background-color: var(--card-bg);
  color: var(--card-text);
}
```

This lets different sections of a page use "the same variable name" but with different actual values depending on context — very powerful for theming.

## Real-World Use Case: Dark Mode Toggle

CSS Variables make theme switching much easier, especially when combined with JavaScript.

```css
:root {
  --bg-color: white;
  --text-color: black;
}

body {
  background-color: var(--bg-color);
  color: var(--text-color);
  transition: background-color 0.3s, color 0.3s;
}

body.dark-mode {
  --bg-color: #121212;
  --text-color: #f1f1f1;
}
```

With JavaScript, you'd simply toggle the `dark-mode` class on `<body>`, and because the variables change, every element using `var(--bg-color)` and `var(--text-color)` updates instantly — no need to rewrite dozens of rules.

## Variables vs. Sass/LESS Variables (just a note)

If you've heard of Sass or LESS (CSS preprocessors), they also have variables (`$variable` in Sass). The key difference: **CSS Variables are native to the browser and can change dynamically** (e.g., via JavaScript or media queries) — Sass variables are fixed at compile time and can't change once the CSS is generated. This makes native CSS Variables especially powerful for interactive, dynamic designs like theming.

## A Practical Example: A consistent design system

```css
:root {
  --color-primary: #6c5ce7;
  --color-secondary: #00cec9;
  --color-text: #2d3436;
  --spacing-sm: 8px;
  --spacing-md: 16px;
  --spacing-lg: 32px;
  --radius: 8px;
}

.button {
  background-color: var(--color-primary);
  color: white;
  padding: var(--spacing-sm) var(--spacing-md);
  border-radius: var(--radius);
}

.card {
  padding: var(--spacing-lg);
  border-radius: var(--radius);
  color: var(--color-text);
}
```

This approach — defining a small set of reusable design values — is exactly how professional design systems are built.

## Key Takeaways

- CSS Variables (custom properties) are declared with `--name: value;` and read with `var(--name)`.
- Declaring them inside `:root` makes them available globally across the page.
- They can be scoped to specific elements for local overrides (great for themes).
- `var()` supports a fallback value as a second argument.
- Unlike Sass/LESS variables, native CSS Variables can update dynamically in the browser (e.g., dark mode toggles).

## Practice Exercise

Create `:root` variables for a primary color, a secondary color, and a spacing value. Use them to style a button and a card. Then create a `.dark-mode` class that overrides the color variables, and toggle it to see the whole page theme change instantly.
