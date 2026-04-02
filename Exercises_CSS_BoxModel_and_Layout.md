## Exercises: CSS Box Model + Layout

### How to use these exercises
- Create a simple `index.html` and `styles.css`.
- Copy the HTML snippet, then write the CSS yourself.
- Use your browser DevTools (Inspect) to see padding, border, margin.

---

## Exercise 1: Two cards with spacing

### HTML
```html
<div class="wrapper">
  <div class="card">
    <h2>Card A</h2>
    <p>Make this card look clean.</p>
  </div>

  <div class="card">
    <h2>Card B</h2>
    <p>Same style as Card A.</p>
  </div>
</div>
```

### Requirements
- `wrapper` should center content and not touch the screen edges
- each `.card` should have:
  - padding
  - border
  - rounded corners
  - margin or gap between cards

---

## Exercise 2: box-sizing comparison

### HTML
```html
<div class="demo">
  <div class="box box-a">A</div>
  <div class="box box-b">B</div>
</div>
```

### Requirements
- both boxes:
  - `width: 200px;`
  - `padding: 20px;`
  - `border: 5px solid black;`
- only one uses `box-sizing: border-box;`
- make both boxes sit in a row (hint: flexbox)

Question: which one becomes visually larger and why?

---

## Exercise 3: Simple navbar (flex)

### HTML
```html
<header class="navbar">
  <div class="brand">MySite</div>
  <nav class="links">
    <a href="#">Home</a>
    <a href="#">Docs</a>
    <a href="#">Contact</a>
  </nav>
  <button class="cta">Sign up</button>
</header>
```

### Requirements
- brand on left, links in middle, button on right
- add spacing between links
- add padding to navbar and a bottom border

---

## Exercise 4: Grid of cards

### HTML
```html
<section class="products">
  <div class="product">Product 1</div>
  <div class="product">Product 2</div>
  <div class="product">Product 3</div>
  <div class="product">Product 4</div>
  <div class="product">Product 5</div>
  <div class="product">Product 6</div>
</section>
```

### Requirements
- use CSS grid
- 3 columns on wide screens
- nice gap between items
- each product has padding + border + border-radius

Bonus: try `grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));`
