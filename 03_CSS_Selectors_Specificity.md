## CSS Selectors + Specificity (Beginner Friendly)

### What is a selector?
A **selector** is how CSS chooses which HTML element(s) to style.

```css
/* selector */  /* declaration block */
p { color: #333; }
```

---

### The most common selectors

#### 1) Element selector
Targets all tags of that type.

```css
h1 { font-size: 32px; }
p { line-height: 1.6; }
```

#### 2) Class selector (recommended for styling)
Targets elements with `class="..."`

```css
.button { background: black; color: white; }
```

```html
<a class="button">Buy</a>
<button class="button">Save</button>
```

#### 3) ID selector (use sparingly)
Targets a single element with `id="..."`

```css
#site-header { position: sticky; top: 0; }
```

```html
<header id="site-header">...</header>
```

---

### Combining selectors

#### Descendant selector (space)
Targets elements inside other elements.

```css
.card p { color: #555; }
```

This means: “All `p` inside `.card`”.

#### Child selector (`>`)
Targets only direct children.

```css
nav > a { text-decoration: none; }
```

#### Multiple selectors (comma)
Apply the same rules to different selectors.

```css
h1, h2, h3 { font-family: system-ui, Arial, sans-serif; }
```

---

### Attribute selectors (useful!)

```css
input[type="email"] { border: 1px solid #999; }
a[target="_blank"] { color: rebeccapurple; }
```

---

### Pseudo-classes (state)
Styles based on user interaction or state.

```css
a:hover { text-decoration: underline; }
button:disabled { opacity: 0.6; cursor: not-allowed; }
input:focus { outline: 2px solid dodgerblue; }
```

Common ones:
- `:hover`
- `:focus`
- `:active`
- `:visited`
- `:checked`
- `:disabled`

---

### Pseudo-elements (parts of an element)

```css
p::first-line { font-weight: 600; }
.tag::before { content: "#"; }
```

Common ones:
- `::before`
- `::after`
- `::first-line`

---

## Specificity (why one rule wins)
When multiple rules target the same element/property, CSS decides which one “wins”.

### General rule (from weaker to stronger)
- **element** selectors (e.g. `p`)
- **class / attributes / pseudo-classes** (e.g. `.note`, `[type="text"]`, `:hover`)
- **id** selectors (e.g. `#main`)
- **inline style** (e.g. `style="..."`)

If specificity is equal, **the later rule wins**.

---

### Examples

```css
p { color: blue; }            /* weak */
.note { color: green; }       /* stronger */
#main { color: purple; }      /* strongest among these */
```

If an element is:

```html
<p id="main" class="note">Hello</p>
```

Then `#main` wins and the text becomes purple.

---

### Avoid `!important` unless you must
`!important` forces a rule to win and can make CSS hard to maintain.

```css
.warning { color: red !important; }
```

Better approach:
- use clearer class names
- reduce overly-specific selectors
- order your CSS intentionally

---

## Practice
1) Make 3 rules (element, class, id) that set `color`. Apply all three to one `<p>`. Which wins?
2) Create `.card p` and `p` rules. Put a `<p>` inside and outside `.card`. Confirm only the inside one changes.
