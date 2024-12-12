# Complete CSS Flexbox Guide
## A Visual and Practical Guide for Beginners

### 1. Understanding Flexbox Basics

First, let's understand what Flexbox is:
- It's a one-dimensional layout method
- Helps distribute space among items
- Works in either rows or columns
- Makes responsive design easier

### 2. Basic Flexbox Container

```html
<div class="container">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
</div>
```

```css
.container {
    display: flex;
    /* This makes the container a flex container */
    
    background-color: #f0f0f0;
    padding: 10px;
}

.item {
    background-color: #3498db;
    color: white;
    padding: 20px;
    margin: 5px;
}
```

**Explanation**: 
- `display: flex` turns a container into a flex container
- Child elements automatically become flex items
- Items are placed in a row by default

### 3. Flex Direction

```css
.container {
    display: flex;
    flex-direction: row;          /* Default - left to right */
    /* OR */
    flex-direction: column;       /* Top to bottom */
    /* OR */
    flex-direction: row-reverse;  /* Right to left */
    /* OR */
    flex-direction: column-reverse; /* Bottom to top */
}
```

**Real World Example:**
```html
<nav class="navbar">
    <div class="logo">Logo</div>
    <div class="menu">
        <a href="#">Home</a>
        <a href="#">About</a>
        <a href="#">Contact</a>
    </div>
</nav>
```

```css
.navbar {
    display: flex;
    justify-content: space-between;
    padding: 20px;
    background-color: #333;
}

.menu {
    display: flex;
    gap: 20px;  /* Space between menu items */
}

.menu a {
    color: white;
    text-decoration: none;
}
```

### 4. Justifying Content (Main Axis)

```css
.container {
    display: flex;
    justify-content: flex-start;      /* Default */
    /* OR */
    justify-content: center;          /* Center items */
    /* OR */
    justify-content: flex-end;        /* End of container */
    /* OR */
    justify-content: space-between;   /* Equal space between items */
    /* OR */
    justify-content: space-around;    /* Equal space around items */
    /* OR */
    justify-content: space-evenly;    /* Equal space between and edges */
}
```

**Card Layout Example:**
```html
<div class="card-container">
    <div class="card">
        <h2>Card 1</h2>
        <p>Some content</p>
    </div>
    <div class="card">
        <h2>Card 2</h2>
        <p>Some content</p>
    </div>
    <div class="card">
        <h2>Card 3</h2>
        <p>Some content</p>
    </div>
</div>
```

```css
.card-container {
    display: flex;
    justify-content: space-between;
    gap: 20px;
    padding: 20px;
}

.card {
    flex: 1;  /* Each card takes equal space */
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 8px;
}
```

### 5. Aligning Items (Cross Axis)

```css
.container {
    display: flex;
    height: 300px;  /* Give container height to see alignment */
    align-items: stretch;      /* Default - full height */
    /* OR */
    align-items: flex-start;  /* Top */
    /* OR */
    align-items: center;      /* Center */
    /* OR */
    align-items: flex-end;    /* Bottom */
    /* OR */
    align-items: baseline;    /* Align by text baseline */
}
```

### 6. Flexible Items

```css
.item {
    flex-grow: 1;      /* Ability to grow */
    flex-shrink: 1;    /* Ability to shrink */
    flex-basis: 200px; /* Starting size */
    
    /* Shorthand */
    flex: 1 1 200px;   /* grow shrink basis */
}
```

**Example: Image Gallery**
```html
<div class="gallery">
    <div class="image-container">
        <img src="image1.jpg" alt="Image 1">
    </div>
    <div class="image-container">
        <img src="image2.jpg" alt="Image 2">
    </div>
    <div class="image-container">
        <img src="image3.jpg" alt="Image 3">
    </div>
</div>
```

```css
.gallery {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    padding: 20px;
}

.image-container {
    flex: 1 1 300px; /* Grow, shrink, basis */
    max-width: 400px;
}

.image-container img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}
```

### 7. Responsive Flexbox

```html
<div class="responsive-layout">
    <header class="header">Header</header>
    <div class="content-wrapper">
        <main class="main-content">Main Content</main>
        <aside class="sidebar">Sidebar</aside>
    </div>
    <footer class="footer">Footer</footer>
</div>
```

```css
.responsive-layout {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
}

.content-wrapper {
    display: flex;
    flex: 1;
}

.main-content {
    flex: 3;  /* Takes 3/4 of space */
    padding: 20px;
}

.sidebar {
    flex: 1;  /* Takes 1/4 of space */
    padding: 20px;
    background-color: #f0f0f0;
}

/* Mobile Responsive */
@media (max-width: 768px) {
    .content-wrapper {
        flex-direction: column;
    }
    
    .sidebar {
        order: -1; /* Moves sidebar above main content */
    }
}
```

### 8. Common Patterns and Use Cases

1. **Centering Content**
```css
.center-container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh; /* Full viewport height */
}
```

2. **Navigation Bar**
```css
.navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
}
```

3. **Card Grid**
```css
.card-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
}

.card {
    flex: 1 1 300px;
}
```