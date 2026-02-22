# 02 - Selectors & Specificity

**Author:** Solomon Kassa  
**Level:** Beginner to Intermediate  
**Prerequisites:** Basic CSS knowledge  
**Time to Complete:** 3-4 hours

---

## 📚 Table of Contents
1. [What are Selectors?](#what-are-selectors)
2. [Types of Selectors](#types-of-selectors)
3. [Understanding Specificity](#understanding-specificity)
4. [Calculating Specificity](#calculating-specificity)
5. [Cascade and Inheritance](#cascade-and-inheritance)
6. [Key Takeaways](#key-takeaways)
7. [Exercises](#exercises)

---

## What are Selectors?

**CSS Selectors** are patterns used to select and style HTML elements. They're the first part of any CSS rule that targets which elements to style.

```css
selector {
  property: value;
}
```

### Selector Examples

```css
p { }              /* Selects all <p> elements */
#header { }        /* Selects element with id="header" */
.button { }        /* Selects elements with class="button" */
p.highlight { }    /* Selects <p> elements with class="highlight" */
```

---

## Types of Selectors

### 1. Element Selector

Selects all HTML elements of a specified type.

```css
p {
  color: blue;
}

h1 {
  font-size: 2em;
}

body {
  background-color: #f0f0f0;
}
```

**HTML:**
```html
<p>This is blue</p>
<p>This is also blue</p>
<h1>This is 2em</h1>
```

---

### 2. Class Selector

Selects elements with a specific `class` attribute. Uses a dot (`.`).

```css
.highlight {
  background-color: yellow;
}

.btn-primary {
  background-color: blue;
  color: white;
}
```

**HTML:**
```html
<p class="highlight">This has yellow background</p>
<button class="btn-primary">Click me</button>
```

---

### 3. ID Selector

Selects an element with a specific `id` attribute. Uses a hash (`#`). **IDs must be unique!**

```css
#main-header {
  font-size: 3em;
  color: navy;
}

#footer {
  background-color: gray;
}
```

**HTML:**
```html
<header id="main-header">Welcome</header>
<footer id="footer">Copyright 2026</footer>
```

---

### 4. Universal Selector

Selects all elements on the page. Uses an asterisk (`*`).

```css
* {
  margin: 0;
  padding: 0;
}
```

**Common Use:** Reset default browser styles

---

### 5. Attribute Selector

Selects elements based on their attributes.

```css
/* Elements with a type attribute */
input[type="text"] {
  border: 1px solid blue;
}

/* Links with href containing "example" */
a[href*="example"] {
  color: red;
}

/* Elements with disabled attribute */
button[disabled] {
  opacity: 0.5;
}

/* Links that target new window */
a[target="_blank"] {
  color: green;
}
```

**HTML:**
```html
<input type="text" placeholder="Text input">
<input type="checkbox">
<a href="https://example.com">Example link</a>
<button disabled>Disabled button</button>
```

---

### 6. Pseudo-Class Selector

Selects elements in a specific state.

```css
/* Unvisited link */
a:link {
  color: blue;
}

/* Visited link */
a:visited {
  color: purple;
}

/* Link on hover */
a:hover {
  text-decoration: underline;
}

/* Element on focus */
input:focus {
  outline: 2px solid blue;
}

/* First child */
li:first-child {
  font-weight: bold;
}

/* Last child */
li:last-child {
  border-bottom: none;
}

/* Odd/even children */
li:nth-child(odd) {
  background-color: #f0f0f0;
}

li:nth-child(even) {
  background-color: white;
}
```

---

### 7. Pseudo-Element Selector

Selects and styles parts of an element.

```css
/* First letter of paragraph */
p::first-letter {
  font-size: 2em;
  font-weight: bold;
}

/* First line of paragraph */
p::first-line {
  color: blue;
}

/* Content before an element */
::before {
  content: "→ ";
  color: red;
}

/* Content after an element */
::after {
  content: " ←";
  color: red;
}
```

**HTML & Result:**
```html
<p>Welcome to CSS</p>
<!-- Result: "W" is 2em and bold -->

<p>::before and ::after with content</p>
<!-- Result: "→ ::before..." with "..." ← in red -->
```

---

### 8. Combinator Selectors

Combine multiple selectors in meaningful ways.

#### Descendant Selector (space)

Selects nested elements at any depth.

```css
div p {
  color: blue;
}
```

**HTML:**
```html
<div>
  <p>This is blue</p>
  <section>
    <p>This is also blue (nested deep)</p>
  </section>
</div>
```

#### Child Selector (>)

Selects direct children only.

```css
div > p {
  color: blue;
}
```

**HTML:**
```html
<div>
  <p>This is blue (direct child)</p>
  <section>
    <p>This is NOT blue (not direct child)</p>
  </section>
</div>
```

#### Adjacent Sibling Selector (+)

Selects the next sibling element.

```css
h2 + p {
  font-weight: bold;
}
```

**HTML:**
```html
<h2>Heading</h2>
<p>This is bold (first p after h2)</p>
<p>This is not bold</p>
```

#### General Sibling Selector (~)

Selects all following sibling elements.

```css
h2 ~ p {
  color: gray;
}
```

**HTML:**
```html
<h2>Heading</h2>
<p>This is gray</p>
<p>This is also gray</p>
<p>And this too</p>
```

---

### 9. Group Selector (comma)

Apply same styles to multiple selectors.

```css
h1, h2, h3 {
  color: navy;
  font-family: Georgia;
}

/* Instead of writing: */
h1 { color: navy; font-family: Georgia; }
h2 { color: navy; font-family: Georgia; }
h3 { color: navy; font-family: Georgia; }
```

---

## Understanding Specificity

**Specificity** determines which CSS rule applies when multiple rules target the same element. Higher specificity wins.

### Specificity Hierarchy

```
┌─────────────────────────────────────┐
│ Importance (__Higher wins__)         │
├─────────────────────────────────────┤
│ !important (highest)                │
│ Inline styles (style="...")         │
│ IDs (#id)                           │
│ Classes (.class), Attributes, :hover│
│ Elements (p, div, etc.)             │
│ Universal (*) (lowest)              │
└─────────────────────────────────────┘
```

### Specificity Points

Calculate specificity as: **(a, b, c)**

- **a** = IDs
- **b** = Classes, attributes, pseudo-classes
- **c** = Elements, pseudo-elements

### Examples

```css
p                    /* (0, 0, 1) */
.highlight           /* (0, 1, 0) */
#header              /* (1, 0, 0) */
p.highlight          /* (0, 1, 1) */
div > p              /* (0, 0, 2) */
#header .nav a:hover /* (1, 2, 1) */
```

### Specificity Example

```css
/* (0, 0, 1) - Element selector */
p {
  color: blue;
}

/* (0, 1, 0) - Class selector - WINS! */
.highlight {
  color: yellow;
}

/* (1, 0, 0) - ID selector - WINS! */
#main-text {
  color: red;
}

/* (1, 0, 1) - ID + Element - WINS! */
#main-text p {
  color: green;
}
```

**HTML:**
```html
<p class="highlight">Yellow (class beats element)</p>
<p id="main-text">Green (ID beats class)</p>
```

---

## Calculating Specificity

### Complete Example

Let's compare these selectors:

```css
/* Specificity: (0, 0, 1) */
body p { }

/* Specificity: (0, 1, 1) - WINS */
body p.highlight { }

/* Specificity: (1, 0, 0) - ALWAYS WINS */
#main { }

/* Specificity: (0, 2, 0) - Higher class count */
.container .item { }
```

### Quick Calculation Guide

```
ID count × 100 + Class count × 10 + Element count × 1

Example: #header .nav a:hover
- 1 ID = 1 × 100 = 100
- 2 Classes (.nav, :hover) = 2 × 10 = 20
- 1 Element (a) = 1 × 1 = 1
- Total: 121
```

---

## Cascade and Inheritance

### Cascade (The "C" in CSS)

When multiple rules target the same element, **order matters**. Later rules override earlier ones (same specificity).

```css
p {
  color: blue;
}

p {
  color: red;  /* This wins because it comes last */
}
```

**Result:** All `<p>` elements are red.

### Inheritance

Some CSS properties are inherited from parent to child elements.

**Inherited Properties:** color, font-family, font-size, text-align, line-height

```css
body {
  color: blue;
  font-family: Arial;
}
```

**HTML:**
```html
<body>
  <p>This is blue Arial (inherited)</p>
  <div>
    <span>This is blue Arial (inherited)</span>
  </div>
</body>
```

### Non-Inherited Properties

**Not Inherited:** margin, padding, border, width, height, background

```css
body {
  background-color: yellow;
}
```

**HTML:**
```html
<body>
  <p>Background is yellow (applied to body only)</p>
  <div>Background is also yellow (applied to div)</div>
</body>
```

### Control Inheritance

```css
/* Force inheritance */
.container div {
  color: inherit;  /* Use parent's color */
}

/* Reset inheritance */
.container div {
  color: initial;  /* Use CSS default */
}

/* Revert to browser default */
.container div {
  color: revert;
}
```

---

## Key Takeaways

✅ **Selectors target HTML elements** for styling  
✅ **Element, class, ID** are most common selectors  
✅ **Specificity** determines which rule applies  
✅ **ID has highest specificity** (except !important)  
✅ **Cascade** means later rules override earlier ones  
✅ **Inheritance** passes some styles from parent to child  
✅ **Combinators** select elements by relationships  

---

## Exercises

### Exercise 1: Selector Practice

Write CSS for the following:
1. Style all `<p>` tags red
2. Style elements with class "highlight" yellow background
3. Style the element with id "main" blue
4. Style links that are hovered green

**Solution:**
```css
p {
  color: red;
}

.highlight {
  background-color: yellow;
}

#main {
  color: blue;
}

a:hover {
  color: green;
}
```

### Exercise 2: Specificity Challenge

Without running code, determine which color wins:

```css
p { color: blue; }
.text { color: red; }
#intro { color: green; }
```

```html
<p id="intro" class="text">What color am I?</p>
```

**Answer:** Green (ID has highest specificity: 1, 0, 0)

### Exercise 3: Build Selector Quiz

Create a checklist of which selector will be applied:
- [ ] Element selector
- [ ] Class selector  
- [ ] ID selector
- [ ] Attribute selector
- [ ] Pseudo-class
- [ ] Pseudo-element

---

## Next Steps

→ **Next Topic:** [03 - The Box Model](./03-box-model.md)

Learn about margin, padding, border, and content!

---

**Created by:** Solomon Kassa  
**Last Updated:** February 2026
