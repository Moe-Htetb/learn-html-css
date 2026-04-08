## Flex + Grid Demo README

This guide explains the files:
- `html/flex_grid.html`
- `css/flex_grid.css`

They are a practice project that shows common **Flexbox** and **CSS Grid** components in one page.

---

## How to Run

Open this file in browser:

```bash
open /Users/moehtetoo/Desktop/notes/html/flex_grid.html
```

The HTML file links to CSS with:

```html
<link rel="stylesheet" href="../css/flex_grid.css" />
```

So keep this folder structure:
- `html/` for HTML
- `css/` for CSS

---

## What You Will Learn

### Flexbox patterns
1. **Navbar flex row**
   - logo left, nav links center/right, button right
   - properties: `display: flex`, `justify-content: space-between`, `gap`

2. **Hero center section**
   - center content vertically and horizontally
   - properties: `display: flex`, `align-items`, `justify-content`

3. **Toolbar/action row**
   - text on left, action buttons on right
   - useful for admin/dashboard UI

4. **Wrapping card row**
   - cards wrap automatically when screen becomes narrow
   - properties: `flex-wrap`, `flex: 1 1 ...`

5. **Media object**
   - avatar/icon + text block beside it
   - common in chat/comments/notifications

6. **Form stack**
   - vertical form fields using `flex-direction: column` and `gap`

---

### Grid patterns
1. **Responsive card grid**
   - properties: `grid-template-columns: repeat(auto-fit, minmax(...))`
   - automatically changes number of columns by screen size

2. **App shell layout**
   - fixed sidebar + fluid content area
   - properties: `grid-template-columns: 220px 1fr`

3. **Bento layout**
   - named areas for custom shape layout
   - property: `grid-template-areas`

4. **Grid + Flex combined**
   - outer layout uses grid
   - each card uses flex column
   - footer is pushed to bottom with `margin-top: auto`

---

## File Structure Overview

### `html/flex_grid.html`
- contains all demo sections
- each section has a title + short description
- semantic elements used: `header`, `main`, `section`, `article`, `footer`

### `css/flex_grid.css`
- global variables (`:root`) for easy theme editing
- reusable button styles (`.btn`, `.btn-sm`, `.btn.ghost`)
- component styles grouped by topic:
  - flex components
  - grid components
  - combined patterns
- responsive media query at the bottom

---

## Quick Edit Guide

### Change color theme
Edit variables in `:root`:
- `--primary`
- `--bg`
- `--surface`
- `--text`

### Make cards bigger
Edit padding/radius:
- `.mini-card`
- `.grid-card`
- `.combo-card`

### Change responsive behavior
Edit breakpoint section:
- `@media (max-width: 720px)`

---

## Suggested Practice Tasks

1. Add a new **Flex** section: vertical timeline using `display: flex`.
2. Add a new **Grid** section: photo gallery with `auto-fit`.
3. Add hover animation to cards using:
   - `transition: transform 180ms ease;`
   - `transform: translateY(-4px);`
4. Add dark mode variables with:
   - `@media (prefers-color-scheme: dark) { ... }`

---

## Common Mistakes (and fixes)

1. **CSS not loading**
   - check relative path `../css/flex_grid.css`

2. **Flex items not aligning**
   - parent needs `display: flex`
   - use `align-items` and `justify-content` on parent, not child

3. **Grid not creating columns**
   - parent needs `display: grid`
   - define `grid-template-columns`

4. **Layout breaks on mobile**
   - add/update media query rules
   - avoid fixed widths when possible

---

## One-line Summary

This project is a practical reference of real UI components built with Flexbox and Grid, designed for beginner-to-intermediate CSS learning.
