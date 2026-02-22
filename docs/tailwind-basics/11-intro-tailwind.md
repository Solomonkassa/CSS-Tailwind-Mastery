# 11 - Introduction to Tailwind CSS

**Author:** Solomon Kassa  
**Level:** Beginner  
**Prerequisites:** CSS fundamentals knowledge  
**Time to Complete:** 2-3 hours

---

## 📚 Table of Contents
1. [What is Tailwind CSS?](#what-is-tailwind-css)
2. [Why Tailwind?](#why-tailwind)
3. [Installation](#installation)
4. [First Steps](#first-steps)
5. [Tailwind vs Traditional CSS](#tailwind-vs-traditional-css)
6. [Key Takeaways](#key-takeaways)
7. [Exercises](#exercises)

---

## What is Tailwind CSS?

**Tailwind CSS** is a utility-first CSS framework that helps you build custom designs without leaving your HTML.

Instead of writing CSS classes like:
```css
.btn-primary {
  background-color: blue;
  color: white;
  padding: 10px 20px;
  border-radius: 5px;
}
```

With Tailwind, you write:
```html
<button class="bg-blue-500 text-white px-5 py-2 rounded">
  Click me
</button>
```

---

## Why Tailwind?

### ✨ Key Benefits

| Benefit | Description |
|---------|-------------|
| **Speed** | Build UIs faster without context switching |
| **Consistency** | Built-in design system (colors, spacing, etc.) |
| **Responsive** | Mobile-first responsive design built-in |
| **Customizable** | Easily configure colors, fonts, sizes |
| **Small** | Unused CSS is automatically removed |
| **Dark Mode** | First-class dark mode support |
| **Accessibility** | Built-in focus states, transitions |

### Traditional CSS vs Tailwind

**Traditional CSS:**
```css
/* styles.css */
.card {
  background-color: white;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  padding: 20px;
}

.card-title {
  font-size: 1.5rem;
  font-weight: bold;
  margin-bottom: 10px;
}
```

```html
<!-- index.html -->
<div class="card">
  <h2 class="card-title">Title</h2>
  <p>Content</p>
</div>
```

**Tailwind CSS:**
```html
<div class="bg-white rounded-lg shadow p-5">
  <h2 class="text-xl font-bold mb-2">Title</h2>
  <p>Content</p>
</div>
```

---

## Installation

### Method 1: CDN (Quick Start)

For learning and prototyping:

```html
<!DOCTYPE html>
<html>
<head>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body>
  <button class="bg-blue-500 text-white px-4 py-2 rounded">
    Click me
  </button>
</body>
</html>
```

### Method 2: npm (Recommended for Production)

```bash
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

**Configure tailwind.config.js:**
```js
module.exports = {
  content: [
    "./index.html",
    "./src/**/*.{js,jsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

**Add to your CSS file:**
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

---

## First Steps

### Basic Tailwind Classes

```html
<!-- Styling text -->
<p class="text-blue-500">Blue text</p>
<p class="text-lg font-bold">Large bold text</p>

<!-- Backgrounds -->
<div class="bg-red-500">Red background</div>

<!-- Padding & Margin -->
<div class="p-5 m-4">Padded and margined</div>

<!-- Flexbox -->
<div class="flex justify-center items-center">
  <p>Centered content</p>
</div>

<!-- Responsive -->
<div class="w-full md:w-1/2 lg:w-1/3">
  Responsive width
</div>

<!-- Hover effects -->
<button class="bg-blue-500 hover:bg-blue-600">
  Hover me
</button>
```

---

## Tailwind vs Traditional CSS

### Learning Curve

**Traditional CSS:**
- Create CSS classes with meaningful names
- Write all styles in separate file
- Manage class organization
- Share styles via CSS
- Context switching (HTML → CSS → HTML)

**Tailwind CSS:**
- Use pre-built utility classes
- Styles in HTML
- No naming conventions to learn
- All styles visible in one place
- Faster development flow

### Code Comparison

**Task:** Create a card component

**Traditional CSS (3 files):**
```css
/* styles.css */
.card {
  background: white;
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.card-header {
  font-size: 1.5rem;
  font-weight: bold;
  margin-bottom: 15px;
}

.card-body {
  color: #666;
  line-height: 1.6;
}
```

```html
<!-- index.html -->
<div class="card">
  <div class="card-header">Title</div>
  <div class="card-body">Content</div>
</div>
```

**Tailwind CSS (1 file):**
```html
<div class="bg-white rounded-lg shadow-md p-5">
  <div class="text-xl font-bold mb-4">Title</div>
  <div class="text-gray-600 leading-relaxed">Content</div>
</div>
```

---

## Key Takeaways

✅ **Utility-First** approach: Use small, reusable classes  
✅ **No CSS files needed** for most styling  
✅ **Responsive by default**: Build mobile-first designs  
✅ **Easy customization**: Configuration in one place  
✅ **Smaller bundle size**: Unused CSS is removed  
✅ **Faster development**: Build UIs quickly  

---

## Exercises

### Exercise 1: Your First Tailwind Component

Create a button using Tailwind:

**Solution:**
```html
<button class="bg-blue-500 text-white px-6 py-2 rounded-lg hover:bg-blue-600 transition">
  Click Me
</button>
```

### Exercise 2: Build a Simple Card

Create a card with:
- White background
- Shadow effect
- Rounded corners
- Padding inside
- Title and description

**Solution:**
```html
<div class="bg-white rounded-lg shadow-lg p-6">
  <h2 class="text-2xl font-bold mb-2">Card Title</h2>
  <p class="text-gray-600">Card description goes here</p>
</div>
```

### Exercise 3: Responsive Layout

Create a layout that stacks on mobile, shows 2 columns on tablet, 3 on desktop.

**Solution:**
```html
<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
  <div class="bg-white p-4 rounded">Item 1</div>
  <div class="bg-white p-4 rounded">Item 2</div>
  <div class="bg-white p-4 rounded">Item 3</div>
</div>
```

---

## Next Steps

→ **Next Topic:** [12 - Utility-First Approach](./12-utility-first.md)

Deep dive into the utility-first methodology!

---

**Created by:** Solomon Kassa  
**Last Updated:** February 2026
