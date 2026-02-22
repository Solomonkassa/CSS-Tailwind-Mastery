# CSS Best Practices

**Author:** Solomon Kassa  
**Level:** All Levels  
**Last Updated:** February 2026

---

## 📚 Table of Contents
1. [Naming Conventions](#naming-conventions)
2. [Organization](#organization)
3. [Performance](#performance)
4. [Maintainability](#maintainability)
5. [Browser Compatibility](#browser-compatibility)
6. [Accessibility](#accessibility)

---

## Naming Conventions

### Use Meaningful Class Names

❌ **Bad:**
```css
.red { color: red; }
.big { font-size: 20px; }
.mtop { margin-top: 10px; }
```

✅ **Good:**
```css
.error { color: red; }
.heading-large { font-size: 20px; }
.section-title { margin-top: 10px; }
```

### BEM Methodology

Block-Element-Modifier naming system:

```css
/* Block */
.card { }

/* Element */
.card__header { }
.card__body { }
.card__footer { }

/* Modifier */
.card--large { }
.card--highlighted { }
.card__header--centered { }
```

### Avoid Type Selectors

❌ **Avoid:**
```css
div.container { }
p.text { }
```

✅ **Better:**
```css
.container { }
.text { }
```

---

## Organization

### Group Related Styles

```css
/* ========================================
   LAYOUT
   ======================================== */

.container {
  display: flex;
  flex-wrap: wrap;
}

/* ========================================
   TYPOGRAPHY
   ======================================== */

h1 {
  font-size: 2rem;
  font-weight: bold;
}

/* ========================================
   COMPONENTS
   ======================================== */

.button {
  padding: 10px 20px;
  border-radius: 5px;
}
```

### File Structure

```
css/
├── base.css           /* Reset, global styles */
├── variables.css      /* CSS custom properties */
├── layout.css         /* Grid, flexbox layouts */
├── components.css     /* Reusable components */
├── utilities.css      /* Utility classes */
└── responsive.css     /* Media queries */
```

---

## Performance

### Minimize CSS

```css
/* ❌ Avoid specificity wars */
.container .wrapper .content p { }
.container .wrapper .content p { }

/* ✅ Simpler selectors */
.article-text { }
```

### Use CSS Variables for Theming

```css
:root {
  --primary-color: #3498db;
  --secondary-color: #2ecc71;
  --spacing-unit: 8px;
}

.button {
  background-color: var(--primary-color);
  padding: calc(var(--spacing-unit) * 2);
}
```

### Avoid Redundant Rules

```css
/* ❌ Bad */
.button {
  background-color: blue;
  color: white;
  padding: 10px 20px;
}

.button-small {
  background-color: blue;
  color: white;
  padding: 5px 10px;
}

/* ✅ Good */
.button {
  background-color: blue;
  color: white;
  padding: 10px 20px;
}

.button-small {
  padding: 5px 10px;
}
```

---

## Maintainability

### Keep It DRY (Don't Repeat Yourself)

```css
/* ❌ Repetitive */
.card {
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.dialog {
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

/* ✅ Reusable */
.rounded-elevated {
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.card {
  @extend .rounded-elevated;
}

.dialog {
  @extend .rounded-elevated;
}
```

### Document Complex Styles

```css
/* 
  Fixed positioning with sticky fallback
  Supports browsers without position: sticky
*/
.sticky-header {
  position: sticky;
  top: 0;
  z-index: 100;
}
```

### Use Consistent Units

```css
/* ✅ Consistent */
html { font-size: 16px; }

body {
  font-size: 1rem;        /* 16px */
  line-height: 1.6;
}

h1 { font-size: 2rem; }    /* 32px */
h2 { font-size: 1.5rem; }  /* 24px */
```

---

## Browser Compatibility

### Use Vendor Prefixes When Needed

```css
.box {
  -webkit-transform: rotate(45deg);
  -moz-transform: rotate(45deg);
  transform: rotate(45deg);
}
```

### Feature Fallbacks

```css
/* Fallback for old browsers */
.container {
  display: flex;
  display: grid;  /* Modern browsers use this */
  grid-template-columns: repeat(3, 1fr);
}
```

### Check Browser Support

Use [Can I Use](https://caniuse.com) before using new CSS features:

```css
/* Good browser support */
.flex-container { display: flex; }

/* Need fallbacks */
.grid-container {
  display: grid;  /* ~90% browsers */
  /* Consider fallback for older browsers */
}
```

---

## Accessibility

### Color Contrast

✅ **Good contrast** (WCAG AA):
```css
.text {
  color: #000;      /* Black on white: 21:1 */
  background: #fff;
}
```

❌ **Poor contrast**:
```css
.text {
  color: #777;      /* Gray on white: 5:1 (not WCAG AA) */
  background: #fff;
}
```

### Focus States

Always include focus styles for keyboard navigation:

```css
button:focus {
  outline: 2px solid #3498db;
  outline-offset: 2px;
}

input:focus {
  border-color: #3498db;
  box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.1);
}
```

### Semantic HTML with CSS

```html
<!-- Semantic HTML -->
<button>Submit</button>

<!-- Styled with CSS -->
<style>
  button {
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    background-color: #3498db;
    color: white;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #2980b9;
  }
  
  button:focus {
    outline: 2px solid #2ecc71;
  }
</style>
```

### Avoid Color Alone

Don't convey information through color only:

```css
/* ✅ Good - uses color + icon/text */
.error {
  color: red;
  border-left: 4px solid red;
}

/* ❌ Bad - color only */
.error {
  color: red;
}
```

---

## Common Pitfalls to Avoid

### 1. Over-Nesting

```css
/* ❌ Avoid deep nesting */
.container {
  .wrapper {
    .content {
      .section {
        p { }
      }
    }
  }
}

/* ✅ Keep shallow */
.section-content { }
```

### 2. Using !important

```css
/* ❌ Avoid !important */
.button {
  background-color: blue !important;
}

/* ✅ Use proper specificity */
button.button {
  background-color: blue;
}
```

### 3. Inline Styles

```html
<!-- ❌ Avoid -->
<div style="color: red; font-size: 20px;">Text</div>

<!-- ✅ Use classes -->
<div class="error-text">Text</div>
```

### 4. Magic Numbers

```css
/* ❌ Unclear */
.section { margin-top: 27px; }

/* ✅ Meaningful */
:root { --spacing-large: 28px; }
.section { margin-top: var(--spacing-large); }
```

---

## Performance Checklist

- [ ] CSS is minified
- [ ] Remove unused CSS
- [ ] Use shorthand properties
- [ ] Minimize selector specificity
- [ ] Use CSS variables for repeated values
- [ ] Avoid heavy animations on load
- [ ] Use `will-change` sparingly
- [ ] Modern browser features with fallbacks

---

## Tooling & Linting

### CSS Linters

- **Stylelint** - Find and fix CSS errors
- **CSSLint** - Identify problems in CSS
- **Prettier** - Format CSS automatically

### Setup Example

```bash
npm install --save-dev stylelint postcss
```

```json
{
  "extends": "stylelint-config-standard",
  "rules": {
    "indentation": 2,
    "color-no-invalid-hex": true
  }
}
```

---

## Code Review Checklist

When reviewing CSS:

- [ ] Follows naming conventions
- [ ] No unnecessary specificity
- [ ] Proper indentation and formatting
- [ ] Comments for complex logic
- [ ] No hardcoded colors (use variables)
- [ ] Mobile-first responsive design
- [ ] Accessibility considerations
- [ ] Browser compatibility checked
- [ ] Performance optimized
- [ ] Consistent with project style guide

---

**Created by:** Solomon Kassa  
**Last Updated:** February 2026
