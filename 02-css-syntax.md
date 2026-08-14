# Lecture 2: CSS Syntax — Selectors, Properties, and Values

## The basic building block of CSS: the Rule

Every piece of CSS is written as a **rule**. A rule has this shape:

```css
selector {
  property: value;
  property: value;
}
```

Let's break this down piece by piece using a real example:

```css
p {
  color: green;
  font-size: 18px;
}
```

### 1. Selector
`p` — This tells the browser **which HTML element(s)** to style. In this case, every `<p>` (paragraph) tag on the page.

### 2. Declaration Block
The `{ }` curly braces contain everything that describes **how** the element should look. Everything inside is called the **declaration block**.

### 3. Declaration
Each line like `color: green;` is called a **declaration**. A declaration always has two parts separated by a colon:
- **Property** — the aspect you want to style (e.g., `color`, `font-size`, `margin`)
- **Value** — the setting you want for that property (e.g., `green`, `18px`)

### 4. The Semicolon
Each declaration must end with a semicolon `;`. This tells the browser "this declaration is finished, move to the next one." Forgetting a semicolon is one of the most common beginner mistakes.

## Full example with explanation

```css
h1 {
  color: navy;         /* text color */
  font-size: 40px;      /* size of the text */
  text-align: center;   /* aligns text in the center */
}
```

This rule says: "For every `<h1>` element, make the text navy blue, 40 pixels large, and center-aligned."

## Comments in CSS

You can write notes to yourself (or teammates) using comments. The browser ignores anything inside `/* ... */`.

```css
/* This is a comment and will not affect the design */
p {
  color: black;
}
```

## Multiple selectors, one rule

If several elements should share the same style, separate the selectors with commas:

```css
h1, h2, h3 {
  font-family: Arial, sans-serif;
  color: darkslategray;
}
```

This applies the same font and color to all `<h1>`, `<h2>`, and `<h3>` tags.

## Common beginner mistakes

| Mistake | Problem | Fix |
|---|---|---|
| `color: blue` (no semicolon) | Next declaration may break | Add `;` |
| `color = blue;` | Wrong symbol used | Use `:` not `=` |
| `Color: Blue;` | Property/value should be lowercase (usually) | Use `color: blue;` |
| Missing `{ }` | Rule won't apply at all | Always wrap declarations in curly braces |

## Key Takeaways

- A CSS rule = **selector** + **declaration block**.
- A declaration block contains one or more **declarations**.
- A declaration = **property** + **value**, separated by a colon, ending with a semicolon.
- Comments use `/* */` and are ignored by the browser.
- You can group selectors with commas to apply the same styles to multiple elements.

## Practice Exercise

Write a CSS rule that makes every `<h2>` element have a gray color, a font size of 24px, and italic text (`font-style: italic;`). Add a comment explaining what the rule does.
