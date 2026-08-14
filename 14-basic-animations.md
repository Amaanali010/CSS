# Lecture 14: Basic Animations — @keyframes

## Transitions vs. Animations — what's the difference?

- **Transitions** (Lecture 13) animate between **two states only** (e.g., normal → hover), and they need a trigger like `:hover` or a class change.
- **Animations** using `@keyframes` can have **multiple steps**, can repeat automatically, and don't need a trigger — they can run the moment the page loads, on a loop, forever if you want.

## Step 1: Define the Animation with @keyframes

`@keyframes` describes **what happens at each stage** of the animation, using percentages from 0% (start) to 100% (end).

```css
@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
```

This defines an animation named `fadeIn` that goes from fully invisible to fully visible.

You can also use `from` and `to` as shortcuts for `0%` and `100%`:

```css
@keyframes fadeIn {
  from { opacity: 0; }
  to   { opacity: 1; }
}
```

## Step 2: Apply the Animation to an Element

Once defined, you attach the animation to an element using the `animation` property.

```css
.box {
  animation-name: fadeIn;
  animation-duration: 2s;
}
```

Or using the shorthand:
```css
.box {
  animation: fadeIn 2s ease-in;
}
```

## Multi-Step Animations

You're not limited to just start and end — you can add as many percentage steps as you like.

```css
@keyframes bounce {
  0%   { transform: translateY(0); }
  50%  { transform: translateY(-30px); }
  100% { transform: translateY(0); }
}

.ball {
  animation: bounce 1s ease-in-out infinite;
}
```

This makes an element rise up and come back down repeatedly — a bouncing effect.

## Key Animation Properties

```css
.element {
  animation-name: bounce;             /* which @keyframes rule to use */
  animation-duration: 1s;             /* how long ONE cycle takes */
  animation-timing-function: ease;    /* speed curve, same values as transitions */
  animation-delay: 0.5s;              /* wait before starting */
  animation-iteration-count: infinite; /* how many times it repeats (a number, or "infinite") */
  animation-direction: alternate;     /* normal, reverse, alternate, alternate-reverse */
  animation-fill-mode: forwards;      /* keeps the final keyframe's styles after it ends */
}
```

### Shorthand order
```css
animation: name duration timing-function delay iteration-count direction fill-mode;
```

Example:
```css
.element {
  animation: bounce 1s ease-in-out 0s infinite alternate;
}
```

## Explaining the trickier properties

- **`animation-iteration-count`**: `1` runs it once (default); `3` runs it 3 times; `infinite` loops forever.
- **`animation-direction`**: `normal` plays 0%→100% each time; `alternate` plays 0%→100% then 100%→0%, back and forth (like a real bounce).
- **`animation-fill-mode: forwards`**: without this, once the animation ends, the element "snaps back" to its original (pre-animation) styles. `forwards` keeps it looking like the final keyframe.

## A Complete, Practical Example: Loading Spinner

```css
.spinner {
  width: 40px;
  height: 40px;
  border: 4px solid #ddd;
  border-top: 4px solid #333;
  border-radius: 50%;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  from { transform: rotate(0deg); }
  to   { transform: rotate(360deg); }
}
```

This is the classic circular loading spinner seen across countless websites — built with just a few lines of CSS.

## Another Example: Attention-Grabbing "Pulse" Button

```css
@keyframes pulse {
  0%   { transform: scale(1); }
  50%  { transform: scale(1.1); }
  100% { transform: scale(1); }
}

.notification-dot {
  animation: pulse 1.5s ease-in-out infinite;
}
```

## Key Takeaways

- `@keyframes` defines the stages of an animation using percentages (or `from`/`to`).
- The `animation` property attaches a defined keyframe animation to an element.
- Unlike transitions, animations can run automatically, loop, and have multiple steps.
- `animation-iteration-count: infinite` loops forever; `animation-fill-mode: forwards` keeps the last frame's styles after finishing.

## Practice Exercise

Create a `@keyframes` animation called `slideIn` that moves an element from `translateX(-100%)` (off-screen left) to `translateX(0)` (its normal position), with a fade-in effect. Apply it so it runs once when the page loads.
