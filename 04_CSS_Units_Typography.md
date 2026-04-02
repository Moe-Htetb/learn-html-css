## CSS Units + Typography (Beginner Friendly)

### Why units matter
CSS uses units to describe sizes like font-size, spacing, width/height, etc.
Choosing the right unit helps your design look good on different screen sizes.

---

## Common Units

### px (pixels)
Simple and predictable.

```css
h1 { font-size: 32px; }
.box { border-radius: 12px; }
```

Good for:
- borders
- shadows
- small fixed details

---

### % (percent)
Relative to the parent’s size (often width).

```css
.container { width: 80%; }
img { width: 100%; height: auto; }
```

---

### em (relative to current element’s font-size)
If an element has `font-size: 20px`, then `1em = 20px` for that element.

```css
.title {
  font-size: 20px;
  margin-bottom: 1em; /* = 20px */
}
```

Gotcha: em can “compound” when nested.

---

### rem (relative to root font-size)
`1rem` is based on the root element (`html`) font-size.
This makes spacing more consistent.

```css
html { font-size: 16px; }

p { font-size: 1rem; }    /* 16px */
h1 { font-size: 2rem; }   /* 32px */
.card { padding: 1.25rem; } /* 20px */
```

---

### vw / vh (viewport width/height)
Relative to the browser window.

```css
.hero { min-height: 100vh; }
.banner { width: 100vw; }
```

Good for:
- full-screen sections

Be careful with:
- mobile browser UI (address bar) can affect `vh`

---

## Typography Basics

### font-family
Always provide fallbacks.

```css
body {
  font-family: system-ui, -apple-system, "Segoe UI", Roboto, Arial, sans-serif;
}
```

---

### font-size
Beginner-friendly approach:
- keep `html` at 16px (default)
- use `rem` for scaling

```css
body { font-size: 1rem; }
h1 { font-size: 2rem; }
h2 { font-size: 1.5rem; }
```

---

### line-height (very important for readability)
Often best without units.

```css
body { line-height: 1.6; }
```

---

### font-weight
Common weights: 400 (normal), 600 (semi-bold), 700 (bold)

```css
h1 { font-weight: 700; }
.subtitle { font-weight: 500; }
```

---

### letter-spacing
Small changes can help headings.

```css
h1 { letter-spacing: -0.02em; }
.caps { letter-spacing: 0.08em; text-transform: uppercase; }
```

---

## Practice
1) Set `body` font-family + line-height and see how the whole page becomes more readable.
2) Create a `.card` and set padding in `rem`. Change `html { font-size: ... }` and watch spacing scale.
