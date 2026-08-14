# Lecture 4: Colors & Backgrounds

## Ways to define color in CSS

CSS gives you several ways to describe a color. All of them are valid — you just pick whichever is easiest for the situation.

### 1. Named colors
CSS has about 140 built-in color names.

```css
h1 {
  color: red;
}
```
Easy to read, but limited — you can't get an exact custom shade.

### 2. HEX codes
A hexadecimal code represents Red, Green, and Blue values using 6 characters (2 per color).

```css
h1 {
  color: #ff0000; /* red */
}
```
- `#ff0000` → full red, no green, no blue
- `#000000` → black (no color at all)
- `#ffffff` → white (full of every color)

This is the most commonly used method in real projects because design tools (like Figma) usually give you hex codes directly.

### 3. RGB
RGB stands for Red, Green, Blue. Each value ranges from 0 to 255.

```css
h1 {
  color: rgb(255, 0, 0); /* red */
}
```

### 4. RGBA
Same as RGB, but with an added **alpha** value for transparency (0 = fully transparent, 1 = fully solid).

```css
h1 {
  color: rgba(255, 0, 0, 0.5); /* red, 50% see-through */
}
```

### 5. HSL
HSL stands for Hue, Saturation, Lightness. Many designers find this the most intuitive because it's close to how humans naturally think about color.

```css
h1 {
  color: hsl(0, 100%, 50%); /* red */
}
```
- **Hue** (0–360): the color itself, like a color wheel (0 = red, 120 = green, 240 = blue)
- **Saturation** (0–100%): how vivid or dull the color is
- **Lightness** (0–100%): how light or dark the color is

## Text Color vs. Background Color

```css
p {
  color: white;              /* the text color */
  background-color: black;   /* the background behind the text */
}
```

`color` always refers to the **text/foreground**, while `background-color` refers to the area **behind** the element.

## Background Properties

CSS gives you several background-related properties:

```css
div {
  background-color: lightblue;
  background-image: url('photo.jpg');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}
```

- `background-image` — sets an image as the background
- `background-repeat` — controls if the image repeats (`repeat`, `no-repeat`, `repeat-x`, `repeat-y`)
- `background-size` — controls how the image scales (`cover` fills the area, `contain` fits inside without cropping)
- `background-position` — controls where the image starts (`center`, `top left`, etc.)

### Shorthand background

You can combine many of these into one line:

```css
div {
  background: lightblue url('photo.jpg') no-repeat center/cover;
}
```

## Gradients (a bonus but very common feature)

A gradient smoothly blends between two or more colors, and is technically a type of `background-image`.

```css
div {
  background: linear-gradient(to right, red, yellow);
}
```

This creates a background that fades from red on the left to yellow on the right.

## Key Takeaways

- Colors can be written as **named colors**, **HEX**, **RGB**, **RGBA**, or **HSL**.
- Use RGBA or HSL(a) when you need transparency.
- `color` styles text; `background-color` styles the area behind an element.
- `background-image`, `background-size`, `background-position`, and `background-repeat` control image backgrounds.
- Gradients are created using `linear-gradient()` or `radial-gradient()`.

## Practice Exercise

Create a `<div>` with a gradient background going from blue to purple. Inside it, add a paragraph with white text and 70% opacity using RGBA.
