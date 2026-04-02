## CSS Basics + Box Model (Beginner Friendly Notes)

### What is CSS?
**CSS (Cascading Style Sheets)** is used to style HTML: colors, sizes, spacing, layout, fonts, and more.

- **HTML** = structure (what content exists)
- **CSS** = presentation (how it looks)

---

### 3 Ways to Add CSS

#### 1) Inline CSS (inside an HTML tag)
Good for quick tests, but not recommended for real projects.

```html
<p style="color: red; font-size: 20px;">Hello</p>
```

#### 2) Internal CSS (in the HTML `<head>`)

```html
<head>
  <style>
    p { color: red; }
  </style>
</head>
```

#### 3) External CSS (recommended)
Create a `.css` file and link it.

```html
<head>
  <link rel="stylesheet" href="styles.css" />
</head>
```

```css
/* styles.css */
p { color: red; }
```

---

### CSS Syntax

```css
selector {
  property: value;
  property: value;
}
```

Example:

```css
h1 {
  color: navy;
  font-size: 32px;
}
```

- **selector**: which element(s) to style
- **property**: what you want to change
- **value**: the new setting

---

### Common Selectors (quick intro)

#### Element selector
Targets all elements of that type.

```css
p { color: #333; }
```

#### Class selector (very common)
Targets elements with a class attribute.

```css
.card { background: white; }
```

```html
<div class="card">...</div>
```

#### ID selector (use carefully)
Targets a single unique element.

```css
#header { padding: 16px; }
```

```html
<header id="header">...</header>
```

---

### Cascade, Specificity, and “Why didn’t my CSS work?”
CSS can conflict when multiple rules apply to the same element.

#### Cascade (order matters)
If specificity is equal, **the later rule wins**.

```css
p { color: blue; }
p { color: red; } /* wins */
```

#### Specificity (some selectors are “stronger”)
General idea (from weaker to stronger):

- element: `p`
- class: `.note`
- id: `#main`
- inline: `style="..."`

Example:

```css
p { color: blue; }
.note { color: green; }   /* stronger than p */
#main { color: purple; }  /* stronger than class */
```

#### Inheritance (some properties pass down)
Some properties like `color` and `font-family` often inherit from parent to child.

```css
body { font-family: Arial, sans-serif; }
```

---

## The CSS Box Model (Most Important Concept)
In CSS, **every element is a box**.

That box is made of (from inside to outside):

1) **Content** (text/image area)
2) **Padding** (space inside the border)
3) **Border** (line around padding+content)
4) **Margin** (space outside the border)

---

### Visualizing the Box Model

```css
.box {
  width: 200px;
  height: 100px;
  padding: 20px;
  border: 5px solid black;
  margin: 30px;
}
```

What you might expect vs what happens:
- **Content box** is `200 x 100`
- Padding adds space inside
- Border adds thickness
- Margin adds space outside

So the space the element “occupies” becomes bigger than `200 x 100` (unless you change box-sizing, see below).

---

### Width/Height: content box by default
By default, `width` and `height` apply only to the **content** area.

So total size is:

\[
\text{total width} = \text{content width} + (padding \times 2) + (border \times 2)
\]

For `.box` above:
- content width: 200
- padding left+right: 20+20 = 40
- border left+right: 5+5 = 10
- **total** = 200 + 40 + 10 = **250px**

---

### box-sizing (recommended!)
`box-sizing: border-box;` makes `width` include padding+border.
This is easier to reason about.

```css
.box {
  box-sizing: border-box;
  width: 200px;     /* now total visible width stays 200 */
  padding: 20px;
  border: 5px solid black;
}
```

Many projects set this globally:

```css
*,
*::before,
*::after {
  box-sizing: border-box;
}
```

---

### Padding
Padding creates space **inside** the border.

```css
.btn {
  padding: 12px 16px; /* top/bottom 12, left/right 16 */
}
```

Common patterns:
- `padding: 10px;` (all sides)
- `padding: 10px 20px;` (vertical, horizontal)
- `padding: 10px 20px 5px 20px;` (top, right, bottom, left)

---

### Border
Border sits around padding+content.

```css
.panel {
  border: 2px solid #999;
}
```

Border is shorthand for:
- `border-width`
- `border-style` (solid/dashed/etc)
- `border-color`

---

### Margin
Margin creates space **outside** the border.

```css
h2 {
  margin-bottom: 12px;
}
```

#### Margin collapsing (important beginner gotcha)
Vertical margins between block elements can “collapse”.

Example:
- `h1 { margin-bottom: 20px; }`
- `p { margin-top: 20px; }`

You might expect 40px space, but you often get **20px**, not 40px.

Tip: If spacing feels weird, try:
- add padding to a parent container, or
- use `display: flow-root;` on a container, or
- use flex/grid layouts (later lessons).

---

### Outline vs Border
- **border** affects layout size
- **outline** does not take up space (it draws on top)

```css
.debug {
  outline: 2px solid red;
}
```

Great for debugging spacing.

---

## Small Practice (do these in an HTML file)

### Practice 1: Make a card
Create HTML:

```html
<div class="card">
  <h2>Card title</h2>
  <p>This is a simple card component.</p>
</div>
```

Style it:

```css
.card {
  width: 320px;
  padding: 16px;
  border: 1px solid #ddd;
  border-radius: 12px;
  margin: 20px;
  font-family: system-ui, Arial, sans-serif;
}
```

### Practice 2: Compare box-sizing
- Make 2 boxes with same width/padding/border
- Give one `box-sizing: border-box;`
- Observe which one is visually larger

---

## Quick Checklist When CSS Doesn’t Work
- Is the CSS file linked correctly?
- Is the selector correct (class name spelled right)?
- Is another rule overriding it (specificity/order)?
- Is the browser cache showing old CSS (hard refresh)?
- Are you styling the correct element (inspect in DevTools)?

---

## Mini Glossary
- **selector**: chooses elements to style
- **property/value**: what you change and to what
- **box model**: content + padding + border + margin
- **specificity**: which rule wins when conflict happens
