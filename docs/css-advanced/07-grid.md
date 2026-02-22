# 07 - CSS Grid

**Author:** Solomon Kassa  
**Level:** Intermediate to Advanced  
**Prerequisites:** Flexbox knowledge  
**Time to Complete:** 4-5 hours

---

## 📚 Table of Contents
1. [What is CSS Grid?](#what-is-css-grid)
2. [Grid Container Properties](#grid-container-properties)
3. [Grid Item Properties](#grid-item-properties)
4. [Grid Areas & Layout](#grid-areas--layout)
5. [Responsive Grids](#responsive-grids)
6. [Real-World Patterns](#real-world-patterns)
7. [Key Takeaways](#key-takeaways)
8. [Exercises](#exercises)

---

## What is CSS Grid?

**CSS Grid** is a two-dimensional layout system for creating complex layouts with rows and columns.

```
┌─────────┬─────────┬─────────┐
│ Cell    │ Cell    │ Cell    │
├─────────┼─────────┼─────────┤
│ Cell    │ Cell    │ Cell    │
├─────────┼─────────┼─────────┤
│ Cell    │ Cell    │ Cell    │
└─────────┴─────────┴─────────┘
```

### Grid vs Flexbox

| Aspect | Grid | Flexbox |
|--------|------|---------|
| **Dimensions** | 2D (rows + columns) | 1D (rows OR columns) |
| **Use Case** | Page layouts | Component layouts |
| **Complexity** | Complex layouts | Simple alignment |
| **Learning** | Steeper curve | Easier to learn |

---

## Grid Container Properties

### display: grid

Creates a grid container.

```css
.container {
  display: grid;
}
```

---

### grid-template-columns

Defines column sizes.

```css
/* 3 equal columns */
.grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}

/* Mixed sizes */
.grid {
  grid-template-columns: 200px 1fr 150px;
}

/* Repeat function */
.grid {
  grid-template-columns: repeat(3, 1fr);  /* Same as above */
}

/* Auto-fit responsive */
.grid {
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
}
```

**Unit Guide:**
- `px` - Fixed pixels
- `fr` - Fraction of available space
- `auto` - Automatic sizing
- `%` - Percentage

---

### grid-template-rows

Defines row sizes.

```css
.grid {
  display: grid;
  grid-template-rows: 100px 1fr 50px;
}

/* Auto rows with minimum */
.grid {
  grid-auto-rows: minmax(100px, auto);
}
```

---

### gap

Adds space between grid items (same as flexbox).

```css
.grid {
  display: grid;
  gap: 20px;        /* Space between all items */
  row-gap: 10px;    /* Space between rows */
  column-gap: 20px; /* Space between columns */
}
```

---

### justify-items & align-items

Aligns items horizontally and vertically.

```css
.grid {
  display: grid;
  justify-items: center;  /* Center items horizontally */
  align-items: center;    /* Center items vertically */
}
```

---

### justify-content & align-content

Aligns entire grid within container.

```css
.grid {
  display: grid;
  width: 100%;
  height: 100vh;
  justify-content: center;  /* Center grid horizontally */
  align-content: center;    /* Center grid vertically */
}
```

---

## Grid Item Properties

### grid-column

Specifies which column(s) an item spans.

```css
.item1 {
  grid-column: 1 / 3;  /* Starts at column 1, ends at column 3 (spans 2) */
}

.item2 {
  grid-column: span 2;  /* Spans 2 columns */
}

.item3 {
  grid-column: 1 / -1;  /* Spans from first to last column */
}
```

---

### grid-row

Specifies which row(s) an item spans.

```css
.item1 {
  grid-row: 1 / 3;   /* Spans 2 rows */
}

.item2 {
  grid-row: span 2;  /* Spans 2 rows */
}
```

---

### grid-area

Combines grid-column and grid-row.

```css
.item {
  grid-area: 1 / 1 / 3 / 3;  /* row-start / col-start / row-end / col-end */
}

/* Or with grid-template-areas (see below) */
.header {
  grid-area: header;
}
```

---

## Grid Areas & Layout

### grid-template-areas

Create named grid regions.

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 60px 1fr 60px;
  grid-template-areas:
    "header header header"
    "sidebar main main"
    "footer footer footer";
  height: 100vh;
}

.header {
  grid-area: header;
  background-color: navy;
}

.sidebar {
  grid-area: sidebar;
  background-color: #f0f0f0;
}

.main {
  grid-area: main;
  background-color: white;
}

.footer {
  grid-area: footer;
  background-color: navy;
}
```

**HTML:**
```html
<div class="container">
  <div class="header">Header</div>
  <div class="sidebar">Sidebar</div>
  <div class="main">Main Content</div>
  <div class="footer">Footer</div>
</div>
```

---

## Responsive Grids

### Auto-Fit & Auto-Fill

```css
/* Responsive columns that wrap */
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}

/* Difference: auto-fill fills with empty tracks, auto-fit collapses them */
```

### Media Queries with Grid

```css
.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

@media (max-width: 768px) {
  .grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 480px) {
  .grid {
    grid-template-columns: 1fr;
  }
}
```

---

## Real-World Patterns

### Responsive Dashboard

```css
.dashboard {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
  padding: 20px;
}

.card {
  background: white;
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}
```

### Full-Page Layout

```css
.page {
  display: grid;
  grid-template-columns: 250px 1fr;
  grid-template-rows: 60px 1fr 60px;
  height: 100vh;
  grid-template-areas:
    "header header"
    "sidebar main"
    "footer footer";
}

.header { grid-area: header; }
.sidebar { grid-area: sidebar; }
.main { grid-area: main; }
.footer { grid-area: footer; }
```

### Product Grid

```css
.products {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 15px;
  padding: 20px;
}

.product {
  background: white;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.product img {
  width: 100%;
  height: 200px;
  object-fit: cover;
}

.product-info {
  padding: 15px;
}
```

---

## Key Takeaways

✅ **Grid** is 2D (rows AND columns)  
✅ **grid-template-columns** defines column sizes  
✅ **grid-template-rows** defines row sizes  
✅ **fr unit** represents fractions of space  
✅ **gap** adds space between items  
✅ **grid-template-areas** creates named regions  
✅ **auto-fit/auto-fill** create responsive grids  

---

## Exercises

### Exercise 1: Simple Grid

Create a 3-column grid with 4 items.

**Solution:**
```css
.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
```

### Exercise 2: Full Page Layout

Create a layout with header, sidebar, main content, and footer.

**Solution:**
```css
.page {
  display: grid;
  grid-template-columns: 250px 1fr;
  grid-template-rows: 60px 1fr 60px;
  height: 100vh;
  grid-template-areas:
    "header header"
    "sidebar main"
    "footer footer";
}
```

### Exercise 3: Responsive Grid

Create a grid that displays 3 columns on desktop, 2 on tablet, 1 on mobile.

**Solution:**
```css
.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

@media (max-width: 768px) {
  .grid { grid-template-columns: repeat(2, 1fr); }
}

@media (max-width: 480px) {
  .grid { grid-template-columns: 1fr; }
}
```

---

## Next Steps

→ **Next Topic:** [08 - Transforms & Transitions](./08-transforms-transitions.md)

Learn how to transform and animate elements!

---

**Created by:** Solomon Kassa  
**Last Updated:** February 2026
