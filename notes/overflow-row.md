# Case: the action falls outside a narrow screen

This is a synthetic minimal reproduction. It illustrates one flex layout failure; it does not imply that the same patch fits every page.

## Reproduce

1. Open a row containing text and a primary action at a viewport width of 360 CSS pixels.
2. Give the row a fixed width of 420px.
3. Confirm whether the primary action is clipped or requires horizontal scrolling.

```css
/* Before: the row can be wider than the available content area. */
.example-row { width: 420px; display: flex; }
```

## Bounded repair

```css
/* After: adapt the row to its parent and allow content to wrap. */
.example-row { width: 100%; min-width: 0; display: flex; flex-wrap: wrap; gap: 0.75rem; }
.example-row > * { min-width: 0; }
.example-row .action { flex-shrink: 0; }
```

Use the actual component names and layout rules in your own project. Avoid hiding overflow merely to make a test pass: clipped interactive content remains a defect. Long words, translated copy and media can require further changes.

## Verify the changed behavior

- At 360px and the normal desktop width, the action stays visible and usable.
- Long copy does not force the page beyond its viewport.
- Keyboard focus is visible and reaches the action.
- Relevant component tests and the project build still pass.

These notes were adapted from the existing Launch Patch synthetic sample. No claim of a new customer repair or fresh cross-browser execution is made.
