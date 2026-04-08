## CSS Properties Guide: Flexbox + Grid

This file explains **CSS properties** directly, especially:
- `display: flex`
- `display: grid`
- related layout properties you use with each one

Use this as a quick reference while reading `css/flex_grid.css`.

---

## 1) `display` (the starting point)

`display` controls how an element behaves in layout.

```css
.box { display: block; }  /* new line, full width by default */
.row { display: flex; }   /* one-dimensional layout */
.grid { display: grid; }  /* two-dimensional layout */
```

- Use **flex** for row/column alignment.
- Use **grid** for rows + columns together.

---

## 2) Flexbox Properties (Parent Container)

### `display: flex`
Turns children into flex items.

```css
.container {
  display: flex;
}
```

### `flex-direction`
Main axis direction.

```css
flex-direction: row;         /* left to right (default) */
flex-direction: column;      /* top to bottom */
```

### `justify-content`
Aligns items along the **main axis**.

```css
justify-content: flex-start;
justify-content: center;
justify-content: space-between;
justify-content: space-around;
```

### `align-items`
Aligns items along the **cross axis**.

```css
align-items: stretch;      /* default */
align-items: center;
align-items: flex-start;
align-items: flex-end;
```

### `flex-wrap`
Controls wrapping.

```css
flex-wrap: nowrap;   /* default, single line */
flex-wrap: wrap;     /* move to next line if needed */
```

### `gap`
Space between flex items (better than margins in many cases).

```css
gap: 1rem;
```

---

## 3) Flex Item Properties (Children)

### `flex-grow`, `flex-shrink`, `flex-basis`
Common shorthand:

```css
flex: 1 1 200px;
```

Meaning:
- `1` grow if extra space exists
- `1` shrink if needed
- `200px` preferred starting size

### `align-self`
Override one item’s cross-axis alignment.

```css
.special-item {
  align-self: flex-start;
}
```

### `margin-top: auto` (very useful)
In a column flex card, pushes footer/button to bottom.

```css
.card {
  display: flex;
  flex-direction: column;
}
.card-footer {
  margin-top: auto;
}
```

---

## 4) Grid Properties (Parent Container)

### `display: grid`
Turns children into grid items.

```css
.grid {
  display: grid;
}
```

### `grid-template-columns`
Defines column structure.

```css
grid-template-columns: 1fr 1fr 1fr;   /* 3 equal columns */
grid-template-columns: 220px 1fr;     /* fixed sidebar + flexible content */
```

### `grid-template-rows`
Defines row structure (optional, often auto).

```css
grid-template-rows: auto auto;
```

### `gap`
Space between rows and columns.

```css
gap: 1rem;
```

### `repeat()`
Cleaner way to write repeated tracks.

```css
grid-template-columns: repeat(3, 1fr);
```

### `minmax()`
Set min and max track size.

```css
grid-template-columns: repeat(3, minmax(200px, 1fr));
```

### `auto-fit` with `minmax()` (responsive favorite)

```css
grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
```

Behavior:
- Creates as many columns as fit
- Each column at least `200px`
- Expands columns to fill extra width

### `grid-template-areas`
Named layout areas.

```css
.layout {
  display: grid;
  grid-template-areas:
    "header header"
    "sidebar main"
    "footer footer";
}
```

Then assign areas:

```css
.header { grid-area: header; }
.sidebar { grid-area: sidebar; }
.main { grid-area: main; }
.footer { grid-area: footer; }
```

---

## 5) Grid Item Properties (Children)

### `grid-column` / `grid-row`
Make items span multiple tracks.

```css
.wide {
  grid-column: span 2;
}
```

### `place-self`
Align one item in its cell (shortcut for `align-self` + `justify-self`).

```css
.item {
  place-self: center;
}
```

---

## 6) Related Layout Properties

### `width: min(...)`
Useful for page wrappers.

```css
width: min(960px, 92%);
```

### `position: sticky`
Keeps header visible while scrolling.

```css
position: sticky;
top: 0;
```

### `box-sizing: border-box`
Makes sizing easier (includes padding + border in width).

```css
*,
*::before,
*::after {
  box-sizing: border-box;
}
```

### Media query (responsive changes)

```css
@media (max-width: 720px) {
  .grid {
    grid-template-columns: 1fr;
  }
}
```

---

## 7) Flex vs Grid (When to use which)

- Use **Flexbox** for:
  - navbar rows
  - button groups
  - centering content
  - 1D layouts (row OR column)

- Use **Grid** for:
  - card galleries
  - dashboard/page sections
  - 2D layouts (rows AND columns)

- Use **both together**:
  - grid for overall page
  - flex inside components

---

## 8) Common mistakes

1. Setting `justify-content` on child instead of parent.
2. Forgetting `display: flex` / `display: grid` on container.
3. Using fixed widths everywhere (breaks responsiveness).
4. Not adding media queries for small screens.
5. Using margins for spacing when `gap` is cleaner.

---

## Quick Cheat Sheet

```css
/* FLEX */
.parent {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;
}

/* GRID */
.parent {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1rem;
}
```
