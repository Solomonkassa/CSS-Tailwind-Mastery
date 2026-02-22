# 01 - Getting Started with CSS

**Author:** Solomon Kassa  
**Level:** Beginner  
**Prerequisites:** Basic HTML knowledge  
**Time to Complete:** 2-3 hours

---

## 📚 Table of Contents
1. [What is CSS?](#what-is-css)
2. [Why CSS Matters](#why-css-matters)
3. [CSS Syntax](#css-syntax)
4. [Ways to Add CSS](#ways-to-add-css)
5. [Your First CSS](#your-first-css)
6. [CSS Comments](#css-comments)
7. [Key Takeaways](#key-takeaways)
8. [Exercises](#exercises)

---

## What is CSS?

**CSS (Cascading Style Sheets)** is a stylesheet language used to describe how HTML elements are displayed. While HTML provides structure, CSS provides presentation and styling.

### The Holy Trinity of Web Development

```
┌─────────────┐
│    HTML     │  Structure (Content)
├─────────────┤
│     CSS     │  Presentation (Styling)
├─────────────┤
│ JavaScript  │  Behavior (Interactivity)
└─────────────┘
```

---

## Why CSS Matters

### ✨ Benefits of CSS

| Benefit | Description |
|---------|-------------|
| **Separation of Concerns** | Keep content separate from styling |
| **Maintainability** | Update styles globally, not in every HTML element |
| **Reusability** | Apply same styles to multiple elements |
| **Responsiveness** | Create designs that work on all devices |
| **Performance** | External CSS files are cached by browsers |
| **Flexibility** | Create any design you can imagine |

---

## CSS Syntax

CSS uses a simple rule-based syntax:

### Basic Structure

```css
selector {
  property: value;
  property: value;
}
```

### Example

```css
/* This is a CSS rule */
h1 {
  color: blue;           /* property: value */
  font-size: 24px;       /* another property: value */
  text-align: center;    /* and another */
}
```

### Anatomy Breakdown

```
┌─ Selector ─┬────────── Declaration Block ────────┐
│            │  ┌─ Declaration ─┐                   │
│     h1     │  │  color: blue;  │  ← One rule      │
│            │  │ font-size: 2em │  ← Another rule  │
│            │  └────────────────┘                   │
└────────────┴────────────────────────────────────────┘
  ↓              ↓          ↓
Selector    Property    Value
(targets   (what to    (how to
 elements)  change)    change it)
```

---

## Ways to Add CSS

There are three main methods to add CSS to your HTML:

### 1️⃣ Inline CSS

Apply styles directly to HTML elements using the `style` attribute.

```html
<p style="color: red; font-size: 18px;">This is inline CSS</p>
<h1 style="background-color: yellow;">Inline heading</h1>
```

**Pros:** Quick for testing  
**Cons:** Difficult to maintain, not reusable, mixes content with styling

❌ **Not Recommended for Production**

---

### 2️⃣ Internal CSS

Add CSS inside a `<style>` tag in the HTML document's `<head>`.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    p {
      color: red;
      font-size: 18px;
    }
    h1 {
      background-color: yellow;
    }
  </style>
</head>
<body>
  <p>This is styled with internal CSS</p>
  <h1>Internal CSS heading</h1>
</body>
</html>
```

**Pros:** Keeps CSS in one place, reusable within the page  
**Cons:** Not reusable across multiple pages, can make HTML file large

⚠️ **Good for single-page projects only**

---

### 3️⃣ External CSS (✅ Recommended)

Link to an external `.css` file using the `<link>` tag.

**HTML File:**
```html
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <p>This is styled with external CSS</p>
  <h1>External CSS heading</h1>
</body>
</html>
```

**CSS File (styles.css):**
```css
p {
  color: red;
  font-size: 18px;
}

h1 {
  background-color: yellow;
}
```

**Pros:** Reusable across multiple pages, clean separation, easy to maintain, cached by browsers  
**Cons:** Requires an extra file

✅ **Best Practice - Use This Method**

---

## Your First CSS

Let's create a complete HTML file with external CSS:

### Project Structure
```
my-project/
├── index.html
└── style.css
```

### Step 1: Create HTML file (index.html)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My First CSS Page</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <h1>Welcome to My Website</h1>
    <p>My first CSS project</p>
  </header>
  
  <main>
    <section>
      <h2>About Me</h2>
      <p>I'm learning CSS and it's awesome!</p>
    </section>
    
    <section>
      <h2>My Interests</h2>
      <ul>
        <li>Web Development</li>
        <li>Design</li>
        <li>Learning</li>
      </ul>
    </section>
  </main>
  
  <footer>
    <p>&copy; 2026 My Website. All rights reserved.</p>
  </footer>
</body>
</html>
```

### Step 2: Create CSS file (style.css)

```css
/* Global styles */
body {
  font-family: Arial, sans-serif;
  line-height: 1.6;
  margin: 0;
  padding: 20px;
  background-color: #f4f4f4;
  color: #333;
}

/* Header styles */
header {
  background-color: #2c3e50;
  color: white;
  padding: 20px;
  text-align: center;
  border-radius: 5px;
  margin-bottom: 20px;
}

header h1 {
  margin: 0;
  font-size: 2.5em;
}

header p {
  margin: 10px 0 0 0;
  font-size: 1.2em;
}

/* Main content */
main {
  background-color: white;
  padding: 20px;
  border-radius: 5px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

section {
  margin-bottom: 20px;
}

section h2 {
  color: #2c3e50;
  border-bottom: 2px solid #3498db;
  padding-bottom: 10px;
}

section p {
  line-height: 1.8;
}

/* List styles */
ul {
  list-style-type: none;
  padding: 0;
}

ul li {
  background-color: #ecf0f1;
  margin: 5px 0;
  padding: 10px;
  border-left: 4px solid #3498db;
}

/* Footer styles */
footer {
  background-color: #2c3e50;
  color: white;
  text-align: center;
  padding: 15px;
  margin-top: 20px;
  border-radius: 5px;
}
```

### Result
This creates a nicely styled webpage with:
- Colored header and footer
- Structured content with sections
- Styled lists
- Professional look and feel

---

## CSS Comments

Use comments to explain your CSS code. They're ignored by browsers but help you and others understand your code.

### Single Line Comments

```css
/* This is a single-line comment */
color: blue;
```

### Multi-Line Comments

```css
/*
  This is a multi-line comment.
  Use it for longer explanations
  about your CSS rules.
*/
color: blue;
```

### Best Practices for Comments

```css
/* ========================================
   HEADER STYLES
   ======================================== */

header {
  background-color: navy;
}

/* Main content container */
main {
  padding: 20px;
}

/* Use comments to separate sections */
/* ========================================
   FOOTER STYLES
   ======================================== */

footer {
  background-color: navy;
}
```

---

## Key Takeaways

✅ **CSS Purpose**: CSS styles HTML elements  
✅ **Three Methods**: Inline, Internal, External CSS  
✅ **External CSS**: Best practice for professional projects  
✅ **Basic Syntax**: `selector { property: value; }`  
✅ **Comments**: Use `/* comment */` to explain your code  
✅ **Separation**: Keep content (HTML) separate from styling (CSS)  

---

## Exercises

### Exercise 1: Create Your First Styled Page
Create an HTML page with external CSS that includes:
- A header with a background color
- A main section with some paragraphs
- A footer with copyright information
- At least 5 different CSS properties

**Solution:**
```html
<!-- index.html -->
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <h1>My Portfolio</h1>
  </header>
  <main>
    <p>Welcome to my page!</p>
  </main>
  <footer>
    <p>&copy; 2026</p>
  </footer>
</body>
</html>
```

```css
/* style.css */
header {
  background-color: #333;
  color: white;
  padding: 20px;
}

main {
  padding: 40px;
}

footer {
  background-color: #333;
  color: white;
  padding: 10px;
  text-align: center;
}
```

### Exercise 2: Inline vs External
Create the same page using:
1. Inline CSS
2. Internal CSS
3. External CSS

Observe the differences and note which is easiest to maintain.

### Exercise 3: Comment Your Code
Take any CSS file and add comments to explain:
- What each section does
- Why certain styles are applied
- Any special considerations

---

## Next Steps

→ **Next Topic:** [02 - Selectors & Specificity](./02-selectors-specificity.md)

Learn about CSS selectors and how specificity works!

---

## Related Resources

📖 **MDN Documentation**
- [Getting Started with CSS](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps)
- [CSS Syntax](https://developer.mozilla.org/en-US/docs/Web/CSS/Syntax)

🎮 **Interactive Learning**
- [CSS Diner](https://flukeout.github.io/) - Selector practice game

---

**Created by:** Solomon Kassa  
**Last Updated:** February 2026
