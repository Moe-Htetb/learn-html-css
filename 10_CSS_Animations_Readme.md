## CSS Animations (Beginner Friendly)

CSS can create movement in two main ways:

1. **Transition**: smooth change from one style to another (usually on `:hover` / `:focus`)
2. **Animation**: a repeating/stepped motion timeline using `@keyframes` (plays automatically or can be triggered)

---

## 1) Transitions (Hover effects, “smooth switching”)

### Syntax
```css
selector {
  transition: property duration timing-function delay;
}
```

Most common:
```css
.box {
  transition: transform 200ms ease, background-color 200ms ease;
}
.box:hover {
  transform: translateY(-4px);
  background-color: #eef2ff;
}
```

### Key transition properties
- `property`: what changes (`transform`, `opacity`, `background-color`)
- `duration`: how long (e.g. `150ms`, `0.3s`)
- `timing-function`: speed pattern (`ease`, `ease-in-out`)
- `delay`: wait before starting (e.g. `100ms`)

---

## 2) Animations (Keyframes timeline)

### Syntax
```css
@keyframes bounce {
  0% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
  100% { transform: translateY(0); }
}

selector {
  animation-name: bounce;
  animation-duration: 1s;
  animation-iteration-count: infinite;
}
```

### Full “animation” shorthand
```css
selector {
  animation: bounce 1s ease-in-out infinite;
}
```

### Common animation settings
- `animation-duration`: total time of one cycle
- `animation-timing-function`: how movement speeds up/slows down
- `animation-iteration-count`: `1`, `infinite`, etc.
- `animation-direction`: `normal`, `alternate` (back and forth)
- `animation-fill-mode`:
  - `forwards`: stay on the last keyframe
  - `backwards`: apply styles from the first keyframe before starting

---

## 3) Accessibility: reduced motion
Some people prefer less animation. Respect that:

```css
@media (prefers-reduced-motion: reduce) {
  .animated {
    animation: none !important;
    transition: none !important;
  }
}
```

---

## 4) Beginner mistakes
- Animating **layout properties** like `width`/`height` can be slow. Prefer:
  - `transform` (move/scale/rotate)
  - `opacity` (fade)
- Forgetting the `@keyframes` name or spelling it wrong
- Not including units where needed (`translateY(10px)`, not `10`)
- Animation plays immediately (unless you add a delay)

---

## Practice (small tasks)
1) Add a `fade-in` animation to a card when the page loads (`opacity + transform`).
2) Make a button “wiggle” on hover using transitions (`transform`) OR keyframes.
3) Add `prefers-reduced-motion: reduce` to turn animations off.

