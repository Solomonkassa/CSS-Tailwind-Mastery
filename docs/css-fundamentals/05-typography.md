# 05 - Typography & Text Properties

**Author:** Solomon Kassa  
**Level:** Beginner  
**Prerequisites:** CSS fundamentals  
**Time to Complete:** 2-3 hours

---

## 📚 Table of Contents
1. [Font Properties](#font-properties)
2. [Text Properties](#text-properties)
3. [Font Families](#font-families)
4. [Web Fonts](#web-fonts)
5. [Text Effects](#text-effects)
6. [Key Takeaways](#key-takeaways)
7. [Exercises](#exercises)

---

## Font Properties

### font-family

Specifies the typeface. Provide fallbacks in order of preference.

```css
body {
  font-family: Arial, Helvetica, sans-serif;
}
```

**Structure:**
```
font-family: "Primary Font", "Fallback 1", "Fallback 2", generic-family;
```

**Generic Families:**
- `serif` - Has little lines (Georgia, Times)
- `sans-serif` - No lines (Arial, Verdana)
- `monospace` - Fixed width (Courier, Monaco)
- `cursive` - Handwriting style
- `fantasy` - Decorative

```css
h1 {
  font-family: Georgia, serif;  /* Serif font with serif fallback */
}

p {
  font-family: "Courier New", monospace;  /* Fixed-width with monospace fallback */
}
```

---

### font-size

Controls text size. Can use px, em, rem, %, etc.

```css
h1 {
  font-size: 2.5em;
}

p {
  font-size: 16px;
}

small {
  font-size: 0.875em;
}
```

**Size Units:**
- `px` - Pixels (fixed)
- `em` - Relative to parent (1em = parent size)
- `rem` - Relative to root (1rem = html size, usually 16px)
- `%` - Percentage of parent

**Best Practice:** Use `rem` for consistency

```css
html {
  font-size: 16px;  /* Base size */
}

h1 {
  font-size: 2rem;  /* 32px (2 × 16px) */
}

p {
  font-size: 1rem;  /* 16px */
}
```

---

### font-weight

Controls text thickness.

```css
.light {
  font-weight: 300;
}

.normal {
  font-weight: 400;  /* Default */
}

.bold {
  font-weight: 700;
}

.extra-bold {
  font-weight: 900;
}
```

**Named Values:**
```css
font-weight: normal;    /* 400 */
font-weight: bold;      /* 700 */
font-weight: lighter;   /* Lighter than parent */
font-weight: bolder;    /* Bolder than parent */
```

---

### font-style

Controls italics.

```css
em {
  font-style: italic;
}

strong {
  font-style: normal;  /* Removes italics */
}
```

---

### line-height

Controls vertical spacing between lines. Best as unitless (multiplier).

```css
body {
  line-height: 1.6;  /* 1.6 × font-size */
}

h1 {
  line-height: 1.2;
}

.tight-spacing {
  line-height: 1;
}
```

**Best Practices:**
- Body text: 1.4 - 1.8
- Headings: 1.1 - 1.3

---

### font Shorthand

Combines multiple font properties.

```css
/* Longhand */
p {
  font-style: italic;
  font-weight: bold;
  font-size: 1.2em;
  line-height: 1.5;
  font-family: Arial, sans-serif;
}

/* Shorthand */
p {
  font: italic bold 1.2em/1.5 Arial, sans-serif;
}
```

**Format:** `font: [style] [weight] [size]/[line-height] [family];`

---

## Text Properties

### text-align

Aligns text horizontally.

```css
.left {
  text-align: left;      /* Default */
}

.center {
  text-align: center;
}

.right {
  text-align: right;
}

.justify {
  text-align: justify;   /* Stretches to fill width */
}
```

---

### text-decoration

Adds underline, overline, or line-through.

```css
a {
  text-decoration: none;           /* Remove underline */
}

.underline {
  text-decoration: underline;
}

.line-through {
  text-decoration: line-through;
}

.overline {
  text-decoration: overline;
}
```

---

### text-transform

Changes text case.

```css
.uppercase {
  text-transform: uppercase;   /* TEXT */
}

.lowercase {
  text-transform: lowercase;   /* text */
}

.capitalize {
  text-transform: capitalize;  /* Text */
}

.normal {
  text-transform: none;        /* No change */
}
```

---

### letter-spacing

Increases/decreases space between letters.

```css
.spaced-out {
  letter-spacing: 2px;
}

.tight {
  letter-spacing: -1px;
}
```

---

### word-spacing

Increases/decreases space between words.

```css
p {
  word-spacing: 5px;  /* Extra space between words */
}
```

---

### text-shadow

Adds shadow to text.

```css
h1 {
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
  /* offset-x offset-y blur-radius color */
}

.glow {
  color: white;
  text-shadow: 0 0 10px #ff00ff, 0 0 20px #ff00ff;
}
```

---

### color

Sets text color.

```css
p {
  color: blue;
  color: #0000ff;
  color: rgb(0, 0, 255);
  color: rgba(0, 0, 255, 0.5);  /* 50% transparent */
}
```

---

## Font Families

### Safe Web Fonts (Pre-installed)

```css
/* Sans-serif */
font-family: Arial, sans-serif;
font-family: Verdana, sans-serif;
font-family: Trebuchet MS, sans-serif;

/* Serif */
font-family: Georgia, serif;
font-family: "Times New Roman", serif;

/* Monospace */
font-family: "Courier New", monospace;
font-family: Consolas, monospace;
```

---

## Web Fonts

### Google Fonts

Import fonts from Google's free font library.

```html
<!-- In <head> -->
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&family=Playfair+Display:wght@700&display=swap" rel="stylesheet">
```

```css
body {
  font-family: 'Roboto', sans-serif;
}

h1 {
  font-family: 'Playfair Display', serif;
}
```

### @font-face

Define custom fonts.

```css
@font-face {
  font-family: 'MyFont';
  src: url('myfont.woff2') format('woff2'),
       url('myfont.woff') format('woff');
  font-weight: normal;
  font-style: normal;
}

body {
  font-family: 'MyFont', sans-serif;
}
```

---

## Text Effects

### text-overflow

Handles text that overflows its container.

```css
.truncate {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;  /* Shows ... */
}
```

### word-break

Controls how words break.

```css
.break-word {
  word-break: break-word;  /* Break long words */
}

.break-all {
  word-break: break-all;   /* Break anywhere */
}
```

### white-space

Controls whitespace handling.

```css
.nowrap {
  white-space: nowrap;  /* No wrapping */
}

.pre {
  white-space: pre;     /* Preserve formatting */
}

.pre-wrap {
  white-space: pre-wrap;  /* Preserve formatting, wrap text */
}
```

---

## Complete Typography Example

```html
<style>
  html {
    font-size: 16px;
  }

  body {
    font-family: 'Segoe UI', Tahoma, sans-serif;
    font-size: 1rem;
    line-height: 1.6;
    color: #333;
  }

  h1 {
    font-family: 'Georgia', serif;
    font-size: 2.5rem;
    font-weight: 700;
    line-height: 1.2;
    margin-bottom: 20px;
    text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
  }

  h2 {
    font-size: 1.8rem;
    font-weight: 600;
    margin-top: 30px;
    margin-bottom: 15px;
    color: #2c3e50;
  }

  p {
    margin-bottom: 15px;
    text-align: justify;
  }

  a {
    color: #3498db;
    text-decoration: none;
  }

  a:hover {
    text-decoration: underline;
  }

  .highlight {
    color: #e74c3c;
    font-weight: bold;
  }

  code {
    font-family: 'Courier New', monospace;
    background-color: #f4f4f4;
    padding: 2px 6px;
    border-radius: 3px;
  }
</style>

<h1>Welcome to Typography</h1>
<p>This demonstrates <span class="highlight">professional</span> typography practices.</p>
<p>Use <code>font-family</code> to set typefaces.</p>
```

---

## Key Takeaways

✅ **font-family** sets the typeface with fallbacks  
✅ **font-size** controls text size (use rem for consistency)  
✅ **font-weight** controls thickness  
✅ **line-height** controls vertical spacing (1.4-1.8 for body)  
✅ **text-align** aligns text horizontally  
✅ **color** sets text color  
✅ **Web fonts** allow custom typefaces  
✅ **text-shadow** adds depth to text  

---

## Exercises

### Exercise 1: Create Professional Typography

Create a page with:
- Heading (larger, bold, serif)
- Body text (readable line-height)
- Links (styled differently)
- Code snippets (monospace)

**Solution:**
```css
h1 {
  font-family: Georgia, serif;
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 20px;
}

p {
  font-family: Arial, sans-serif;
  font-size: 1rem;
  line-height: 1.6;
  margin-bottom: 15px;
}

a {
  color: #0066cc;
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}

code {
  font-family: 'Courier New', monospace;
  background-color: #f4f4f4;
  padding: 2px 6px;
}
```

### Exercise 2: Import Google Font

Use Google Fonts to style a page with custom fonts.

**Solution:**
1. Visit fonts.google.com
2. Select fonts
3. Copy import code
4. Apply in CSS

### Exercise 3: Text Effects

Create examples of:
- Truncated text with ellipsis
- Text shadow effects
- Custom letter spacing

---

## Next Steps

→ **Next Topic:** [06 - Flexbox Mastery](../css-advanced/06-flexbox.md)

Learn the powerful flexbox layout system!

---

**Created by:** Solomon Kassa  
**Last Updated:** February 2026
