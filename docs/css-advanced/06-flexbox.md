# 06 - Flexbox Mastery

**Author:** Solomon Kassa  
**Level:** Intermediate  
**Prerequisites:** Box model, display property  
**Time to Complete:** 4-5 hours

---

## 📚 Table of Contents
1. [What is Flexbox?](#what-is-flexbox)
2. [Flex Container Properties](#flex-container-properties)
3. [Flex Item Properties](#flex-item-properties)
4. [Real-World Patterns](#real-world-patterns)
5. [Key Takeaways](#key-takeaways)
6. [Exercises](#exercises)

---

## What is Flexbox?

**Flexbox** is a one-dimensional layout system for arranging items in rows or columns with flexible sizing and alignment.

```
┌──────────────────────────────────────┐
│  Flex Container                      │
│  ┌─────┐ ┌─────┐ ┌─────┐           │
│  │Item │ │Item │ │Item │           │
│  │  1  │ │  2  │ │  3  │           │
│  └─────┘ └─────┘ └─────┘           │
└──────────────────────────────────────┘
```

### When to Use Flexbox

- Navigation bars
- Card layouts
- Centering content
- Space distribution
- One-dimensional layouts

---

## Flex Container Properties

The parent element with `display: flex` controls the layout.

### display: flex

Creates a flex container.

```css
.container {
  display: flex;
}
```

---

### flex-direction

Controls direction of flex items (row or column).

```css
.row {
  display: flex;
  flex-direction: row;         /* Default: left to right */
}

.column {
  display: flex;
  flex-direction: column;      /* Top to bottom */
}

.row-reverse {
  display: flex;
  flex-direction: row-reverse;  /* Right to left */
}

.column-reverse {
  display: flex;
  flex-direction: column-reverse; /* Bottom to top */
}
```

**Visualization:**
```
flex-direction: row
┌─┬─┬─┐

flex-direction: column
┌─┐
├─┤
├─┤
└─┘

flex-direction: row-reverse
┌─┬─┬─┐ (reversed order)

flex-direction: column-reverse
┌─┐
├─┤
├─┤
└─┘ (reversed order)
```

---

### justify-content

Aligns items along the main axis (horizontally in row direction).

```css
.center {
  display: flex;
  justify-content: center;     /* Center items */
}

.space-between {
  display: flex;
  justify-content: space-between;  /* First and last at edges, space between */
}

.space-around {
  display: flex;
  justify-content: space-around;   /* Equal space around each item */
}

.space-evenly {
  display: flex;
  justify-content: space-evenly;   /* Equal space between and around items */
}

.flex-start {
  display: flex;
  justify-content: flex-start;  /* Default: align to start */
}

.flex-end {
  display: flex;
  justify-content: flex-end;    /* Align to end */
}
```

**Visual Guide:**
```
justify-content: flex-start
[A] [B] [C]

justify-content: center
   [A] [B] [C]

justify-content: space-between
[A]     [B]     [C]

justify-content: space-around
  [A]  [B]  [C]

justify-content: space-evenly
   [A]   [B]   [C]
```

---

### align-items

Aligns items along the cross axis (vertically in row direction).

```css
.center {
  display: flex;
  align-items: center;        /* Center vertically */
  height: 200px;              /* Need height to see effect */
}

.flex-start {
  display: flex;
  align-items: flex-start;    /* Align to top */
}

.flex-end {
  display: flex;
  align-items: flex-end;      /* Align to bottom */
}

.stretch {
  display: flex;
  align-items: stretch;       /* Default: items fill height */
}

.baseline {
  display: flex;
  align-items: baseline;      /* Align baselines of text */
}
```

---

### gap

Adds space between flex items.

```css
.container {
  display: flex;
  gap: 20px;           /* Space between all items */
}

.container2 {
  display: flex;
  gap: 10px 20px;      /* row-gap col-gap */
  row-gap: 10px;       /* Space between rows */
  column-gap: 20px;    /* Space between columns */
}
```

---

### flex-wrap

Controls whether items wrap to next line.

```css
.nowrap {
  display: flex;
  flex-wrap: nowrap;   /* Default: single line, items shrink */
}

.wrap {
  display: flex;
  flex-wrap: wrap;     /* Items wrap to next line */
}

.wrap-reverse {
  display: flex;
  flex-wrap: wrap-reverse;  /* Wrap bottom to top */
}
```

---

### align-content

Aligns lines (when wrapping) along cross axis.

```css
.container {
  display: flex;
  flex-wrap: wrap;
  height: 400px;
  align-content: center;   /* Center all lines */
}
```

---

## Flex Item Properties

Properties applied to flex children.

### flex-grow

How much item grows to fill available space.

```css
.item {
  flex-grow: 0;  /* Default: doesn't grow */
}

.item.grow {
  flex-grow: 1;  /* Grows to fill space */
}

.item.grow-2 {
  flex-grow: 2;  /* Grows twice as much */
}
```

**Example:**
```css
.container {
  display: flex;
  width: 600px;
}

.item1 { flex-grow: 1; }  /* 200px */
.item2 { flex-grow: 2; }  /* 400px */
/* Total: 1 + 2 = 3 parts, divides space proportionally */
```

---

### flex-shrink

How much item shrinks when space is limited.

```css
.item {
  flex-shrink: 1;   /* Default: shrinks equally */
}

.item.no-shrink {
  flex-shrink: 0;   /* Doesn't shrink */
}

.item.shrink-2 {
  flex-shrink: 2;   /* Shrinks twice as much */
}
```

---

### flex-basis

Base size before flex-grow/shrink is applied.

```css
.item {
  flex-basis: 200px;  /* Base size is 200px */
}
```

---

### flex Shorthand

Combines grow, shrink, and basis.

```css
/* Longhand */
.item {
  flex-grow: 1;
  flex-shrink: 1;
  flex-basis: 200px;
}

/* Shorthand */
.item {
  flex: 1 1 200px;
}

/* Common patterns */
.item { flex: 1; }              /* Grow equally, shrink, auto size */
.item { flex: 0 0 200px; }      /* Fixed 200px, no grow/shrink */
.item { flex: 1 0 0; }          /* Grow equally, no shrink, 0 base */
```

---

### align-self

Override align-items for individual item.

```css
.container {
  display: flex;
  align-items: center;
}

.item.top {
  align-self: flex-start;   /* Override: align to top */
}

.item.bottom {
  align-self: flex-end;     /* Override: align to bottom */
}
```

---

## Real-World Patterns

### Centered Container

```css
.flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
```

### Navigation Bar

```css
nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 20px;
  background-color: navy;
}

nav a {
  color: white;
  margin: 0 15px;
}

nav .logo {
  flex-grow: 1;  /* Push other items to right */
}
```

### Card Layout

```css
.cards-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: center;
}

.card {
  flex: 1 1 300px;  /* Grow, shrink, 300px base */
  max-width: 300px;
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  padding: 20px;
}
```

### Sidebar Layout

```css
.layout {
  display: flex;
  min-height: 100vh;
}

.sidebar {
  flex: 0 0 250px;  /* Fixed 250px width */
  background-color: #f0f0f0;
  padding: 20px;
}

.main {
  flex: 1;  /* Takes remaining space */
  padding: 20px;
}
```

### Space-Between Layout

```css
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px;
}

.logo {
  flex: 0 0 auto;  /* Fixed size */
}

.nav {
  flex: 1;  /* Takes space in middle */
  display: flex;
  justify-content: center;
  gap: 20px;
}

.user-menu {
  flex: 0 0 auto;  /* Fixed size */
}
```

---

## Key Takeaways

✅ **Flexbox** is a 1D layout system (row or column)  
✅ **justify-content** aligns along main axis  
✅ **align-items** aligns along cross axis  
✅ **flex-direction** sets direction (row/column)  
✅ **gap** adds space between items  
✅ **flex: 1** makes item grow equally  
✅ **flex-wrap** allows items to wrap  

---

## Exercises

### Exercise 1: Centered Button

Create a button centered on screen using flexbox.

**Solution:**
```css
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

button {
  padding: 10px 20px;
  font-size: 16px;
}
```

### Exercise 2: Navigation Bar

Create a responsive nav bar with:
- Logo on left
- Menu items in center
- Sign-in button on right

**Solution:**
```css
nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 20px;
  background-color: navy;
}

.menu { display: flex; gap: 20px; }
```

### Exercise 3: Card Grid

Create a responsive grid of cards that wrap on smaller screens.

**Solution:**
```css
.cards {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: center;
}

.card {
  flex: 1 1 250px;
  max-width: 300px;
}
```

---

## Next Steps

→ **Next Topic:** [07 - CSS Grid](./07-grid.md)

Learn the 2D layout power of CSS Grid!

---

**Created by:** Solomon Kassa  
**Last Updated:** February 2026
