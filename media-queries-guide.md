# Complete CSS Media Queries Guide
## Understanding and Mastering Responsive Design

### 1. Understanding Media Queries

#### Basic Syntax
```css
@media mediatype and (condition) {
    /* CSS rules go here */
}
```

**Media Types:**
- `screen` - For computer screens, tablets, phones
- `print` - For printed documents and print preview
- `all` - Default, for all media types
- `speech` - For screen readers

### 2. Common Breakpoints

```css
/* Extra small devices (phones) */
@media screen and (max-width: 576px) {
    /* styles for phones */
}

/* Small devices (tablets) */
@media screen and (min-width: 577px) and (max-width: 768px) {
    /* styles for tablets */
}

/* Medium devices (laptops) */
@media screen and (min-width: 769px) and (max-width: 992px) {
    /* styles for laptops */
}

/* Large devices (desktops) */
@media screen and (min-width: 993px) and (max-width: 1200px) {
    /* styles for desktops */
}

/* Extra large devices */
@media screen and (min-width: 1201px) {
    /* styles for large desktops */
}
```

### 3. Mobile-First Approach

```css
/* Base styles for mobile */
.container {
    width: 100%;
    padding: 15px;
}

/* Tablet styles */
@media screen and (min-width: 768px) {
    .container {
        width: 750px;
        margin: 0 auto;
    }
}

/* Desktop styles */
@media screen and (min-width: 1024px) {
    .container {
        width: 960px;
    }
}

/* Large desktop styles */
@media screen and (min-width: 1200px) {
    .container {
        width: 1140px;
    }
}
```

### 4. Common Media Features

```css
/* Width and Height */
@media screen and (min-width: 768px) {...}
@media screen and (max-width: 1200px) {...}
@media screen and (min-height: 600px) {...}
@media screen and (max-height: 800px) {...}

/* Orientation */
@media screen and (orientation: portrait) {...}
@media screen and (orientation: landscape) {...}

/* Aspect Ratio */
@media screen and (aspect-ratio: 16/9) {...}
@media screen and (min-aspect-ratio: 1/1) {...}

/* Resolution */
@media screen and (min-resolution: 300dpi) {...}
@media screen and (max-resolution: 150dpi) {...}

/* Multiple Conditions */
@media screen and (min-width: 768px) and (orientation: landscape) {...}
```

### 5. Real-World Examples

#### Responsive Navigation
```html
<nav class="main-nav">
    <button class="mobile-menu">☰</button>
    <ul class="nav-links">
        <li><a href="#">Home</a></li>
        <li><a href="#">About</a></li>
        <li><a href="#">Services</a></li>
        <li><a href="#">Contact</a></li>
    </ul>
</nav>
```

```css
/* Mobile First Approach */
.main-nav {
    padding: 1rem;
}

.nav-links {
    display: none; /* Hidden by default on mobile */
}

.mobile-menu {
    display: block;
}

/* Tablet and above */
@media screen and (min-width: 768px) {
    .mobile-menu {
        display: none; /* Hide hamburger menu */
    }
    
    .nav-links {
        display: flex;
        gap: 20px;
    }
}
```

#### Responsive Grid Layout
```css
.grid {
    display: grid;
    gap: 20px;
    padding: 20px;
    
    /* Mobile: 1 column */
    grid-template-columns: 1fr;
}

/* Tablet: 2 columns */
@media screen and (min-width: 768px) {
    .grid {
        grid-template-columns: repeat(2, 1fr);
    }
}

/* Desktop: 3 columns */
@media screen and (min-width: 1024px) {
    .grid {
        grid-template-columns: repeat(3, 1fr);
    }
}

/* Large Desktop: 4 columns */
@media screen and (min-width: 1200px) {
    .grid {
        grid-template-columns: repeat(4, 1fr);
    }
}
```

### 6. Advanced Techniques

#### Using Container Queries (Modern Browsers)
```css
.card-container {
    container-type: inline-size;
}

@container (min-width: 400px) {
    .card {
        display: grid;
        grid-template-columns: 200px 1fr;
    }
}
```

#### Complex Conditions
```css
/* Combining multiple conditions */
@media screen and (min-width: 768px) and (orientation: landscape) and (min-height: 500px) {
    /* Styles for landscape tablets with sufficient height */
}

/* Using 'not' and 'or' */
@media not screen and (color), print and (color) {
    /* Styles for non-color screens or color printers */
}
```

### 7. Common Responsive Patterns

#### Card Layout
```css
.card {
    padding: 20px;
    margin: 10px;
}

/* Mobile */
@media screen and (max-width: 576px) {
    .card {
        margin: 10px 0;
    }
    
    .card img {
        width: 100%;
        height: auto;
    }
}

/* Tablet */
@media screen and (min-width: 577px) and (max-width: 768px) {
    .card {
        display: grid;
        grid-template-columns: 200px 1fr;
        gap: 20px;
    }
}
```

#### Typography Scaling
```css
/* Base (Mobile) */
html {
    font-size: 16px;
}

h1 { font-size: 1.75rem; }
h2 { font-size: 1.5rem; }

/* Tablet */
@media screen and (min-width: 768px) {
    html {
        font-size: 18px;
    }
    
    h1 { font-size: 2rem; }
    h2 { font-size: 1.75rem; }
}

/* Desktop */
@media screen and (min-width: 1024px) {
    html {
        font-size: 20px;
    }
    
    h1 { font-size: 2.5rem; }
    h2 { font-size: 2rem; }
}
```

### 8. Best Practices

1. **Always Design Mobile-First**
   - Start with base styles for mobile
   - Use `min-width` queries to scale up
   - Keeps code cleaner and more maintainable

2. **Use Logical Breakpoints**
   ```css
   /* Don't use random numbers */
   @media screen and (min-width: 783px) {...}

   /* Do use standard breakpoints */
   @media screen and (min-width: 768px) {...}
   ```

3. **Avoid Device-Specific Breakpoints**
   ```css
   /* Don't */
   @media screen and (min-width: 768px) and (max-width: 1024px) {...}

   /* Do */
   @media screen and (min-width: 768px) {...}
   ```

4. **Test Multiple Devices**
   - Use browser dev tools
   - Test on real devices
   - Consider orientation changes