## CSS Display + Layout Basics (Beginner Friendly)

### The `display` property (core concept)
`display` controls how an element behaves in layout.

Common values:
- `block`
- `inline`
- `inline-block`
- `none`
- `flex`
- `grid`

---

## block vs inline

### block
- starts on a new line
- can set width/height
- takes full width by default

Examples: `div`, `p`, `h1`, `section`

```css
div { display: block; }
```

### inline
- stays in the same line with text
- width/height usually don’t apply the same way
- padding/margin behave differently than block

Examples: `span`, `a`, `strong`

```css
span { display: inline; }
```

---

## inline-block (useful middle ground)
Behaves like inline (sits on a line) but accepts width/height like block.

```css
.chip {
  display: inline-block;
  padding: 6px 10px;
  border: 1px solid #ccc;
  border-radius: 999px;
}
```

---

## display: none
Removes the element from layout completely (it takes no space).

```css
.hidden { display: none; }
```

---

## Centering basics

### Center a block with fixed/max width

```css
.container {
  max-width: 900px;
  margin: 0 auto; /* left/right auto centers */
  padding: 0 16px;
}
```

---

## Flexbox (modern, common)
Best for arranging items in a row/column and aligning them.

```css
.row {
  display: flex;
  gap: 12px;
  align-items: center;     /* vertical alignment (in row direction) */
  justify-content: space-between; /* horizontal spacing */
}
```

Useful patterns:
- center both directions:

```css
.center {
  display: flex;
  align-items: center;
  justify-content: center;
}
```

---

## Grid (great for 2D layouts)

```css
.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}
```

---

## Practice
1) Make 3 `.chip` items with `inline-block`. Add margin/gap and observe spacing.
2) Make a `.row` with a logo on left and button on right using flexbox.
3) Make a 3-column grid of cards using CSS grid.
