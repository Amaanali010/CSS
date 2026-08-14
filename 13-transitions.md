# Lecture 13: Transitions — Simple Animations Between States

## What is a CSS Transition?

A transition lets a property change **smoothly over time**, instead of changing instantly/abruptly. Without a transition, if you change a button's color on hover, it snaps to the new color immediately. With a transition, it smoothly fades from one color to the other.

## Basic Syntax

```css
button {
  background-color: blue;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: darkblue;
}
```

Here, when the user hovers over the button, instead of an instant color-snap, the background smoothly fades from blue to dark blue over 0.3 seconds.

## The Four Parts of a Transition

```css
transition: property duration timing-function delay;
```

### 1. Property
Which CSS property should animate. You can target a specific one, or use `all` to animate every property that changes.

```css
transition: background-color 0.3s;  /* only animates background-color */
transition: all 0.3s;               /* animates any property that changes */
```

### 2. Duration
How long the transition takes, in seconds (`s`) or milliseconds (`ms`).

```css
transition: transform 0.5s; /* half a second */
```

### 3. Timing Function (easing)
Controls the **speed curve** of the animation — whether it moves at a constant speed or speeds up/slows down.

```css
transition: transform 0.5s ease-in-out;
```

Common values:
- `linear` — constant speed throughout
- `ease` — starts slow, speeds up, ends slow (default, feels natural)
- `ease-in` — starts slow, ends fast
- `ease-out` — starts fast, ends slow
- `ease-in-out` — slow start and slow end, faster in the middle

### 4. Delay (optional)
How long to wait before the transition starts.

```css
transition: opacity 0.3s ease 0.2s; /* waits 0.2s before starting */
```

## Transitioning Multiple Properties

You can animate several properties at once by separating them with commas:

```css
.card {
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 16px rgba(0,0,0,0.2);
}
```

This creates a popular "lift up" hover effect where a card rises slightly and gains a shadow.

## What properties can be animated?

Most numeric or color-based properties can transition smoothly, including:
- `color`, `background-color`, `border-color`
- `width`, `height`
- `opacity`
- `transform` (scale, rotate, translate — very commonly animated)
- `box-shadow`

Properties like `display` cannot be smoothly transitioned (an element is either shown or not — there's no "halfway" state).

## Common Real-World Examples

### Button hover effect
```css
button {
  background-color: #4CAF50;
  transition: background-color 0.3s ease, transform 0.2s ease;
}
button:hover {
  background-color: #45a049;
  transform: scale(1.05);
}
```

### Fading in on hover
```css
.overlay {
  opacity: 0;
  transition: opacity 0.4s ease;
}
.container:hover .overlay {
  opacity: 1;
}
```

### Smooth link underline
```css
a {
  border-bottom: 2px solid transparent;
  transition: border-color 0.3s;
}
a:hover {
  border-bottom-color: currentColor;
}
```

## Key Takeaways

- Transitions make property changes happen smoothly instead of instantly.
- Syntax: `transition: property duration timing-function delay;`
- `ease` is the default and usually feels the most natural.
- You can transition multiple properties by separating them with commas.
- Commonly paired with `:hover`, `:focus`, and class toggles (via JavaScript).

## Practice Exercise

Create a button that smoothly changes its background color and slightly grows in size (`transform: scale()`) when hovered. Try different `timing-function` values (`linear`, `ease-in`, `ease-out`) and notice how the "feel" of the animation changes.
