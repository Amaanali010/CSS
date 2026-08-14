# Lecture 3: Selectors — Element, Class, ID, Attribute

Selectors are how CSS finds the HTML elements it wants to style. Think of selectors as "addresses" — they tell CSS exactly where to apply the style.

## 1. Element Selector (Type Selector)

Selects **all** elements of a certain HTML tag.

```css
p {
  color: gray;
}
```

This styles every `<p>` on the page. It's simple but not very specific — you can't target just one paragraph this way.

## 2. Class Selector

A **class** lets you group elements and style them together. Classes are written in HTML using `class="name"` and selected in CSS with a **dot** (`.`).

```html
<p class="highlight">This is important.</p>
<p class="highlight">This is also important.</p>
<p>This is normal text.</p>
```

```css
.highlight {
  background-color: yellow;
  font-weight: bold;
}
```

Only the two paragraphs with `class="highlight"` will get the yellow background and bold text. The third paragraph stays unchanged.

**Key point:** Multiple elements can share the same class, and one element can have multiple classes:
```html
<p class="highlight large">Text here</p>
```

## 3. ID Selector

An **ID** targets exactly **one** unique element. IDs are written in HTML using `id="name"` and selected in CSS with a **hash** (`#`).

```html
<h1 id="main-title">Welcome to My Site</h1>
```

```css
#main-title {
  color: crimson;
  font-size: 48px;
}
```

**Important rule:** An `id` should be used only **once per page**. If you need to style multiple elements the same way, use a class instead.

### Class vs. ID — When to use which?

| | Class | ID |
|---|---|---|
| Symbol | `.` | `#` |
| Can reuse? | Yes, many elements | No, only one element |
| Common use | Styling groups of elements (buttons, cards) | Styling one unique element (a page header, a specific section) |

**Rule of thumb:** Use classes almost all the time. Use IDs sparingly, mainly for unique page landmarks or when JavaScript needs to find one specific element.

## 4. Attribute Selector

Selects elements based on an HTML **attribute** and/or its value.

```css
input[type="text"] {
  border: 1px solid gray;
}
```

This selects only `<input>` elements where `type="text"`, leaving other input types (like checkboxes) untouched.

More examples:

```css
/* Any element with a "title" attribute */
[title] {
  cursor: help;
}

/* Links that open in a new tab */
a[target="_blank"] {
  color: orange;
}

/* Class attribute that CONTAINS the word "btn" */
[class~="btn"] {
  padding: 10px;
}
```

## Combining Selectors

You can combine selectors to be more specific:

```css
p.highlight {
  color: red;
}
```
This only selects `<p>` elements that ALSO have `class="highlight"` (not other tags with that class).

```css
div#container p {
  margin: 0;
}
```
This selects `<p>` elements that are **inside** an element with `id="container"`.

## Key Takeaways

- **Element selector** (`p`) → styles all elements of that tag.
- **Class selector** (`.classname`) → styles all elements with that class; reusable.
- **ID selector** (`#idname`) → styles one unique element; use once per page.
- **Attribute selector** (`[attribute="value"]`) → styles elements based on their HTML attributes.
- Selectors can be combined for more precision.

## Practice Exercise

Create a page with three buttons. Give all of them a class called `btn` to style them the same (padding, color). Give just one of them an ID called `submit-btn` and give it a unique background color.
