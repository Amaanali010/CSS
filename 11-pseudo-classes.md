# Lecture 11: Pseudo-classes — :hover, :focus, :nth-child()

## What is a pseudo-class?

A pseudo-class is a special keyword added to a selector that targets an element in a **specific state or condition**, rather than by its tag, class, or ID. It starts with a single colon `:`.

General syntax:
```css
selector:pseudo-class {
  property: value;
}
```

Pseudo-classes let you style things like "when the mouse is hovering," "when an input is focused," or "the third item in a list" — states that pure HTML/CSS selectors alone can't describe.

## :hover — when the mouse is over an element

```css
button:hover {
  background-color: darkblue;
  cursor: pointer;
}
```

This style only applies while the user's mouse pointer is resting on top of the button. The moment the mouse moves away, the style reverts.

**Common use case:** Buttons, links, and cards that visually respond to mouse movement, giving the user feedback that something is clickable/interactive.

## :focus — when an element is selected/active for input

```css
input:focus {
  border-color: blue;
  outline: none;
}
```

This applies when an element (usually a form input) is currently selected — for example, after the user clicks into a text box or tabs to it with the keyboard.

**Important for accessibility:** Never fully remove focus styles without replacing them with something visible. Keyboard users rely on focus styles to know where they are on the page.

## :active — while an element is being clicked

```css
button:active {
  transform: scale(0.98); /* slightly shrinks the button while pressed */
}
```

This applies only during the exact moment the mouse button is held down on the element.

### The order matters: LVHA

When styling links, the recommended order is **L-V-H-A**: `:link`, `:visited`, `:hover`, `:active`. Writing them in this order avoids styles unexpectedly overriding each other.

```css
a:link    { color: blue; }
a:visited { color: purple; }
a:hover   { color: red; }
a:active  { color: orange; }
```

## :nth-child() — targeting elements by position

This is one of the most powerful pseudo-classes. It selects an element based on its **position among its siblings**.

```css
li:nth-child(2) {
  color: red; /* targets only the 2nd <li> in its parent */
}
```

### Common patterns

```css
li:nth-child(odd)  { background: #f2f2f2; } /* 1st, 3rd, 5th... — great for striped tables */
li:nth-child(even) { background: #ffffff; } /* 2nd, 4th, 6th... */

li:nth-child(3)     { font-weight: bold; }   /* exactly the 3rd item */
li:nth-child(3n)    { color: green; }        /* every 3rd item: 3rd, 6th, 9th... */
li:nth-child(n+3)   { opacity: 0.5; }        /* the 3rd item and every one after it */
```

**Real-world use case:** Striped (zebra) table rows, styling every other card in a grid differently, highlighting the first or last item in a navigation list.

## Other useful pseudo-classes

```css
li:first-child { font-weight: bold; }   /* the first child among siblings */
li:last-child  { border-bottom: none; } /* the last child among siblings */

input:disabled { opacity: 0.5; }        /* disabled form fields */
input:checked  { border-color: green; } /* a checked checkbox/radio button */

p:empty { display: none; }              /* elements with no content at all */
```

## Combining pseudo-classes with other selectors

```css
.card:hover {
  box-shadow: 0 4px 12px rgba(0,0,0,0.2);
}

nav a:hover {
  text-decoration: underline;
}

table tr:nth-child(even) {
  background-color: #f9f9f9;
}
```

## Key Takeaways

- Pseudo-classes (written with `:`) target elements based on **state** or **position**, not just tag/class/ID.
- `:hover` responds to mouse-over; `:focus` responds to keyboard/click selection; `:active` responds to the moment of clicking.
- `:nth-child()` selects elements by their position among siblings — very useful for patterns like striped rows.
- Always keep visible `:focus` styles for accessibility.

## Practice Exercise

Create a list of 6 items. Style even items with a light gray background using `:nth-child(even)`. Then create a button that changes background color on `:hover` and slightly shrinks on `:active`.
