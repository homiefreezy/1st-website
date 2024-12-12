# CSS Grid Layout: Complete Guide
## From Basics to Advanced Concepts

### 1. Grid Container Basics

```html
<div class="grid-container">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
    <div class="item">4</div>
    <div class="item">5</div>
    <div class="item">6</div>
</div>
```

```css
.grid-container {
    display: grid;
    /* Basic 3x2 grid */
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(2, 100px);
    gap: 10px;
}

.item {
    background-color: #3498db;
    color: white;
    padding: 20px;
    text-align: center;
}
```

**Explanation:**
- `display: grid` creates a grid container
- `grid-template-columns` defines column width
- `grid-template-rows` defines row height
- `gap` sets spacing between grid items

### 2. Grid Terminology

```css
.grid-container {
    display: grid;
    /* 
    fr = fractional unit
    1fr = 1 part of available space
    */
    grid-template-columns: 1fr 2fr 1fr;
    
    /* Grid lines are numbered starting from 1 */
    
    /* 
    Grid track = space between two grid lines
    Grid cell = intersection of row and column
    Grid area = rectangular area surrounded by four grid lines
    */
}
```

### 3. Different Ways to Define Columns and Rows

```css
.grid-container {
    display: grid;
    
    /* Fixed units */
    grid-template-columns: 200px 200px 200px;
    
    /* Mix of units */
    grid-template-columns: 200px 1fr 2fr;
    
    /* Using repeat */
    grid-template-columns: repeat(3, 1fr);
    
    /* Auto-fill and auto-fit */
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    
    /* Named grid lines */
    grid-template-columns: [start] 1fr [middle] 2fr [end];
}
```

### 4. Grid Areas and Template Areas

```html
<div class="page-layout">
    <header class="header">Header</header>
    <nav class="sidebar">Sidebar</nav>
    <main class="main">Main Content</main>
    <footer class="footer">Footer</footer>
</div>
```

```css
.page-layout {
    display: grid;
    grid-template-areas: 
        "header header header"
        "sidebar main main"
        "footer footer footer";
    grid-template-columns: 200px 1fr 1fr;
    grid-template-rows: 80px 1fr 60px;
    min-height: 100vh;
    gap: 20px;
}

.header {
    grid-area: header;
    background: #333;
    color: white;
}

.sidebar {
    grid-area: sidebar;
    background: #f4f4f4;
}

.main {
    grid-area: main;
    background: #fff;
}

.footer {
    grid-area: footer;
    background: #333;
    color: white;
}
```

### 5. Positioning Items

```css
.item {
    /* Using grid lines */
    grid-column: 1 / 3;        /* Start at line 1, end at line 3 */
    grid-row: 1 / 2;          /* Start at line 1, end at line 2 */
    
    /* Shorthand */
    grid-area: 1 / 1 / 2 / 3; /* row-start/column-start/row-end/column-end */
    
    /* Spanning */
    grid-column: span 2;      /* Span 2 columns */
    grid-row: span 2;         /* Span 2 rows */
}
```

### 6. Responsive Grid Layout

```css
.responsive-grid {
    display: grid;
    /* Auto-responsive grid */
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
    padding: 20px;
}

/* Media Queries for specific layouts */
@media (max-width: 768px) {
    .page-layout {
        grid-template-areas: 
            "header"
            "main"
            "sidebar"
            "footer";
        grid-template-columns: 1fr;
        grid-template-rows: auto;
    }
}
```

### 7. Common Grid Patterns

#### Card Layout
```html
<div class="card-grid">
    <div class="card">
        <img src="image.jpg" alt="Card image">
        <h3>Card Title</h3>
        <p>Card content goes here</p>
    </div>
    <!-- More cards -->
</div>
```

```css
.card-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 20px;
    padding: 20px;
}

.card {
    display: grid;
    grid-template-rows: 200px auto auto;
    gap: 10px;
    padding: 15px;
    border: 1px solid #ddd;
    border-radius: 8px;
}

.card img {
    width: 100%;
    height: 200px;
    object-fit: cover;
}
```

### 8. Advanced Grid Features

#### Grid Auto Flow
```css
.grid-container {
    display: grid;
    grid-auto-flow: dense; /* Fills in holes in the grid */
    /* or */
    grid-auto-flow: column; /* Creates new columns instead of rows */
}
```

#### Alignment
```css
.grid-container {
    /* Align grid items */
    justify-items: center;     /* Horizontal alignment */
    align-items: center;       /* Vertical alignment */
    
    /* Align entire grid */
    justify-content: center;   /* Horizontal alignment */
    align-content: center;     /* Vertical alignment */
}

.item {
    /* Individual item alignment */
    justify-self: center;
    align-self: center;
}
```

### 9. Grid vs Flexbox

When to use Grid:
- Two-dimensional layouts (rows AND columns)
- Complex layouts with overlapping
- When you need precise control over placement
- Gallery layouts
- Overall page structure

When to use Flexbox:
- One-dimensional layouts (row OR column)
- Navigation menus
- Centering content
- Flexible spacing
- Content flow

### 10. Best Practices

1. **Start Mobile-First**
```css
.grid {
    display: grid;
    grid-template-columns: 1fr; /* Single column for mobile */
}

@media (min-width: 768px) {
    .grid {
        grid-template-columns: repeat(3, 1fr); /* 3 columns for desktop */
    }
}
```

2. **Use Named Areas for Complex Layouts**
3. **Avoid Fixed Units When Possible**
4. **Consider Fallbacks for Older Browsers**
5. **Use Gap Instead of Margins**
6. **Keep Grid Structure Semantic**