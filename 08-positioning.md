# Lecture 8: Positioning — static, relative, absolute, fixed, sticky

The `position` property controls **how an element is placed** on the page, and whether it can be moved using the `top`, `right`, `bottom`, and `left` properties.

## 1. position: static (the default)

Every element is `static` by default. It simply follows the **normal document flow** — top to bottom, left to right, in the order it's written in HTML.

```css
div {
  position: static;
}
```

`top`, `left`, `right`, `bottom` have **no effect** on static elements. If you never set `position`, this is what you get.

## 2. position: relative

The element stays in the normal document flow (it still takes up its original space), but you can now **nudge it** away from its normal position using `top`, `left`, `right`, `bottom`.

```css
div {
  position: relative;
  top: 20px;   /* moves it 20px down from where it would normally be */
  left: 10px;  /* moves it 10px right from where it would normally be */
}
```

**Important:** The space the element *originally* occupied is still reserved — other elements don't move to fill the gap. It just visually shifts.

**Key use case:** `position: relative` is also often used just to create a **reference point** for a child element that uses `position: absolute` (explained next).

## 3. position: absolute

The element is **removed from the normal document flow** completely (other elements act like it isn't there) and is positioned relative to its **nearest positioned ancestor** — meaning the closest parent that has `position: relative`, `absolute`, `fixed`, or `sticky`.

If no ancestor is positioned, it positions itself relative to the entire page (`<html>`).

```css
.parent {
  position: relative; /* creates the reference point */
}
.child {
  position: absolute;
  top: 0;
  right: 0; /* places child in the top-right corner of .parent */
}
```

**Common use case:** Badges, tooltips, close buttons ("X") in the corner of a card or modal.

## 4. position: fixed

The element is removed from the document flow and positioned relative to the **browser window (viewport)**. It stays in the exact same spot on screen **even when the page is scrolled**.

```css
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
}
```

**Common use case:** Sticky navigation bars, "back to top" buttons, chat widgets that always stay visible.

## 5. position: sticky

A hybrid between `relative` and `fixed`. The element behaves like `relative` (in normal flow) **until** the page scrolls to a certain point, then it "sticks" like `fixed` within its parent container.

```css
.section-header {
  position: sticky;
  top: 0; /* sticks to the top of the viewport once reached */
}
```

**Common use case:** Section headers in a long list (like contact names grouped alphabetically), table headers that stay visible while scrolling.

## Comparison Table

| Value | In normal flow? | Moves with scroll? | Positioned relative to |
|---|---|---|---|
| `static` | Yes | Yes | N/A (default) |
| `relative` | Yes (keeps its space) | Yes | Its own original position |
| `absolute` | No | Yes (scrolls with page unless ancestor is fixed) | Nearest positioned ancestor |
| `fixed` | No | No (stays on screen) | The browser viewport |
| `sticky` | Yes, until threshold | Switches to fixed-like after threshold | Nearest scrolling ancestor |

## z-index — controlling stacking order

When elements overlap (common with `absolute` and `fixed`), `z-index` decides which one appears on top. Higher numbers appear in front of lower numbers.

```css
.modal {
  position: fixed;
  z-index: 100; /* appears above elements with a lower z-index */
}
```

**Note:** `z-index` only works on elements that have a `position` value other than `static`.

## Key Takeaways

- `static` is the default — no special positioning.
- `relative` shifts an element from its normal spot while still reserving its original space.
- `absolute` removes the element from flow and positions it relative to its nearest positioned ancestor.
- `fixed` sticks the element to the browser window, ignoring scroll.
- `sticky` acts relative until a scroll threshold, then acts fixed.
- `z-index` controls stacking order for overlapping positioned elements.

## Practice Exercise

Build a card with `position: relative`. Inside it, add a small "NEW" badge with `position: absolute; top: 10px; right: 10px;`. Then create a navigation bar with `position: fixed` at the top of the page.
