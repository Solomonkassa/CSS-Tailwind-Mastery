# 03 - The Box Model

**Author:** Solomon Kassa  
**Level:** Beginner  
**Prerequisites:** Basic CSS knowledge  
**Time to Complete:** 2-3 hours

---

## 📚 Table of Contents
1. [What is the Box Model?](#what-is-the-box-model)
2. [Components of the Box Model](#components-of-the-box-model)
3. [Margin](#margin)
4. [Padding](#padding)
5. [Border](#border)
6. [Content](#content)
7. [Box-Sizing](#box-sizing)
8. [Key Takeaways](#key-takeaways)
9. [Exercises](#exercises)

---

## What is the Box Model?

Every HTML element on the page is a **box**. The CSS Box Model describes how these boxes are structured and how they interact with other elements.

```
┌──────────────────────────────────┐
│         MARGIN (outside)         │
│  ┌────────────────────────────┐  │
│  │   BORDER (around content)  │  │
│  │  ┌──────────────────────┐  │  │
│  │  │ PADDING (inside)     │  │  │
│  │  │  ┌──────────────────┐ │  │  │
│  │  │  │   CONTENT        │ │  │  │
│  │  │  │  (text/images)   │ │  │  │
│  │  │  └──────────────────┘ │  │  │
│  │  └──────────────────────┘  │  │
│  └────────────────────────────┘  │
└──────────────────────────────────┘
```

---

## Components of the Box Model

### The Four Layers (Inside to Outside)

```
LAYER 1: CONTENT     ← Text, images, and child elements
LAYER 2: PADDING     ← Space inside the border
LAYER 3: BORDER      ← Line around the padding
LAYER 4: MARGIN      ← Space outside the border
```

---

## Margin

**Margin** creates space **outside** the border (external space).

### Basic Margin

```css
/* All sides */
div {
  margin: 20px;  /* 20px on all sides */
}

/* Vertical and Horizontal */
div {
  margin: 10px 20px;  /* 10px top/bottom, 20px left/right */
}

/* Individual sides */
div {
  margin-top: 10px;
  margin-right: 20px;
  margin-bottom: 10px;
  margin-left: 20px;
}

/* Shorthand: top right bottom left (clockwise) */
div {
  margin: 10px 20px 10px 20px;
}
```

### Margin Examples

```css
.box {
  width: 100px;
  height: 100px;
  background-color: blue;
  margin: 20px;  /* 20px space around the box */
}

.box2 {
  width: 100px;
  height: 100px;
  background-color: red;
  margin: 0 40px;  /* No top/bottom, 40px left/right */
}
```

**HTML:**
```html
<div class="box"></div>
<div class="box2"></div>
```

### Auto Margin

Center an element horizontally:

```css
.centered-box {
  width: 200px;
  margin: 0 auto;  /* 0 top/bottom, auto left/right = centered */
}
```

### Margin Collapse

**Important:** When vertical margins meet, they collapse to the larger value.

```css
.box1 {
  margin-bottom: 30px;
}

.box2 {
  margin-top: 20px;
}

/* Space between: 30px (not 50px!) */
```

---

## Padding

**Padding** creates space **inside** the border (internal space).

### Basic Padding

```css
/* All sides */
div {
  padding: 20px;
}

/* Vertical and Horizontal */
div {
  padding: 10px 20px;
}

/* Individual sides */
div {
  padding-top: 10px;
  padding-right: 20px;
  padding-bottom: 10px;
  padding-left: 20px;
}

/* Shorthand (clockwise): top right bottom left */
div {
  padding: 10px 20px 10px 20px;
}
```

### Padding Examples

```css
.button {
  background-color: blue;
  color: white;
  padding: 10px 20px;  /* Creates space around the text */
}

.card {
  background-color: white;
  border: 1px solid gray;
  padding: 30px;  /* Space inside the card */
}
```

### Padding vs Margin

```
PADDING → Inside (affects element's inside)
MARGIN  → Outside (affects element's outside)
```

**Visual Example:**
```
Padding Example:
┌─────────────┐
│   Padding   │
│ ┌─────────┐ │
│ │ Content │ │
│ └─────────┘ │
│   Padding   │
└─────────────┘

Margin Example:
    Margin
┌─────────────┐
│  Element    │
└─────────────┘
    Margin
```

---

## Border

**Border** creates a line around the padding.

### Basic Border

```css
/* Border on all sides */
div {
  border: 2px solid black;
}

/* Different sides */
div {
  border-top: 2px solid red;
  border-right: 3px dotted blue;
  border-bottom: 2px solid red;
  border-left: 3px dotted blue;
}
```

### Border Properties

```css
.box {
  border-width: 2px;      /* Thickness */
  border-style: solid;    /* Style: solid, dashed, dotted, double */
  border-color: black;    /* Color */
}

/* Or shorthand */
.box {
  border: 2px solid black;
}
```

### Border Styles

```css
border-style: solid;     /* ─────────── */
border-style: dashed;    /* ─ ─ ─ ─ ─ */
border-style: dotted;    /* · · · · · */
border-style: double;    /* ═══════════ */
border-style: groove;    /* 3D effect */
border-style: ridge;     /* 3D effect */
border-style: inset;     /* 3D effect */
border-style: outset;    /* 3D effect */
```

### Border Radius (Rounded Corners)

```css
.box {
  border: 2px solid black;
  border-radius: 10px;  /* All corners */
}

.box2 {
  border-radius: 5px 10px;      /* top-left/bottom-right, top-right/bottom-left */
  border-radius: 5px 10px 15px 20px;  /* Clockwise from top-left */
}

.circle {
  width: 100px;
  height: 100px;
  border-radius: 50%;  /* Perfect circle */
}
```

### Border Examples

```css
/* Rounded button */
.btn {
  border: 2px solid blue;
  border-radius: 5px;
  padding: 10px 20px;
}

/* Card with shadow effect */
.card {
  border: 1px solid #ddd;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

/* Separated borders */
.box {
  border: 2px solid;
  border-top-color: red;
  border-bottom-color: blue;
}
```

---

## Content

The **content** is where text and images are displayed. Its size is set by `width` and `height`.

```css
.box {
  width: 300px;
  height: 200px;
  /* Content area is 300x200 */
}
```

---

## Box-Sizing

**Important:** By default, `width` and `height` only apply to content (not including border and padding).

### Default: content-box

```css
.box {
  width: 100px;
  padding: 20px;
  border: 5px solid black;
  box-sizing: content-box;  /* Default */
}

/* Total width: 100 + 20 + 5 + 20 + 5 = 150px */
```

### Better: border-box

```css
.box {
  width: 100px;
  padding: 20px;
  border: 5px solid black;
  box-sizing: border-box;
}

/* Total width: 100px (padding and border included) */
```

### Global Best Practice

```css
/* Apply to all elements */
* {
  box-sizing: border-box;
}
```

**Why?** Easier to calculate sizes and more intuitive.

---

## Complete Box Model Example

```html
<style>
  body {
    margin: 0;
    padding: 20px;
    background-color: #f0f0f0;
  }

  .box {
    width: 200px;
    height: 100px;
    
    /* Box-sizing */
    box-sizing: border-box;
    
    /* Content */
    background-color: lightblue;
    
    /* Padding: inside */
    padding: 20px;
    
    /* Border: around padding */
    border: 3px solid navy;
    
    /* Margin: outside */
    margin: 30px;
  }
</style>

<div class="box">
  This is the content area
</div>
```

### Visual Output

```
┌─────────────────────────────────┐
│  Margin (30px all around)       │
│  ┌─────────────────────────────┐│
│  │ Border (3px solid navy)     ││
│  │ ┌─────────────────────────┐ ││
│  │ │ Padding (20px)          │ ││
│  │ │ ┌─────────────────────┐ │ ││
│  │ │ │ Content area        │ │ ││
│  │ │ │ (lightblue bg)      │ │ ││
│  │ │ └─────────────────────┘ │ ││
│  │ └─────────────────────────┘ ││
│  └─────────────────────────────┘│
└─────────────────────────────────┘
```

---

## Key Takeaways

✅ **Box Model** has 4 layers: content, padding, border, margin  
✅ **Margin** is external space (outside the border)  
✅ **Padding** is internal space (inside the border)  
✅ **Border** is a line around the element  
✅ **box-sizing: border-box** makes sizing easier  
✅ **Margin collapse** happens with vertical margins  
✅ Use shorthand: `margin: top right bottom left`  

---

## Exercises

### Exercise 1: Box Model Practice

Create a box with:
- 100px width and 100px height
- 10px padding
- 2px solid black border
- 20px margin

Calculate the total width (with default box-sizing).

**Solution:**
```css
.box {
  width: 100px;
  height: 100px;
  padding: 10px;
  border: 2px solid black;
  margin: 20px;
  box-sizing: content-box;
}

/* Total width: 100 + 10 + 2 + 10 + 2 = 124px */
```

### Exercise 2: Create a Card Component

Create a card with:
- White background
- Light gray border
- 20px padding inside
- 15px margin outside
- Rounded corners

**Solution:**
```css
.card {
  background-color: white;
  border: 1px solid #ddd;
  padding: 20px;
  margin: 15px;
  border-radius: 8px;
  box-sizing: border-box;
}
```

### Exercise 3: Center an Element

Center a 300px wide box horizontally on the page.

**Solution:**
```css
.centered {
  width: 300px;
  margin: 0 auto;  /* 0 top/bottom, auto left/right */
}
```

---

## Next Steps

→ **Next Topic:** [04 - Display & Positioning](./04-display-positioning.md)

Learn about display values and positioning elements!

---

**Created by:** Solomon Kassa  
**Last Updated:** February 2026
