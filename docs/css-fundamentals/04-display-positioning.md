# 04 - Display & Positioning

**Author:** Solomon Kassa  
**Level:** Intermediate  
**Prerequisites:** Box Model knowledge  
**Time to Complete:** 3-4 hours

---

## 📚 Table of Contents
1. [Display Property](#display-property)
2. [Position Property](#position-property)
3. [Stacking Context](#stacking-context)
4. [Practical Examples](#practical-examples)
5. [Key Takeaways](#key-takeaways)
6. [Exercises](#exercises)

---

## Display Property

The `display` property controls how an element is rendered on the page.

### display: block

Takes up full width available, starts on a new line.

```css
.block-element {
  display: block;
}
```

**Default Elements:** `<div>`, `<p>`, `<h1-h6>`, `<section>`, `<header>`, `<footer>`

```html
<style>
  .block { display: block; width: 100px; background: blue; }
</style>

<span class="block">Block 1</span>
<span class="block">Block 2</span>
<!-- Spans appear on separate lines -->
```

---

### display: inline

Only takes up space needed, flows with text, doesn't respect width/height.

```css
.inline-element {
  display: inline;
}
```

**Default Elements:** `<span>`, `<a>`, `<strong>`, `<em>`

```html
<style>
  .inline { display: inline; width: 100px; }  /* Width ignored */
</style>

<div class="inline">Inline 1</div>
<div class="inline">Inline 2</div>
<!-- Divs appear on same line -->
```

---

### display: inline-block

Hybrid of block and inline. Flows like inline but respects width/height.

```css
.inline-block-element {
  display: inline-block;
  width: 150px;
  height: 150px;
}
```

**Best for:** Navigation buttons, image galleries

```html
<style>
  .box { display: inline-block; width: 100px; height: 100px; background: blue; margin: 5px; }
</style>

<div class="box"></div>
<div class="box"></div>
<div class="box"></div>
<!-- Boxes appear in a row -->
```

---

### display: flex (Flexbox)

Flexible box layout. Controls alignment and distribution of child elements.

```css
.flex-container {
  display: flex;
  justify-content: center;  /* Horizontal centering */
  align-items: center;      /* Vertical centering */
  gap: 10px;                /* Space between items */
}
```

**Learn more:** See Section 06 - Flexbox Mastery

---

### display: grid

Two-dimensional grid layout for complex arrangements.

```css
.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;  /* 3 equal columns */
  gap: 20px;
}
```

**Learn more:** See Section 07 - CSS Grid

---

### display: none

Hides element (removed from document flow).

```css
.hidden {
  display: none;
}
```

---

## Position Property

Controls how an element is positioned in the page layout.

### position: static (Default)

Element follows normal document flow.

```css
.box {
  position: static;  /* Default, top/left/right/bottom ignored */
}
```

---

### position: relative

Element positioned relative to its **normal position**. Other elements don't fill the gap.

```css
.box {
  position: relative;
  top: 10px;        /* Move 10px down from normal position */
  left: 20px;       /* Move 20px right from normal position */
}
```

**Use Case:** Slight adjustments, creating stacking context

```html
<style>
  .normal { position: static; }
  .shifted { position: relative; top: 20px; left: 20px; }
</style>

<div class="normal">Normal</div>
<div class="shifted">Shifted right and down</div>
```

---

### position: absolute

Element positioned relative to **nearest positioned ancestor**. Removed from document flow.

```css
.container {
  position: relative;  /* Establish positioning context */
}

.box {
  position: absolute;
  top: 10px;
  left: 20px;
}
```

**Common Pattern:**
```html
<style>
  .container { position: relative; width: 300px; height: 300px; border: 1px solid black; }
  .box { position: absolute; top: 50px; right: 20px; width: 50px; height: 50px; background: blue; }
</style>

<div class="container">
  <div class="box">Positioned absolutely inside container</div>
</div>
```

---

### position: fixed

Element positioned relative to **viewport** (stays in place when scrolling).

```css
.header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  height: 60px;
  background: navy;
  z-index: 1000;
}
```

**Use Case:** Navigation bars, sticky headers, modal overlays

```html
<style>
  .sticky-header { position: fixed; top: 0; width: 100%; background: blue; }
</style>

<div class="sticky-header">Stays in place when scrolling</div>
```

---

### position: sticky

Element behaves as relative until scrolled to viewport edge, then fixed.

```css
.sidebar {
  position: sticky;
  top: 20px;  /* Stick when 20px from top */
}
```

**Use Case:** Table headers, sidebar navigation

```html
<style>
  .sticky { position: sticky; top: 0; background: white; font-weight: bold; }
</style>

<table>
  <thead>
    <tr class="sticky">
      <th>Header stays visible when scrolling</th>
    </tr>
  </thead>
</table>
```

---

## Stacking Context

Determines which element appears on top when they overlap.

### z-index

Controls stacking order. Higher values appear on top.

```css
.background {
  position: relative;
  z-index: 1;
}

.foreground {
  position: relative;
  z-index: 2;  /* Appears on top */
}

.overlay {
  position: fixed;
  z-index: 1000;  /* Appears on top of everything */
}
```

**Important:** z-index only works with positioned elements (position ≠ static)

---

## Practical Examples

### Sticky Navigation Bar

```html
<style>
  nav {
    position: fixed;
    top: 0;
    width: 100%;
    background-color: navy;
    color: white;
    padding: 15px;
    z-index: 100;
  }

  body {
    margin-top: 50px;  /* Account for fixed nav */
  }
</style>

<nav>
  <a href="#">Home</a>
  <a href="#">About</a>
  <a href="#">Contact</a>
</nav>

<main>
  <p>Content goes here...</p>
</main>
```

### Centered Modal Dialog

```html
<style>
  .overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
  }

  .modal {
    background: white;
    padding: 30px;
    border-radius: 8px;
    width: 90%;
    max-width: 500px;
  }
</style>

<div class="overlay">
  <div class="modal">
    <h2>Modal Title</h2>
    <p>Modal content goes here</p>
  </div>
</div>
```

### Image with Absolute Caption

```html
<style>
  .image-container {
    position: relative;
    width: 300px;
    height: 200px;
    overflow: hidden;
  }

  .image-container img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .caption {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    background: rgba(0,0,0,0.7);
    color: white;
    padding: 10px;
  }
</style>

<div class="image-container">
  <img src="image.jpg" alt="Image">
  <div class="caption">Image Caption</div>
</div>
```

---

## Key Takeaways

✅ **Display property** controls layout type (block, inline, flex, grid)  
✅ **Position property** controls element positioning (static, relative, absolute, fixed, sticky)  
✅ **Relative** positions relative to normal location  
✅ **Absolute** removes from flow, positions relative to parent  
✅ **Fixed** stays in place, not affected by scrolling  
✅ **Sticky** switches between relative and fixed  
✅ **z-index** controls stacking order  

---

## Exercises

### Exercise 1: Position Practice

Create an element that stays at the top of the screen when scrolling.

**Solution:**
```css
.sticky-nav {
  position: fixed;
  top: 0;
  width: 100%;
  background-color: navy;
  z-index: 100;
}
```

### Exercise 2: Centered Modal

Create a modal dialog centered on screen with a semi-transparent overlay.

**Solution:**
```css
.modal-overlay {
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal {
  background: white;
  padding: 30px;
  border-radius: 8px;
}
```

### Exercise 3: Layout Comparison

Create a page showing the difference between:
- display: block
- display: inline
- display: inline-block
- display: flex

---

## Next Steps

→ **Next Topic:** [05 - Typography & Text Properties](./05-typography.md)

Learn about fonts, text styling, and typography!

---

**Created by:** Solomon Kassa  
**Last Updated:** February 2026
