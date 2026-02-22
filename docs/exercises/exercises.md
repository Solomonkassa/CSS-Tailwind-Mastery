# Exercises & Practice Projects

**Author:** Solomon Kassa  
**Level:** All Levels  
**Last Updated:** February 2026

---

## 📚 Exercise Structure

Each exercise includes:
- **Objective**: What you'll learn
- **Starter Code**: To get you started
- **Challenge**: What to build
- **Hints**: Helpful tips
- **Solution**: Complete working code

---

## 🎯 Beginner Exercises (CSS Fundamentals)

### Exercise 1: Personal Portfolio Page

**Objective**: Apply CSS fundamentals to create a personal portfolio

**Starter Code**:
```html
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>John Doe - Web Developer</header>
  <main>
    <section class="about">
      <h2>About Me</h2>
      <p>I'm learning web development...</p>
    </section>
    <section class="projects">
      <h2>Projects</h2>
      <div class="project">Project 1</div>
      <div class="project">Project 2</div>
    </section>
  </main>
  <footer>Contact: john@example.com</footer>
</body>
</html>
```

**Challenge**:
1. Style the header with background color, padding, centered text
2. Style sections with white background, rounded corners, shadow
3. Create a grid layout for projects (2 columns)
4. Style the footer with dark background
5. Make it responsive (1 column on mobile)

**Hints**:
- Use `display: grid` for project layout
- Use `box-shadow` for depth
- Use media queries for responsive design
- Use `border-radius` for rounded corners

**Solution**: Available in `/examples/exercise-01-portfolio.html`

---

### Exercise 2: Navigation Menu

**Objective**: Create a horizontal navigation menu

**Challenge**:
1. Create a navigation bar with logo and menu items
2. Use flexbox for layout
3. Make logo left-aligned, menu centered, sign-in button right
4. Add hover effects
5. Make responsive (hamburger menu on mobile)

**Solution**: Available in `/examples/exercise-02-navbar.html`

---

### Exercise 3: Card Component

**Objective**: Build a reusable card component

**Challenge**:
1. Create a card with image, title, description, button
2. Use proper spacing with padding/margin
3. Add shadow effect
4. Style the button with hover effect
5. Create multiple cards in a grid

**Solution**: Available in `/examples/exercise-03-cards.html`

---

## 🔧 Intermediate Exercises (Advanced CSS & Flexbox)

### Exercise 4: Responsive Dashboard

**Objective**: Build a dashboard layout using flexbox and grid

**Challenge**:
1. Create a two-column layout (sidebar + main)
2. Add a header spanning both columns
3. Create a grid of widgets in main content
4. Make widgets responsive (change columns on resize)
5. Add a sticky navigation

**Solution**: Available in `/examples/exercise-04-dashboard.html`

---

### Exercise 5: Animated Button

**Objective**: Create interactive button with animations

**Challenge**:
1. Design a button with initial state
2. Add hover state with background change
3. Add active state
4. Create a click animation (scale effect)
5. Add smooth transitions

**Solution**: Available in `/examples/exercise-05-animated-button.html`

---

### Exercise 6: Form Styling

**Objective**: Create a beautiful, accessible form

**Challenge**:
1. Style input fields with focus states
2. Create error states with red borders
3. Style labels, help text, buttons
4. Add transitions for focus effects
5. Make mobile-friendly (full-width on mobile)

**Solution**: Available in `/examples/exercise-06-form-styling.html`

---

## 🎨 Tailwind CSS Exercises

### Exercise 7: Tailwind Button System

**Objective**: Build a component library with Tailwind

**Challenge**:
1. Create button variants (primary, secondary, success, danger)
2. Create button sizes (sm, md, lg)
3. Add loading states
4. Create disabled states
5. Add icons to buttons

**Solution**:
```html
<!-- Primary Button -->
<button class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600">
  Primary
</button>

<!-- Secondary Button -->
<button class="bg-gray-200 text-gray-800 px-4 py-2 rounded hover:bg-gray-300">
  Secondary
</button>

<!-- Large Button -->
<button class="bg-blue-500 text-white px-6 py-3 text-lg rounded">
  Large Button
</button>

<!-- Disabled -->
<button class="bg-gray-300 text-gray-500 px-4 py-2 rounded cursor-not-allowed">
  Disabled
</button>
```

---

### Exercise 8: Tailwind Landing Page

**Objective**: Build a complete landing page with Tailwind

**Challenge**:
1. Create hero section with CTA button
2. Add features section with 3 columns
3. Create pricing section with cards
4. Add testimonials section
5. Create footer with links
6. Make responsive (stack on mobile)

**Solution**: Available in `/examples/exercise-08-landing.html`

---

### Exercise 9: Tailwind E-commerce Product

**Objective**: Build a product showcase with Tailwind

**Challenge**:
1. Display product image with gallery
2. Show product name, price, rating
3. Create "Add to Cart" button
4. Add color/size selectors
5. Show related products grid
6. Make responsive

**Solution**: Available in `/examples/exercise-09-product.html`

---

## 🚀 Advanced Projects

### Project 1: Complete Web App UI

**Objective**: Build a multi-page application UI

**Components needed**:
- Dashboard with analytics
- User profile page
- Settings page
- Notifications center
- Search interface
- Admin panel

---

### Project 2: Design System

**Objective**: Create a complete design system

**Include**:
- Color system
- Typography scale
- Button component library
- Form components
- Card patterns
- Documentation

---

### Project 3: Responsive Blog

**Objective**: Build a full-featured blog

**Features**:
- Post listing with pagination
- Individual post pages
- Search functionality
- Dark mode toggle
- Social sharing
- Comments section

---

## 📊 Project Complexity Levels

```
Beginner    →  Simple layouts, basic styling
              (3-5 hours)

Intermediate →  Complex layouts, animations
              (10-20 hours)

Advanced    →  Full applications, optimization
              (50+ hours)
```

---

## ✅ Submission Guidelines

When submitting exercises or projects:

1. **Code Quality**
   - Clean, well-organized code
   - Comments for complex logic
   - Meaningful variable names
   - No console errors

2. **Responsiveness**
   - Works on mobile
   - Works on tablet
   - Works on desktop
   - No layout breaks

3. **Accessibility**
   - Proper semantic HTML
   - Alt text for images
   - Keyboard navigation
   - Color contrast

4. **Documentation**
   - How to run the project
   - Features included
   - Browser compatibility
   - Known issues

---

## 🎯 Self-Assessment Checklist

After completing each exercise, ask yourself:

**Understanding**:
- [ ] I understand what I built
- [ ] I can explain my code to someone
- [ ] I know why I used certain CSS properties

**Quality**:
- [ ] My code is clean and organized
- [ ] No unused CSS or HTML
- [ ] Follows best practices
- [ ] Works in multiple browsers

**Responsiveness**:
- [ ] Looks good on mobile
- [ ] Looks good on tablet
- [ ] Looks good on desktop
- [ ] No horizontal scrolling

**Accessibility**:
- [ ] Semantic HTML used
- [ ] Images have alt text
- [ ] Good color contrast
- [ ] Keyboard navigable

**Enhancement**:
- [ ] Smooth transitions
- [ ] Hover effects
- [ ] Professional appearance
- [ ] Great user experience

---

## 📞 Getting Help

- Check related tutorial sections
- Review code examples
- Ask in GitHub Discussions
- Open an issue with your code
- Reference external resources

---

## 🏆 Challenge Ideas

**Difficulty Level: Extreme**

- Build a clone of a popular website
- Create a design system with 50+ components
- Build a responsive admin dashboard
- Create an interactive infographic
- Build a game using CSS (CSS Mario, etc.)

---

**Happy Practicing! 🚀**

*Remember: The best way to learn CSS is by doing. Don't just read about it—build with it!*

---

**Created by:** Solomon Kassa  
**Last Updated:** February 2026
